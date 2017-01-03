## Un mismo módulo en distintos archivos {#un-mismo-m-dulo-en-distintos-archivos}

Una característica importante de los módulos es la posibilidad de declarar el mismo en archivos distintos.

module1.ts

```ts
namespace A{ 
  export class Person { }
}
```

module2.ts

```ts
namespace A {
    export class Student extends Person { }
}
```

Tenemos dos archivos distintos: module1.ts y module2.ts. En ambos se declara el módulo _A_. En module1 tenemos una clase de nombre _Person_ y en module2.ts tenemos una clase de nombre _Student_ que hereda de _Person_. Al estar en el mismo módulo, no hay problemas. Pero al estar en archivos separados module2.ts no sabe dónde buscar la clase _Person_. Para ello hay que hacer referencia a ese archivo de forma explícita

module.ts

```ts
///<reference path="module2.ts">
module A { 
  export class Student extends Person { }
}
```

Se ha hecho referencia al archivo module2.ts a través de su ruta relativa. De esta forma ya tiene acceso a _Person_.

Es posible que el editor que estemos usando, como ocurre en el caso de VSCode, esta búsqueda se haga de forma automática y no haga falta referenciarlos explícitamente aunque si generamos todo el código Javascript en in archivo, es aconsejable hacerlo porque de esta forma le decimos al compilador cómo es la dependencia. Si no es capaz de hacerlo por sí mismo y no se lo decimos nosotros, puede ocurrir que declare Student antes de Person  lo cual daría error en tiempo de ejecución.

