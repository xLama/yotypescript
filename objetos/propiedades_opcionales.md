## Propiedades opcionales {#propiedades-opcionales}

Conjuntamente con las propiedades obligatorias se pueden definir opcionales. Éstas no son más que propiedades que pueden ser implementadas o no. Para ello se debe esribir una interrogación “?” al final del nombre de la propiedad:

```ts
type Person = {name: string , age?: number }
let carlos2: Person = { name: "Carlos" } // Correcto.
```

La propiedad _age_ es opcional y aunque no la hayamos declarado en el objeto literal no muestra ningún error.



