## typeof {#typeof}

Este operador es muy útil pues nos informa del tipo de dato de una variable. El resultado que nos devuelve es del tipo _string_

```ts
let str = typeof 22; // "number"
```

Hay que tener cuidado con esto:

```ts
let str = typeof new String("probando typeof"); // "object"
```

Si hacemos _typeof str_, el resultado será _object_. ¿Por qué? Pues porque realmente es un _object_ ya que _String_ es un tipo objeto. La única forma de poder saber el tipo de dato específico es inicializando las variables literalmente. No importa si tipas la variable con _string_ o _String_, lo importante es lo que le asignes.

Devolverá _string_:

```ts
let str1 = typeof "probando typeof";
let str2 = typeof "probando typeof";
```

Devolverá _object_

```ts
let str = typeof new String("probando typeof");
```

Esto es aplicable no sólo a _String_, sino a todos los demás como _Number_, _Boolean_.

Con este operador también podemos tipar una variable con el tipo de otra. Es lo que se conoce en TS como tipos consulta.

```ts
let x: number = 5;
let z: typeof x = 2;
```

Incluso lo podemos hacer por inferencia.

```ts
let x = 5;
let z: typeof x = 2;
```

Aunque no hayamos especificado el tipo de _x_, el compilador sabe que es del tipo _number_ por lo que podemos hacer que _z_ sea de ese tipo.

