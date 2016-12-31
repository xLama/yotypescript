### keyof

Obtiene las propiedades de cualquier objeto en forma de unión de cadenas literales.

```ts
type obj = { a: 1, b: 2, c: 3 };
let obj2: keyof  obj; // obj2 es del tipo "a" | "b" | "c"
obj2 = "a" // Correcto
obj2 = "Other" // Incorrecto
```

Esto se hace relevante en los tipos mapeados

