## Nombres de variables {#nombres-de-variables}

Sólo puede estar formado por letras, números y los símbolos $ (dólar) y _ (guión bajo). Además el primer carácter no puede ser un número. Realmente, al ser UNICODE, acepta mucho más caracteres pero no lo recomiendo porque no se garantiza su compatibilidad en todos los navegadores y pueden no tener mucho sentido. Lanzo una pregunta. ¿Necesitas que una variable se llame  ლ_ಠ益ಠ_ლ? Sí, es válido.

Ejemplos correctos de variables:

```ts
let variable1;
let variable2;
let numeroDeElementos;
let ლ_ಠ益ಠ_ლ = 65;
```

Ejemplos erróneos:

```ts
let var; /* Palabra reservada */
var 1cosa; /* El primer carácter es un número */
```

Se pueden declarar varias en la misma línea separadas por coma.

```ts
let variable1, variable2, variable3;
```