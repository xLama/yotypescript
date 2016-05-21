## Ámbito de una variable {#mbito-de-una-variable}

El ámbito o alcance es la zona del programa donde esa variable está disponible para ser utilizada.

Si declaramos un variable en una función, será local a esa función y no se podrá usar fuera de la misma. No existe la declaración de variables globales dentro de funciones como sí ocurre en JS.

Si la variable es un miembro de instancia se podrá usar sólo dentro de la instancia si es privada o, si es pública, desde cualquier parte siempre y cuando estemos dentro del ámbito de la instancia que la contiene. Si es un miembro estático está disponible sólo escribiendo el nombre de la clase.

```ts
var name; /* Es accesible desde cualquier parte */
function scope() {
  var surname; /* Sólo es accesible en la función */
  name = "Carlos" /* Podemos acceder a nombre */
}
```

TS da soporte al operador _let_ que permite restringir el ámbito a un bloque de código:

```ts
var name = "Carlos"; /* Es accesible desde cualquier parte */
function scope() { 
  if(name === "Carlos"){ 
  // Podemos acceder a name 
    let surname= "Lama"; // Sólo es accesible en el if 
  } 
  var entireName = name + surname; // Error
}
```