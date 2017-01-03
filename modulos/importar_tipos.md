## Importar tipos {#importar-tipos}

Podemos importar módulos y sus entidades a otros módulos con la palabra reservada _import_ para un manejo más fácil de los mismos.

```ts
namespace A{ 
    export class Person { }
}

namespace B { 
    import Person = A.Person; 
    let carlos: Person; 
    let jose: A.Person;
}
```

Tenemos dos módulos independientes, cada uno con sus entidades.

En el módulo _A_ tenemos una clase llamada _Person_. En el módulo _B_ tenemos un _import_ llamado _Person_ que en realidad es un alias a la clase _Person_ del módulo _A._ Al establecerle el mismo nombre en el _import_, manejamos la clase como si estuviera dentro del módulo _B_, ahorrándonos tener que escribir toda su ruta hasta llegar a ella. La variable _jose_ es del mismo tipo que _carlos_.

Hay una regla a la hora de exportar miembros si activamos la generación del archivo de definiciones \(d.ts\): si un miembro exportado hace uso de alguna clase, interfaz o enum en su mismo nivel, también deben ser exportadas o fallará.

```ts
namespace A {
    interface B { }
    export function example(b: B): void { }
}
```

La compilación falla porque la función _example_ que está exportada usa la interfaz _B_ que no lo está. Es obligatorio exportar _B_ también.

