## Un mismo módulo en distintos archivos {#un-mismo-m-dulo-en-distintos-archivos}

Una característica importante de los módulos es la posibilidad de declarar el mismo en archivos distintos.

module1.ts

```ts
namespace A{ 
  export class Persona { }
}```

module2.ts

```ts
namespace A {
    export class Student extends Person { }
}```

Tenemos dos archivos distintos: module1.ts y module2.ts. En ambos se declara del módulo _A_. En module1 tenemos una clase de nombre *Person* y en module2.ts tenemos una clase de nombre *Student* que hereda de *Person*. Al estar en el mismo módulo, no hay problemas. Pero al estar en archivos separados module2.ts no sabe dónde buscar la clase *Person*. Para ello hay que hacer referencia a ese archivo de forma explícita

module.ts

```ts
///<reference path="module2.ts">
module A { 
  export class Student implements Person { }
}
```

Se ha hecho referencia al archivo module2.ts a través de su ruta relativa. De esta forma ya tiene acceso a *Person*.

Es posible que el editor que estemos usando, como ocurre en el caso de VSCode, esta búsqueda se haga de forma automática y no haga falta referenciarlos explícitamente.