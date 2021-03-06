## Constantes {#constantes}

En contraposición a las variables existen las constantes, que como su nombre indica, no se les pueden modificar su valor una vez inicializadas.

Para crearlas se usa la palabra reservada _const_

```ts
const pi = 3.14; 
pi = 3 // Error
```

Además su ámbito se comporta como una variable declarada con _let_ \(ámbito de bloque\).

```ts
function getPI() { 
  if(true){
    const PI = 3.14; 
  } 
  return PI; // Error. PI no alcanzable.
}
```

Lo que evita es la asignación de la variable al completo, no una de sus partes. Con un objeto y un array se ve mejor:

```ts
const options = { frecuency: 10, all: null };
options.frecuency = 20;  // Ok
options = { frecuency: 20, all: true } // Error
```

Además las constantes [se pueden simular en algunas circunstancias](../clases/estaticos.md#757309351116418-_Constantes_mediante_estáticos).

