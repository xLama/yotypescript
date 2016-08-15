## instanceOf {#instanceof}

Es un operador binario muy útil para el manejo de clases. Comprueba si un objeto es de un tipo determinado. Sólo funciona con los tipos referencia, es decir, no funciona con los primitivos.

```ts
let x = new Number(5);
x instanceof Number; // true
``` 

No funciona con los tipos primitivos, sólo con los objeto. No podemos hacer esto:

```ts
let y = 5;
y instanceof number; // No compila
``` 


Además, esto dará false:

```ts
let num: Number = 5
num instanceof Number // false
``` 

El resultado de los tipos objeto inicializados de forma literal será _false_. Para que sea _true _deben haber sido inicializados con su constructor como se muestra en el primer ejemplo.

También pueden ser usados para nuestras propias clases.

```ts
class A { }
class B extends A { }
let a = new A();
let b = new B();

a instanceof A // true
a instanceof B // false
b instanceof A // true
``` 

El último ejemplo es _true_ porque al ser B una subclase de A, las instancias de _B_ son a la vez del tipo _A_ y _B_.

No sirve para interfaces. Es algo que sí funciona en otros lenguajes pero en TS no.