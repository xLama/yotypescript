## Valores de retorno {#valores-de-retorno}

Las funciones pueden devolver un valor si así lo precisamos. Para ello se debe especificar en la cabecera de la función el tipo de dato que queremos devolver: *number*, *string*, _Array_… Si la función no va a devolver nada, hay que especificarlo con la palabra reservada _void_ y en ese caso devolvería de *undefined* de forma implícita..

```ts
function retun(x: number, y: number) {
    return 4; // Devuelve un número
} 

function noReturrn(x: number, y: number) {
    /* No devuelve nada */
}
```


Para ello se hace con la palabra reservada _return_. Si se especifica un tipo de retorno, es obligatoria, mostrando un error si no se hace. Una vez ha devuelto algún valor, se corta la ejecución de la función por lo que si hay algo posterior no se tendrá en cuenta.

```ts
function withReturn(x: number, y: number) {
    return x * y;
    x = y + 2; /* No se ejecuta pues el flujo de la función ha acabado debido al return*/
}
```