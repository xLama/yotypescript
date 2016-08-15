## Funciones que devuelven funciones {#funciones-que-devuelven-funciones}

¿Puede una función devolver otra función con una definición determinada? Sí.

```ts
function devolverFuncion(): (x: string) => number { 
    return fun => 1;
}
```

En este caso tenemos una función llamada _devolverFuncion_ sin parámetros. El tipo devuelto por la función es otra función que tiene como parámetro una variable del tipo **string** y su tipo de retorno es un **number**.

En el _return_ devolvemos una función flecha literalmente. _Fun_ queda tipada por inferencia.