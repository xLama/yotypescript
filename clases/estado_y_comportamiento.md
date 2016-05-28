## Estado y comportamiento {#estado-y-comportamiento}

Una clase tiene atributos (se representan con variables) que definen su estado, y métodos (funciones) que definen su comportamiento. Son los llamados miembros de clase.

### El estado {#el-estado}

Los atributos de una clase son variables que se declaran dentro de la propia clase.

Seguimos construyendo la clase _Persona_. Tenemos que pensar qué características tiene una persona cualquiera, qué es lo que nos define. En este caso hemos optado por su nombre y apellidos. También podría ser el DNI, altura, peso, todo lo que queramos o necesitemos.

**class** Persona {**** nombre: **string**; apellido1: **string**; apellido2: **string**; **constructor**(nombre: **string**, apellido1: **string**, apellido2?: **string**) {}****}

Hemos declarado sus atributos pero no están inicializados. Lo hacemos en el constructor.

**class** Persona {

nombre: **string**; apellido1: **string**; apellido2: **string**; **constructor**(nombre: **string**, apellido1: **string**, apellido2?: **string**) { **this**.nombre = nombre; **this**.apellido1 = apellido1; **this**.apellido2 = apellido2;}****}

Como podemos ver lo que se introduce como argumento al constructor es lo que en su implementación se le asigna a los atributos. Normalmente cuando instanciemos una clase debemos inicializar su atributos pues es lo que va a definir a ese objeto en particular y lo va a diferenciar del resto de objetos de la misma clase.

Hay que puntualizar que las clases no aceptan atributos opcionales.

**class** Persona {**** nombre?:**string**; apellido1: **string**; apellido2: **string** /* (…) */}

#### Otra forma de declarar atributos {#otra-forma-de-declarar-atributos}

Los parámetros de entrada de un constructor pueden ser miembros de la clase (atributos) de forma automática sin declararlos de forma explícita.

**class** Persona { **constructor**(**private** nombre: **string**, **private** apellido1: **string**, **private** apellido2?: **string**) {}

**public** mostrarNombre(): **void** { **** alert(**this**.nombre + " " + **this**.apellido1 + " " + **this**.apellido2);}****}

La diferencia ha sido la de escribir la palabra reservada _private_ (con _public_ y _protected_ también funciona) en la propia definición del método constructor. De esta forma estamos declarando de forma automática esos atributos como miembros de la clase. Y, a la hora de introducirlos como argumentos del constructor, ya se estarían inicializando.

El constructor siempre es público. Es el único caso en que se debe omitir. En algunos lenguajes de programación existen los constructores privados pero en TS no están soportados.

### El comportamiento {#el-comportamiento}

¿Qué podemos hacer ahora? Darle un comportamiento a través de métodos.

¿Qué puede hacer una persona? Puede hablar, caminar, comer… El comportamiento de una clase suele definirse también como verbos. Evidentemente no todas las acciones tienen sentido en todos los contextos. Si estamos creando la clase _Persona_ para un registro de alumnos de un colegio, no tiene sentido implementar un método que se llame _caminar_. Podría tenerlo si estuviéramos desarrollando un juego.

Para el ejemplo crearemos un método llamado _decirNombre()_ que mostrará en un _alert()_ el nombre de la persona junto con sus apellidos.

**class** Persona {

nombre: **string**; apellido1: **string**; apellido2: **string**; **constructor**(nombre: **string**, apellido1: **string**, apellido2?: **string**) { **this**.nombre = nombre; **this**.apellido1 = apellido1; **this**.apellido2 = apellido2;}

mostrarNombre(): **void** { alert(**this**.nombre + " " + **this**.apellido1 + " " + **this**.apellido2); }****}

Puedes observar que muestra la concatenación de los atributos que hemos insertado como argumentos a la hora de instanciar la clase.

Bien, hemos creado unos atributos y un método que define un comportamiento. ¿Cómo accedemos a ellos? Con el operador “.” (punto).

Al instanciar la clase:

**var** persona: Persona = **new** Persona("Carlos", "Lama");

Podemos acceder a sus miembros con el nombre de la variable seguido de un punto, seguido del miembro al que deseemos acceder. Si es un atributo.

Podemos leer el valor o modificarlo.

persona.nombre = "Carlos";

Si es una función podemos invocarla:

persona.mostrarNombre();

### Operador this {#operador-this}

Como puede ver hay un nuevo operador llamado _this_. _this_ se refiere a la clase en sí misma donde se escribe y es la forma de referenciar a los miembros de la clase. Si se intentara acceder a un miembro de clase sin anteponer _this_, fallaría la compilación.

