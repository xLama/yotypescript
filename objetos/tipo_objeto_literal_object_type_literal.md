## Tipo objeto literal (Object type literal) {#tipo-objeto-literal-object-type-literal}

Es posible definir un tipo objeto literal de manera que podamos especificar qué propiedades debe tener un objeto y de qué tipo son éstas:

```ts
let objeto: {a: string , n: number } = { a: "cadena", n : 1 }
```

Lo más común es usarlo junto con los tipos alias:

```ts
type obj = {a: string , n: number }
let g : obj = { a: "cadena", n : 1 }
```

Existen tres restricciones a la hora de asginar objetos literales a variables de tipo objeto literal: número, nombre y tipo de propiedades del objeto:

```ts
type obj = {a: string , n: number }
let a : obj = { cad: "cadena", n : 1 } // Correcto
let b : obj = { cad: "cadena", n : 1, x: 1} // Incorrecto. Tiene más propiedades.
let c : obj = { cad: "cadena" } // Incorrecto. Tiene menos propiedades.
let d : obj = { cad: "cadena", x : 1 } // Incorrecto. Tiene el mismo número de propiedades pero no se llaman igual.
```

Para poder saltarnos la restricción de número de propiedades, podemos hacer una confirmación de tipo. Todos los ejemplos siguientes son correctos:

```ts
type obj = {a: string , n: number }
let a : obj = { cad: "cadena", n : 1 }
let b : obj = <obj> { cad: "cadena", n : 1,x: 1} 
let c : obj = <obj> { cad: "cadena" }
```