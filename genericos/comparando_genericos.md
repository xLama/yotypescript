## Comparando genéricos {#comparando-gen-ricos}

La comparación de genéricos se hace de la misma forma que las funciones, clases e interfaces. Lo que hay que tener en cuenta es que se hace una vez se han sustituidos los parámetros genéricos. Si dos clases son estructuralmente análogas una vez hecho, son compatibles.

Este ejemplo es correcto.

**interface** Generico < T > {}**var** x: Generico<**string**>;**var** y: Generico<**number**>;x = y; // Correcto

Y lo es porque la T de la interfaz genérica no se utiliza por lo que si comparamos las interfaces después de resolver el genérico, nos damos cuenta de que son equivalentes.

Sin embargo, si hacemos esto:

**interface** Generico < T > {**** algo:T;}**var** x: Generico<**string**>;**var** y: Generico<**number**>;x = y; // Incorrecto

No sería correcto pues la x tendría su miembro _algo_ del tipo **string** y la _y_ tendría su miembro _algo_ del tipo **number**. _Number_ y **string** no son compatibles.

Los genéricos no son nada por sí solos, sino que siempre son una clase, interfaz o función. Las comparaciones se realizan una vez se resuelven los parámetros genéricos siguiendo las mismas reglas de comparación vistas en el libro.