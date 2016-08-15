## Crear elementos {#crear-elementos}

Se pueden crear elementos dinámicamente y añadirlos a la vista.

```ts
let capa = document.createElement("div");
```

Al ser una función especializada tipa por inferencia la variable capa con _HTMLDivElement_.

Una vez hecho, sólo debemos añadirlo como hijo a algún elemento que actuará como padre con _appendChild()_

```ts
let capa = document.createElement("div");
let body = document.getElementsByTagName("body")[0]; 
body.appendChild(capa);
```