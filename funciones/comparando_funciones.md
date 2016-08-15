## Comparando funciones {#comparando-funciones}

Las funciones se comparan de la misma forma que se sobrecargan. Simplemente deben coincidir en número de parámetros, tipo de los mismos y devolver el mismo tipo de dato. Los tipos no han de ser exactos, basta con que sean compatibles.

```ts
let func1: (x: number, y: number) => number = (x: number, y: number) => x * y;
let func2: (x: number) => number = (x: number) => x;
func1 = func2 // Correcto
func2 = func1 // Incorrecto
```

La primera asignación es correcta porque se le está asignando a la función con más parámetros una que tiene menos y coinciden en el tipo.

La segunda asignación es incorrecta porque ocurre lo contrario. A la función con menos parámetros se le está asignando una con más y no puede “absorberlos”

Esto resulta muy útil a la hora de construir funciones que acepten otras funciones por parámetro.

```ts
let numbers = [4,5,9,10];
```

Usamos el método

[numeros.filter()](../anexo_i_arrays/metodos.md#filter) que exige como argumento una función con 3 parámetros: los dos primeros son números y el último del tipo _Array_.

¿Es obligatorio pasarle una función con esa definición? Realmente no. Como argumento acepta una función con un máximo de 3 parámetros, por lo que si sólo nos interesa construir una función con un sólo parámetro podemos hacerlo.

```ts
numbers.filter((item) => console.log(item));
```