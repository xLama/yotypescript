## Promise.all*. {#promise.all}

Otra utilidad que tiene es la de controlar que todas las operaciones han sido ejecutadas de forma correcta antes de proceder. 

Imagina que estás construyendo una aplicación que debe hacer llamadas a un servidor externo y hasta que todas esas llamadas no hayan acabado correctamente no se puede continuar. La forma de hacerlo con callbacks es engorrosa porque si queremos que todas se disparen al mismo tiempo (y no encadenar una detrás otra cosa que lo convertiría en síncrono aumentando así el tiempo total de la petición) debemos saber cuántas son e ir comprobando si todas la demás han acabado cuando cada una vaya terminando. Este escenario es muy común en las aplicaciones de hoy en día.

Con callbacks:

```ts
function callService() {
    service1(callback, failback); service2(callback, failback); service3(callback, failback);
}

var serviceEnded = 0;

function callback() {
    serviceEnded++;
    if (serviceEnded === 3) { } // Podemos avanzar 
} 

function failback() { } // Error en uno de los servicios. No avanzamos.
```

Con funciones asíncronas:
```ts
async function callService() {
    try {
        var results = Promise.all( [service1(), service2(), service3()] );
        // Hacemos algo con results si ha ido bien
    }
    catch (error) { 
      /* Algo ha ido mal */ 
    }
}
```

Con Promise.all la función espera hasta que completen todas las llamadas pasadas dentro del array. 
Results será un array en el que cada posición (en este caso 3) será el valor devuelvo (si lo hubiera) por cada una de las llamadas. La comodidad salta a la vista, ¿cierto?

Si lo combinamos junto con la deconstrucción, se hace aún más sencillo:

```ts
 let [resultS1, resultS2, resultS3] = Promise.all( [service1(), service2(), service3()] );
 ```
Hemos descompuesto el array de resultados en 3 partes: resultS1, resultS2, resultS3, los cuales son los resultados de las llamadas a los servicios por separados. Si todo ha ido bien, en la siguiente línea se pueden utilizar  estas variables de forma independiente.

La antigua sitaxis await* ha sido desechada en el estándar por lo que actualmente se debe utilizar Promise.all()