La forma de utilizarlo es la misma con la que accedemos a los métodos públicos de una clase por medio de una instancia de la misma, con _this._ (punto).__

#### Contexto {#contexto}

El _this_ en JS funciona de una forma distinta a como lo hace en la mayoría de los lenguajes orientados a objetos pues se refiere al contexto donde se ha ejecutado. Es un tema que puede traerte de cabeza si no sabes bien cómo funciona.

| Llamada | Valor de _this_ |
| --- | --- |
| **ejecutar();** | Objeto al que pertenece |
| **var objeto = new Objeto();** | La nueva instancia |

El operador _this_ sólo tiene sentido dentro de las funciones pues fuera de éstas su valor siempre es _window_ (excepto en el modo estricto que sería undefined). Ya una vez dentro de la función el valor de _this_ será el objeto al que pertenezca esa función en el momento de ser ejecutada. Podemos decir que las funciones son las únicas que crean nuevos contextos.

```ts
let thisExample = { 
  name: "José",
  surname: "Lama", 
  nameAndSurname: this.name +" "+ this.surname
}
thisExample.nameAndSurname // undefined undefined
```

La propiedad *nameAndSurname* del ejemplo es *undefined undefined* pues _this_ está referenciando a _window_ y éste no tiene las propiedades _name_ y _surname_.

En el caso de que lo usemos dentro de una función.

```ts
function thisExample(){ 
  this; // window
}
thisExample();
```

De nuevo this es _window_ porque _thisExample()_ no pertenece a ningún objeto de forma explícita, por lo que es parte de _window_.

El operador _new_ cambia este comportamiento y hace que el contexto sea la instancia.

**function** thisExample(){ **this;** // object. La instancia.}**var** example = **new** thisExample();

Teniendo en cuenta la primera fila de la tabla, podemos hacer esto:

**var** thisExample = { **** name: "José", surname: "Lama", nameAndSurname: **function**(){**return this**. name +" "+ **this**. surname }****}****thisExample.nameAndSurname(); // José Lama

En esta ocasión, la función sí pertecene a un objeto de forma explícita en el momento de su ejecución por lo que ese _this_ referencia al contexto de la función, que es _thisExample, el objeto._

Algo a muy tener encuenta es lo siguiente.

**var** thisExample = **function**(){ **var** name = "José"; **var** surname = "Lama"; **var** nameAndSurname = **function**(){ console.log**(this**.name +" "+ **this**.surname) }

nameAndSurname();****}****thisExample()// undefined undefined

Si echamos un vistazo a la tabla, es de suponer que _this_ _name_ y _this.surname_, que se encuentran dentro de la función _nameAndSurname(),_ deberían ser correctos pues el contexto de la función es otra función superior que sí posee esas propiedades, es decir, _nameAndSurname()_ pertecene a un objeto (que en este caso es una función). Pero esto realmente no es así. El ejemplo no funciona como parece y en su lugar muestra _undefined undefined._ La conslusión final es que las funciones crean contexto pero no pueden formar parte de él a menos que se use el operador _new._

#### this polimórfico {#this-polim-rfico}

Hay que diferenciar entre el **this** usado en una expresión y el usado como un tipo. Esta característica sólo está disponible en métodos no estáticos.

Si se usa como expresión, es decir, se utiliza el operador **this** en una sentencia cualquiera, como por ejemplo en un **return**, hace referencia a la instancia original:

```ts
class HTMLElement { 
//...
  public setId( id: string ){ 
    this.id = id;
    return this; 
  } 
//...
}
class Div extends HTMLElement { //…
  public setWidth( width: number ){ 
    this.width = width;
    return this; 
  } 
//...
}
let div = new Div().setId("div").setWidth(5);
```

Al invocar el método _setId,_ el cual es de _HTMLElement_, lo devolvería, con lo cual, al intentar invocar _setWidth,_ y no ser éste parte de esa clase, fallaría. Precisamente ese es el comportamiento que ha cambiado. Ahora sabe que lo que devuelve _setId_ no es _HTMLElement,_ sino cualquier clase que herede de ella y que esté invocando el método en ese instante.

El otro uso del **this** polimórfico es como tipo. De esa forma se refiere al tipo de la clase concreta donde se esté usando:

**class** HTMLElement { **public** clone(): this {

//… }}**class** Div **extends** HTMLElement {}**var** div = **new** Div().clone();

La clase _Div_ hereda el método _clone_ y lo que debe devolver es una instancia de _Div,_ no de _HTMLElement_.