## Funciones que devuelven funciones {#funciones-que-devuelven-funciones}

¿Puede una función devolver otra función con una definición determinada? Sí.

```ts
function returnFunction(): (x: string) => number { 
    return fun => 1;
}
```

En este caso tenemos una función llamada returnFunction sin parámetros. El tipo devuelto por la función es otra función que tiene como parámetro una variable del tipo _string_ y su tipo de retorno es un _number_.

En el _return_ devolvemos una función flecha literalmente. _Fun_ queda tipada por inferencia.

