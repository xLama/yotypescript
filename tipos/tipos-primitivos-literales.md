### Tipos primitivos literales \(String, Number, Boolean Literal Types\) {#tipos-de-cadenas-literales-string-literal-types}

Son tipos definidos por un _string, number o boolean_ literal. Así de simple. El único valor que puede contener una variable tipada de esta forma es el propio valor

```ts
let name : "Lama" = "Lama";
let bool: true = true;
let num: 5 = 5;
```

Pero se puede usar junto con los tipos unión para darle más utilidad:

```ts
let movement : "up" | "right" | "down" | "left";
```

Así la variable _movement_ sólo puede contener esas cadenas. Esto resulta muy interesante si lo tratamos como un enumerado, es decir, sería un enumerado de cadenas:

```ts
let movements : "up" | "right" | "down" | "left";
let movement : movements = "right";// Ok
let otherMovement : movements = "upDown"; // Error
```

Mucho cuidado con los tipos intersección. No tiene sentido que dos cadenas, números o booleanes distintos se intersequen pues nunca va a existir un valor que satisfaga esa intersección.

```ts
let movements : "up" & "right";
let movement : movements = "right"; // Error
```

Para que la asignación fuera correcta la cadena como valor debe ser a _up_ y _right_ a la vez, cosa que no es posible. Además, son tratados como cadenas \(su tipo aparente es el mismo\), por lo que tienen la misma interfaz, es decir, mismas propiedades y métodos.

