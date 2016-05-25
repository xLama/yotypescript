## Sentencias útiles para los bucles {#sentencias-tiles-para-los-bucles}

### break {#break}

Corta la ejecución del mismo.

```ts
let nombres = ["Carlos", "José", "Lama"];

for(let indice in nombres) {
  if(nombres[indice] === "José" ){ 
    break;
    // Más código. No se ejecuta.
  } 
}
```

Cuando encuentra el valor “José” en el array _nombres_, ejecuta el _break_ y no sigue iterando.

### continue {#continue}

Ejecuta la siguiente iteración sin haber acabado la actual.

```ts
let nombres = ["Carlos", "José", "Lama"];
for (let index in nombres) { 
  if ( nombres[index] == "José" ){ 
    continue; 
  }
  // Más código… No se ejecuta.
}
```

Si encuentra el valor “José” en el array _nombres_ itera el siguiente sin ejecutar el código que quedaba.

### return {#return}

Termina la ejecución de una función devolviendo un valor. Si no se escpecifica ninguno éste es undefined:

```ts
function retu(x) {
  return; // Acaba la función devolviendo undefined
  let y = 0; // No se ejecuta
}
```