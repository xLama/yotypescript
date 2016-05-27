## El mejor tipo común {#el-mejor-tipo-com-n}

Hay situaciones en las no hemos tipado un array y lo hemos rellenado de valores de distinto tipo:

```ts
let x = ["uno", null, "dos"];
```

El compilador, para tipar por inferencia, elige la mejor opción. En este caso hay dos elecciones posibles: **string** y _Null_. Como _Null_ es compatible con cualquier tipo, elige tipar el _array_ con **string**. En consecuencia _x_ sería un **string**[] (array de strings).

### Any como tipo general {#any-como-tipo-general}

Si introducimos una variable **any** en el _array_, el mejor tipo común será **any**[]

```ts
let x;
let array = [x, "Carlos", true]; // Resultado any[]
```

### **{}**

Si introducimos un objeto {} en el array o un _Object_ _(_**new** _Object() ),_ el mejor tipo común será {} siempre y cuando no haya ninguna variable **any**. En ese caso será **any**.

```ts
var x: any;var array = ["Carlos", {}] // {}[]
var array2 = [x, "Carlos", {}] // any[]
var array3 = [x, "Carlos", new Object()] // any[]
```

### Entre primitivos {#entre-primitivos}

Debido a la existencia de los tipos unión, el mejor tipo va a ser el tipo unión si en el array introducimos dos o más de estos tipos: **string**_,_ **number**_,_ **boolean** o _Array_

```ts
var array = ["Carlos", 24] //  (string | number)[]
```

### Entre primitivos y objetos {#entre-primitivos-y-objetos}

Si introducimos un tipo primitivo y otro objeto relacionados (**number**_/Number_) el mejor tipo común será el del objeto.

```ts
var array = [3, new Number(1)] // Number[]
```

### Entre tipos referencia {#entre-tipos-referencia}

Si rellenamos el array con instancias de clases o interfaces el mejor tipo común será aquél que sea compatible con todos los demás. En el caso de que no exista, el resultado será {}. Aunque las clases instanciadas sean subclases de otra común, el algoritmo debe elegir entre los tipos explícitamente introducidos.

```ts
class A { }
class B { }
var array = [new A(), new B()] // A[]
```

Si existe más de un mejor tipo común posible, elige el primero que encuentra. En este caso _A_.

```ts
class A { }
class B extends A { }
class C extends A { }
var array = [new B(), new C()]; // B[]
```

Aunque _B_ y _C_ sean subclases de _A_, al no estar _A_ explícitamente en el array, no puede escogerla como mejor tipo común.