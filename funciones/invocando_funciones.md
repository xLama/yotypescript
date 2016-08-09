## Invocando funciones {#invocando-funciones}

La forma de usarlas es sencilla. Para invocarlas basta con escribir su nombre y la lista de argumentos que coincida con sus parámetros, si los hay.

```ts
function add(x: number, y: number) {
    return x + y;
}
```

Para usarla basta con:

```ts
add(5, 5);
```

Si la función devuelve _void_, es decir, vacío, no tiene sentido asignárselo a una variable. Pero si devuelve un tipo distinto a _void_, sí que puede llegar a merecer la pena.

```ts
let sum = add(5, 5); // 10
```

El valor de suma será de 10 que es el valor devuelto por la función.