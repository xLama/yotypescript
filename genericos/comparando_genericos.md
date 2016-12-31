## Comparando genéricos {#comparando-gen-ricos}

La comparación de genéricos se hace de la misma forma que las funciones, clases e interfaces. Lo que hay que tener en cuenta es que se hace una vez se han sustituidos los parámetros genéricos. Si dos clases son estructuralmente análogas una vez hecho, son compatibles.

Este ejemplo es correcto.

```ts
interface Generico<T> { }
let x: Generico<string>;
let y: Generico<number>;
x = y; //  Correcto
```

Y lo es porque la T de la interfaz genérica no se utiliza por lo que si comparamos las interfaces después de resolver el genérico, nos damos cuenta de que son equivalentes estructuralmente, pues están vacías.

Sin embargo, si hacemos esto:

```ts
interface Generico<T> { algo: T; }
let x: Generico<string>;
let y: Generico<number>;
x = y; // Incorrecto
```

No sería correcto pues la x tendría su miembro _algo_ del tipo _string y la y tendría su miembro algo_ del tipo _number_. _Number_ y _string_ no son compatibles.

Los genéricos no son nada por sí solos, sino que siempre son una clase, interfaz o función. Las comparaciones se realizan una vez se resuelven los parámetros genéricos siguiendo las mismas reglas de comparación vistas en el libro.

