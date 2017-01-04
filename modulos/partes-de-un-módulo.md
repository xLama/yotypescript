## Partes de un módulo {#partes-de-un-m-dulo}

Cuando hacemos referencia al módulo a través de su nombre original, en este caso _M_, estamos accediendo a la parte de las interfaces, la no instanciada. Pero si accedemos a través de una variable del tipo del módulo, estamos accediendo a la parte instanciada que comprende las variables, clases, enumerados y funciones. Realmente un módulo es un objeto de JS. Recordemos que las interfaces en TS no tienen equivalencia en JS, por lo que cuando declaramos una no genera código. Si un módulo sólo tiene interfaces, ese módulo no tiene equivalencia en JS de ninguna forma, por ello no es posible acceder a la parte instanciada, pues ésta sólo se crea cuando realmente se genera código JS.

```ts
namespace M {
    export class A { }
    export interface B { }
    export var a: number = 1;
}

let m: typeof M = M; /* Ahora con m podemos acceder a las entidades que no sean interfaces */

m.a = 2 // Correcto
m.A // Correcto
m.B // Error. Es una interfaz.
let B: M.B; // Correcto.
```



