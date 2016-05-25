## La importancia de Symbol {#la-importancia-de-symbol}

Existe un **symbol** predefinido que accesible de esta forma:

```ts
Symbol.iterator;
```

Éste sirve para nombrar al método iterador de una clase. Es posible gracias a que un **symbol** puede ser una propiedad de un objeto. Para comprobar si una clase lo posee:

```ts
let nums  = [1, 2, 3];
let iterator  = "iterator";
let x  = 26;
let obj : {} = {name : "Carlos", age: 26}
nums[Symbol.iterator]; // function 
iterator[Symbol.iterator]; // function 
x[Symbol.iterator]; // undefined
obj [Symbol.iterator]; // undefined
```

Sólo el array y el **string** tienen iteradores predefinidos. Tanto el **number** como el object, no. Esto es importante porque ni con el object ni con el **number** podremos usar for-of, ya que éste requiere el método [Symbol.iterator](). Lo realmente potente es que nosotros podemos crear nuestros propios iteradores.