## Propiedades de sólo lectura {#propiedades-opcionales}

Las propiedades de sólo lectura son, como su nombre indican, aquéllas que sólo se pueden inicializar en el momento de la declaración del objeto y no después.

```ts
type readonlyObject = { a: number, readonly b: number };
let obj: readonlyObject = { a: 3, b: 5 }; / Aquí sí podemos asignarle un valor a b
obj.b = 7; // Error. a es de sólo lectura.
```



