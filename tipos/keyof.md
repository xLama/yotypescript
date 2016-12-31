### keyof

Obtiene las propiedades de cualquier objeto en forma de [unión de cadenas literales.](/tipos/tipos-unión.md)

```ts
type obj = { a: 1, b: 2, c: 3 };
let obj2: keyof  obj; // obj2 es del tipo "a" | "b" | "c"
obj2 = "a" // Correcto
obj2 = "Other" // Incorrecto
```

Esto se hace relevante en los [tipos mapeados](/tipos/tipos-mapeados.md)

Se puede utilizar junto con typeof para obtener las propiedades de del tipo de una variable

```ts
let obj : {a :number, b:number, c:string};
let obj2 : keyof typeof obj; // "a" | "b" | "c"
```



