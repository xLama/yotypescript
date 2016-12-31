## Herencia {#herencia}

¿Qué es la herencia? Podemos imaginar que en el mundo existen diferentes tipos de cosas que tienen estados y comportamientos comunes como podrían ser los mamíferos, los automóviles o los teléfonos. La herencia nos provee un mecanismo para relacionar las distintas clases.

Nuestra clase ejemplo _Person_ se refiere a algo muy general. Podríamos especificar más. Si estamos realizando la gestión de un aula, nos damos cuenta de que en ella hay alumnos y profesores y ambos son personas. De esta forma estamos agrupando dos tipos de cosas bajo un mismo comportamiento y estado.

Con todo ello podríamos crear una clase llamada Student y otra llamada Teacher que heredarían de _Person_ por lo que las clases hijas \(así se les llamas a las clases que heredan de otra\) obtendrían todo lo que es y hace el padre \(así se les llama a las clases de las que se hereda\).

Para hacerlo hay que usar la palabra reservada _extends_.

```ts
class Person{}
class Student extends Person { }
class Teacher extends Person { }
```

> No existe la herencia múltiple en TS. Esto es que una clase sólo puede heredar de una sola clase a la vez. No confundir con construir una jerarquía pues una clase puede heredar de varias si entre todas se relacionan de forma vertical.

Alumno -&gt; Persona -&gt; Mamifero -&gt; SerVivo

Ahora tanto _Student_ como _Teacher_ obtendrían todo lo que es y hace _Person_. Bueno, no todo realmente pues aquí entra en juego el principio de ocultación. Todo lo declarado como público se hereda. Todo lo declarado como privado no se hereda y no es accesible desde la clase hija. Hay un tercer modificador, llamado protegido \(_protected_\). Si declaramos un miembro como _protected_, las clases hijas lo heredan pero no es accesible desde fuera.

### Herencia mediante expresiones {#herencia-mediante-expresiones}

Como hemos visto la herencia se consigue gracias a _extends_ seguido del nombre de la clase. Existe otra forma de hacerlo que nos permite que en vez de ser una clase lo que escribamos sea una expresión, como por ejemplo una función:

```ts
function PersonClass() : typeof Person { 
  return Person;
}
class Person{}
class Student extends PersonClass() { }
```

La función devuelve la clase _Person_ que se utiliza como padre. Realmente lo que requiere la expresión es devolver un constructor, ya sea de clase o definido en una interfaz. El siguiente ejemplo es más complejo y no se entendrá bien hasta haber estudiado las interfaces:

La herencia clásica es explícita y estática, es decir, debemos especificar claramente de qué clase se hereda. Con la herencia mediante expresiones podemos darle un poco más de dinamismo ya que, aunque una vez definida la superclase no la podamos cambiar, sí que podemos elegirla según algún criterio antes del proceso de herencia.

Para este ejemplo vamos a recurrir a los coches. Los coches tienen motores que consumen distintos tipos de combustible: gasolina y gasoil. Para ellos nos creamos una interfaz _Fuel_ y dos clases _Gasoil_ y _Gasoline_ que implementan dicha interfaz:

```ts
interface Fuel {
    fuelType(): void;
}

class Gasoil implements Fuel {
    fuelType(): void {
        console.log("Gasoil");
    }
} 

class Gasoline implements Fuel {
    fuelType(): void {
        console.log("Gasoline");
    }
}
```

La marca va a sortear unos coches tanto de gasolina como de gasoil. Como no sabemos el combustible, debemos elegirlo en tiempo de ejecución. Para ello nos hacemos una función que va a servir de selector de la superclase:

```ts
function fuelSelector(): Fuel {
    return Math.random() >= 0.5 ? Gasoil : Gasoline
}
```

Eso muestra un error. El problema es que el tipo devuelto por la función no es el correcto. Realmente lo que debería devolver el tipo de las clases y no la interfaz. Podríamos dejar que la inferencia trabaje por nosotros y, simplemente, eliminar el tipo devuelto. Pero como aquí estamos para aprender vamos a devolver una interfaz. Para ello, lo que realmente espera es un constructor, así que podemos dárselo si hacemos uno para la interfaz:

```ts
interface FuelConstructor {
    new (): Fuel
}
```

Nos hemos creado otra interfaz cuyo único miembro es un constructor que devuelve la interfaz _Fuel._ La interfaz _FuelConstructor_ sí puede ser usada como tipo en la devolución de la función _fuelSelector\(\)_.

