### El comportamiento {#el-comportamiento}

¿Qué podemos hacer ahora? Darle un comportamiento a través de métodos.

¿Qué puede hacer una persona? Puede hablar, caminar, comer… El comportamiento de una clase suele definirse también como verbos. Evidentemente no todas las acciones tienen sentido en todos los contextos. Si estamos creando la clase _Persona_ para un registro de alumnos de un colegio, no tiene sentido implementar un método que se llame _caminar_. Podría tenerlo si estuviéramos desarrollando un juego.

Para el ejemplo crearemos un método llamado _decirNombre\(\)_ que mostrará en un _alert\(\)_ el nombre de la persona junto con sus apellidos.

```ts
class Persona {

    nombre: string; apellido1: string; apellido2: string; constructor(nombre: string, apellido1: string, apellido2?: string) {
        this.nombre = nombre;
        this.apellido1 = apellido1;
        this.apellido2 = apellido2;
    }

    mostrarNombre(): void {
        alert(this.nombre + " " + this.apellido1 + " " + this.apellido2);
    }
}
```

Puedes observar que muestra la concatenación de los atributos que hemos insertado como argumentos a la hora de instanciar la clase.

Bien, hemos creado unos atributos y un método que define un comportamiento. ¿Cómo accedemos a ellos? Con el operador “.” \(punto\).

Al instanciar la clase:

```ts
let persona: Persona = new Persona("Carlos", "Lama");
```

Podemos acceder a sus miembros con el nombre de la variable seguido de un punto, seguido del miembro al que deseemos acceder. Si es un atributo.

Podemos leer el valor o modificarlo.

```ts
persona.nombre = "Carlos";
```

Si es una función podemos invocarla:

```ts
persona.mostrarNombre();
```

### Operador this {#operador-this}

Como puede ver hay un nuevo operador llamado _this_. _this_ se refiere a la clase en sí misma donde se escribe y es la forma de referenciar a los miembros de la clase. Si se intentara acceder a un miembro de clase sin anteponer _this_, fallaría la compilación.

La forma de utilizarlo es la misma con la que accedemos a los métodos públicos de una clase por medio de una instancia de la misma, con _this._ \(punto\).\_\_

#### Contexto {#contexto}

El _this_ en JS funciona de una forma distinta a como lo hace en la mayoría de los lenguajes orientados a objetos pues se refiere al contexto donde se ha ejecutado. Es un tema que puede traerte de cabeza si no sabes bien cómo funciona.

| Llamada | Valor de _this_ |
| --- | --- |
| **ejecutar\(\);** | Objeto al que pertenece |
| **var objeto = new Objeto\(\);** | La nueva instancia |

El operador _this_ sólo tiene sentido dentro de las funciones pues fuera de éstas su valor siempre es _window_ \(excepto en el modo estricto que sería undefined\). Ya una vez dentro de la función el valor de _this_ será el objeto al que pertenezca esa función en el momento de ser ejecutada. Podemos decir que las funciones son las únicas que crean nuevos contextos.

```ts
let thisExample = { 
  name: "José",
  surname: "Lama", 
  nameAndSurname: this.name +" "+ this.surname
}
thisExample.nameAndSurname // undefined undefined
```

La propiedad _nameAndSurname_ del ejemplo es _undefined undefined_ pues _this_ está referenciando a _window_ y éste no tiene las propiedades _name_ y _surname_.

En el caso de que lo usemos dentro de una función.

```ts
function thisExample(){ 
  this; // window
}
thisExample();
```

De nuevo this es _window_ porque _thisExample\(\)_ no pertenece a ningún objeto de forma explícita, por lo que es parte de _window_.

El operador _new_ cambia este comportamiento y hace que el contexto sea la instancia.

```ts
function thisExample(){ 
  this; // object. La instancia.
}
let example = new thisExample();
```

Teniendo en cuenta la primera fila de la tabla, podemos hacer esto:

```ts
let thisExample = {
    name: "José",
    surname: "Lama",
    nameAndSurname: function () {
        return this.name + " " + this.surname
    }
}
thisExample.nameAndSurname(); // José Lama
```

En esta ocasión, la función sí pertecene a un objeto de forma explícita en el momento de su ejecución por lo que ese _this_ referencia al contexto de la función, que es _thisExample, el objeto._

Algo a muy tener encuenta es lo siguiente.

```ts
let thisExample = function () {
    let name = "José";
    let surname = "Lama";
    let nameAndSurname = function () {
        console.log(this.name + " " + this.surname)
    }

    nameAndSurname();
}
thisExample()// undefined undefined
```

Si echamos un vistazo a la tabla, es de suponer que _this_ _name_ y _this.surname_, que se encuentran dentro de la función _nameAndSurname\(\),_ deberían ser correctos pues el contexto de la función es otra función superior que sí posee esas propiedades, es decir, _nameAndSurname\(\)_ pertecene a un objeto \(que en este caso es una función\). Pero esto realmente no es así. El ejemplo no funciona como parece y en su lugar muestra _undefined undefined._ La conslusión final es que las funciones crean contexto pero no pueden formar parte de él a menos que se use el operador _new._

#### this polimórfico {#this-polim-rfico}

Ahora  _this_ se refiere a la instancia de alguna clase que herede de la clase contenedora.

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

