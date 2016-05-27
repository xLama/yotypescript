## typeof {#typeof}

Este operador es muy útil pues nos informa del tipo de dato de una variable. El resultado que nos devuelve es del tipo **string**

```ts
let str = typeof 22; // “number”
```

Hay que tener cuidado con esto:

```ts
let str = typeof new String("probando typeof"); // “object”
```

Si hacemos *typeof str*, el resultado será **object**. ¿Por qué? Pues porque realmente es un _object_ ya que _String_ es una clase de objeto. La única forma de poder saber el tipo de dato específico es inicializando las variables literalmente. No importa si tipas la variable con **string** o **String**, lo importante es lo que le asignes.

Devolverá **string**:

```ts
let str1 = typeof "probando typeof";
let str2 = typeof "probando typeof";
```

Devolverá **object**

```ts
let str = typeof new String("probando typeof");
```

Esto es aplicable no sólo a **String**, sino a todos los demás como **Number**, **Boolean**…

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

Aunque no hayamos especificado el tipo de *x*, el intérprete sabe que es del tipo **number** por lo que podemos hacer que *z* sea de ese tipo.