```ts
function fuelSelector(): FuelSelector {
    return Math.random() >= 0.5 ? Gasoil : Gasoline
}

class Car extends fuelSelector() { }

let car = new Car();
car.fuelType();
```

La elección del tipo de combustible dependerá de lo ejecutado en la función _fuelSelector\(\)_.

### El operador super {#el-operador-super}

Hemos visto el operador _this_, que hace referencia a la clase propia donde lo usemos.

Existe otro llamado _super_ que hace referencia a la clase padre desde donde estemos heredando. Con él podemos referenciar miembros de la clase padre siempre y cuando no sean privados.

Imaginemos que queremos que, además de nombre y apellidos, un alumno tenga un número de alumno.

```ts
class Student extends Person {
    private studentNumber: number;
    constructor(name: string, surname1: string, studentNumber: number, surname2?: string) {
        super(name, surname1, surname2);
        this.studentNumber = studentNumber
    }
}
```

¿Qué ha pasado aquí?

Hemos creado un constructor para _Alumno_ en el que admite un parámetro más que el de _Person_ para incluirle la referencia.

Hemos llamado al constructor de _Person_ pasándole como argumento lo que espera. Es muy importante recalcar que la primera línea de código del constructor de una clase que hereda de otra es una llamada _super\(\)_ con los argumentos que sean. De lo contrario dará error de compilación. Y esto tiene su lógica. Cuando creamos un _Student_ realmente también estamos creando una _Person_ por lo que para hacerlo se debe llamar al constructor de _Person_.

Después de la llamada _super\(\)_ podemos guardar la referencia.

Si _Person_ tiene el constructor sobrecargado, la llamada _super\(\)_ puede ser a cualquiera de las definiciones del constructor. Simplemente hay que cumplir con los parámetros que exige.

Desde otros métodos podemos llamar a los métodos del padre con el mismo _super_. En este caso no se exige que sea la primera llamada.


En este caso hemos creado un nuevo método para *Student* llamado _mostrarReferencia()_ que muestra la referencia del alumno y después su nombre y apellidos. Pero esto último no lo hace reescribiendo otra vez toda la lógica, sino que se aprovecha de que el padre (*Person*) ya lo tiene implementado.

Hay que señalar que un objeto de una clase hija es también del tipo de todas sus clases padre.

En nuestro ejemplo:

Alumno Persona Mamifero SerVivo

Si instanciamos _Alumno_ obtendríamos un objeto del tipo _Alumno_ pero que a su vez también sería del tipo Persona, _Mamifero_ y _SerVivo_. ¿Recuerdas la llamada _super()_ en el constructor de _Alumno_? Con eso se llama al constructor de _Persona_ por lo que podemos deducir que estamos creando también una instancia de _Persona_ y así sucesivamente. No estamos creando 4 instancias distintas, sólo una pero con las características de todas las superclases.

### Sobreescritura {#sobreescritura}

Heredar los miembros de la clase padre no nos obliga a utilizarlos tal y como son. Podemos redeclarar los atributos y los métodos llámandolos de la misma forma en la clase hija. Eso sí, con ciertas restricciones.

Los miembros deben tener el mismo modificador de visibilidad por lo que si en la superclase está declarado como _public_ o _private_, en la clase hija se debe declarar igual.

```ts
class Person {
    public showName(): void { }
}

class Student extends Person {// Error 
    private showName(): void { }
}
```

Estamos intentando sobreescribir el método _showName\(\)_ haciéndolo privado y eso no es posible en TS. Tampoco es posible hacer lo contrario, es decir, hacer público un método que en el padre es privado. También es aplicable a los atributos.

#### Sobreescritura de métodos {#sobreescritura-de-m-todos}

Sobreescribir no es más que declarar una función en el hijo con el mismo nombre que una que ya existe en el padre. Sólo es posible si el método es público. Si es privado y lo intentamos sobreescribir, fallará.

En nuestra clase Persona tenemos el método _showName\(\)_:

```ts
public showName():void {
    alert(this.name+" " + this.surname1 + " " + this.surname2);
}
```

Podemos crear uno nuevo en _Alumno_ con el mismo nombre. De esta forma lo estamos sobreescribiendo.

Si queremos que el método de _Alumno_ haga lo mismo que el de _Persona_ y, además, algo adicional, se debe llamar al método de _Persona_ mediante:

```ts
super.showName();
```

Y, posteriormente, implementar el código que creamos conveniente.

Es muy útil para ampliar una funcionalidad que proviene de la superclase. Por motivos de diseño podemos necesitar que la clase hija realice más acciones en el mismo método además de las que ya se realizaban en la implementación del método del padre.

