### Guardas de tipo \(Type Guards\) {#guarda-de-tipos-type-guards}

Visto los los Tipos Unión y como ya veremos en el polimorfismo, es posible que un mismo parámetro pueda contener valores de distinto tipo en momentos diferentes. Eso requiere que cuando tratemos ese dato debamos saber de qué tipo es para crear un comportamiento adecuado:

```ts
function guards(age: number | string) { }
guards("26"); 
guards(26);
```

En el ejemplo no sabemos, a la hora de construir el cuerpo de la función, el tipo del valor, ya que puede ser _number_ o _string_. TS nos proporciona un mecanismo para estos casos que nos ahorra trabajo, con la guarda de tipos. Éstas son de dos formas: con [typeof](typeof.md) e [instanceof](../clases/instanceof.md). En nuestro caso:

```ts
typeof age === "string"; age instanceof String;
```

Ya que estamos trabajando con primitivos, la que nos interesa es el _typeof_, puesto que el otro dará error. La guarda se realiza con sentencias de control de flujo, más concretamente con _if_ y sus derivados. Las variables dentro de las guardas son convertidas al tipo con el que comparamos:

```ts
function halfLife(age: number | string) {
    if (typeof age === "string") {
        return +age / 2; // Aquí age es string 
    } else {
        return age / 2; // Aquí age es number 
    }
} 
halfLife("26"); 
halfLife(26);
```

Ya que la comparación ha sido si _age_ es un _string_, dentro de ese bloque _if_, _age_ es convertido \(las especificaciones del lenguaje lo denomina “estrechamiento”\) a _string_ por lo que podemos tratarlo como tal. En el _else_, y al sólo quedar _number_ como alternativa, es convertido a _number_. Si la condición hubiera sido “no es un string”, los roles se intercambiarían:

```ts
function halfLife(age: number | string) {
    if (typeof age !== "string") {
        return age / 2; // Aquí age es number 
    } else {
        return +age / 2; // Aquí age es string 
    }
}
halfLife("26");
halfLife(26);
```

El operador unario usado en un _string_ convierte la cadena en un _number_.

Se puede complicar más porque es posible que el parámetro sea del Tipo Unión de más de dos:

```ts
function halfLife(age: number | string | { age: number }) {
    if (typeof age === "string") {
        return +age / 2; // Aquí age es string 
    } else {
        return age / 2; 
        /* Aquí age es number | {age: number}. Error. No puede dividir {age: number} entre 2 */
    }

} 
halfLife("26");
halfLife(26);
halfLife({ age: 26 });
```

Esta vez el bloque _else_ utiliza _age_ como si fuera un _number \| {age: number }_ \(Tipo Unión\) y aunque el _number_ lo pueda dividir entre 2, no así el objeto. Para solucionar esto lo mejor es atomizar las guardas siempre y cuando los tipos no sean compatibles, como es el caso:

```ts
function halfLife(age: number | string | { age: number }) {
    if (typeof age === "string") {
        return +age / 2; // Aquí age es string 
    }
    else if (typeof age === "number") {
        return age / 2; // Aquí age es number 
    } else {
        return age.age / 2; // Aquí age es {age:number} 
    }
}
halfLife("26");
halfLife(26);
halfLife({ age: 26 });
```

Es preferible primero hacer la guarda de los primitivos y dejar para el final los tipos objeto.

### Guardas propias {#guardas-propias}

Hemos hecho guardas con operadores propios del lenguaje que son usados para comprobar el tipo. Esto, aunque supone una ventaja importante, también es cierto que no es flexible ya que nos obliga a reescribir el mismo código una y otra vez si necesitamos la misma comprobación en sitios distintos. Hay una forma de crear las nuestras. Para ello hay que definir una función que actuará de guarda en el que el tipo devuelto sea la expresión “x is C” donde _x_ es el parámetro de la función y _C_ es el tipo:

```ts
class Person { }
class Student extends Person {
    studentId: string;
}
class Teacher extends Person {
    teacherId: string;
}
function isStudent(p: Person): p is Student { // Aquí lo importante 
    return p instanceof Student;
}

function isTeacher(p: Person): p is Teacher { // Aquí lo importante 
    return p instanceof Teacher;
}
let person: Person;

if (isStudent(person)) {
    person.studentId; // Aquí person es un Student 
} else if (isTeacher(person)) {
    person.teacherId; // Aquí person es un Teacher
}
```

No se puede tener más de una expresión de guarda por función. Si no entiendes el ejemplo te recomiendo que vuelvas a este apartado una vez hayas visto las [clases](../clases/README.md).

### Guardas basadas en this {#guardas-basadas-en-this}

Simplemente producen estrechamiento al tipo de _this_ si se cumple la condición. Esto es útil en contadas ocasiones porque parte de la premisa que una clase padre conoce a sus clases hijas y eso, desde un punto de vista de diseño de software, no es recomendable. Pero eso no quiere decir que sea algo inútil. Las guardas basadas en _this_ siguen la expresión “this is C”, muy parecida a la anterior “x is C”, pero ahora _x_ es _this_, porque estas guardas se utilizan en métodos.

```ts
class Structure {

    isDirectory(): this is Directory {
        return this instanceof Directory
    }
    isFile(): this is File {
        return this instanceof File
    }
}
class File extends Structure { }

class Directory extends Structure { }

let file: Structure = // Código para leer una estructura

if (file.isFile()) {
    file.studentId; // Aquí file es un Directory 
}
else if (file.isDirectory()) {
    file.teacherId; // Aquí file es un File 
}
```



