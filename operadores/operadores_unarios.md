## Operadores unarios {#operadores-unarios}

Los operadores unarios son aquéllos que sólo necesitan un operando para poder ser usados.

### Operadores ++ y -- {#operadores-y}

Sólo para _any_, _number_ y _enum_.

Son los llamados incremento \(++\) y decremento \(--\). Sirven para sumar o restar una unidad a un número. A su vez, dependiendo de dónde lo escribamos, pueden ser preincremento/predecremento o postincremento/postdecremento.

```ts
let num = 0;
```

Y le hacemos un postincremento:

```ts
num++; // 1
```

Lo mismo ocurriría si hacemos:

```ts
++num // 1;
```

La diferencia entre el pre y post, es el orden. En pre, primero se ejecuta el operador.

Si hacemos esto:

```ts
let num = 1;
let num2 = --num;
```

¿Cuál será el valor de _num2_? 0. ¿Por qué es 0? Porque primero se ejecuta el operador, es decir, se reduce en 1 la variable _num_ y luego se asigna a _num2_.

Pero si hacemos esto:

```ts
let num = 1;
let num2 = num--;
```

El valor de _num2_ será 1. Pues primero se ha asignado el valor de _num_ a _num2_ y después se la ha restado uno.

Si se usa con _any_ sólo tiene sentido si almacena un número o una cadena que representa un número.

```ts
let example: any = 10;
example ++; // 11

let example: any = "10";
example ++; // 11. Ha convertido la cadena en un número

let example: any = "a";
example ++; // NaN. No puede sumarle 1 a la letra a```

### Operadores +, – {#operadores}

Sólo sirven para *number*,*string*,*any* y *enum*

Convierten un valor del tipo *any* a *number*.

```ts
let num = +"1"; // string “1” a number 1
let num2 = -"1"; // string “1” a number -1
```

El operador - también puede usarse con _number_ para negativizar.

```ts
let num = -1;
```

### Operador ~ {#operador}

Es el complemento a uno. Cambia todos los bits 0 a 1 y todos los bits 1 a 0. En la prática convierte un número en su inverso y le resta 1.

```ts
let x = ~10; // -11 
let y = ~-10; // 9
let z = ~~10; // 10. El complemento del complemento es el número original */
```

### Operador ! {#operador-0}

Sirve para negar una expresión o un tipo de datos _boolean_ o _Boolean_.

Si tenemos esto:

```ts
let truly = true; // true
let falsy = !truly; // false
```

Si negamos _true_, lo convertiremos en _false_. Si negamos _false_ lo convertiremos en _true_.

También puede ser usado para convertir a _boolean_.

```ts
let truly = !"true";
```

Estamos convirtiendo el _string_ “true” a _boolean false_. Si queremos convertirlo a _boolean true_, basta con negar dos veces.

```ts
let falsy = !!"true";
```

### Operador delete {#operador-delete}

Borra propiedades de objetos o elementos de un array.

Si se borra la posición de un array, éste no se redimensiona, sino que convierte esa posición en _undefined_.

Devuelve _true_ o _false_ dependiento de si ha podido eliminar o no el elemento.

```ts
let x = 1;
let obj: Object = { x: 1 };

delete x; // false. Las variables no se pueden borrar 
delete obj["x"] // true
```

### Operador void {#operador-void}

Evalúa una expression cualquiera y siempre devuelve _undefined_.

Suele usarse en el _href_ de los enlaces anchor para realizar alguna acción evitando que se comporte por defecto.

```html
<a href="javascript:void(document.body.style.backgroundColor='green');">Click here for green background</a>
```

### Operador … \(spread\) {#operador-spread}

Expande un _array o un objeto._ Ni más ni menos. De esta forma evitamos el uso de bucles.

Se puede utilizar para añadir los elementos de un _array_ u objeto en otro en el orden que queramos:

```ts
let numbers = [1, 2];
let moreNumbers = [4, 5, 9, ...numbers, 10]; // 4,5,9,1,2,10

let keys = { a: 1, b: 2 };
let moreKeys = { ...keys, c: 3 };
```

Es útil para hacer copias de estructuras. Realmente son copias superficiales pues los objetos que puedan contener esas estructuras no se copian. Para ello habría que hacer una copia profunda.

```ts
let originalArray = [1,2,3];
let copyArray = [...originalArray];

let originalObject = { a: 1, b: 2 };
let copyObject = { ...originalObject };
```

También sirve como parámetro de una función para indicar que admite un número infinito de argumentos, además de usarse como argumento en sí mismo:

```ts
function sum (x: number, ...more: number[]) { } // infinitos números
let numbers: number[] = [4,5,9,10];
sum(1, ...numbers); // pasamos el array expandido
```

Incluso después de usar el _array_, podemos seguir pasando argumentos:

```ts
function sum (a: number, ...more: number ){ }
let numbers = [4,5,9,10];
sum(1,...numbers,20,300);
```

Pero no podemos hacer esto:

```ts
function sum (a: number, b: number) { }
let number = [4,5];
sum(...numbers);
```

Siempre se necesita que uno de los parámetros use también el operador … Con él conseguimos pasar un _array_ como argumento hacia una función que admite infinitos parámetros, y sin usar bucles.

Realmente lo que hace es iterar el iterable \(en este caso un _array_\).

