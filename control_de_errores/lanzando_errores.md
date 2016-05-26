## Lanzando errores {#lanzando-errores}

En el bloque _catch_ se puede ejecutar el código que se desee, como por ejemplo escribir en la consola para obtener información sobre él. Aunque también se puede lanzar el error con el operador _throw_.

Lanzar un error consiste en elevarlo hacia arriba confiando en que exista un _try-catch_ que lo tratará de forma adecuada.

```ts
function erroExample(): void {
    var example = null;
    try {
        example.age = 10;
    } catch (e) {
        throw e; // TypeError 
    }
}

try {
    errorExample();
}
catch (e) {
    console.error(e) /* Mostramos el error */
}
```

La variable *example* no tiene el atributo *age* por lo que se lanza un error que capturamos con *catch*. En el ejemplo hemos decidido seguir lanzando hacia arriba el error para que sea otra entidad la que lo controle. Para esto no es necesario escribir el bloque _try-catch_ dentro de la función, basta con encerrar la invocación a la misma.

```ts
function errorExample(): void {
    let example = null;
    example.age = 10;
}

try {
    errorExample();
} catch (e) {
    console.error(e) /* Mostramos el error */
}
```

Lo errores que no capture nuestro código, lo serán por el navegador. En las versiones más modernas lo hacen de una forma excelente mostrando en la consola el tipo de error y dónde.

Cuando se lanza un error, el flujo de ejecución se para en ese punto para seguir en el bloque que ha lo ha capturado. Si teníamos más código que ejecutar, no lo hará.