## Recursión {#recursi-n}

¿Qué pasa si llamamos a la función generadora dentro de la propia función? ¿Sería una llamada recursiva? La respuesta es que no pasa nada.

```ts
function* generator() {
  yield "José";
  generator();
  yield "Carlos";
}
let gen = generator();
gen.next(); // {value: José, done: false}
gen.next(); // {value: Carlos, done: true}
```

En este mismo sentido. ¿Qué pasaría si invocamos otra función generadora distinta? ¿Se comportaría como esperamos? No, no lo haría. Es como si no tuviera ningún yield.

```ts
function* joseGenerator() { 
  yield "José";
}

function* carlosGenerator() {
  yield "Carlos";
}

function* joseCarlosGenerator() { 
  joseGenerator(); 
  carlosGenerator();
}

let gen = joseCarlosGenerator();
gen.next(); // {value: undefined, done: true}
```

Para hacer funcionar el ejemplo se debe invocar a las funciones generadoras con *:

```ts
function* joseGenerator() { 
  yield "José";
}

function* carlosGenerator() {
  yield "Carlos";
}

function* joseCarlosGenerator() {
  yield* joseGenerator();
  yield* carlosGenerator();
}
let gen = joseCarlosGenerator();
gen.next(); // {value: José, done: false}
gen.next(); // {value: Carlos, done: true}
```

Si no usáramos el *, lo que estaríamos haciendo sería devolver la propia función generadora invocada.

No sólo se usa para otras funciones generadoras, sino que también se puede utilizar para cualquier iterable:

```ts
function* joseCarlosGenerator() { 
  yield* ["José", "Carlos"]; 
  yield* "Lama";
}
let gen = generator();
gen.next(); // {value: José, done: false}
gen.next(); // {value: Carlos, done: false}
gen.next(); // {value: Lama, done: true}
```