## Operadores unarios {#operadores-unarios}

Los operadores unarios son aquéllos que sólo necesitan un operando para poder ser usados.

### Operadores ++ y -- {#operadores-y}

Sólo para **any**_,_ **number** _y_ **enum**.

Son los llamados incremento (++) y decremento (--). Sirven para sumar o restar una unidad a un número. A su vez, dependiendo de dónde lo escribamos, pueden ser preincremento/predecremento o postincremento/postdecremento.

**var** num: **number** = 0;

Y le hacemos un postincremento:

num++ // 1

Lo mismo ocurriría si hacemos:

++num // 1

La diferencia entre el pre y post, es el orden. En pre, primero se ejecuta el operador.

Si hacemos esto:

**var** num: **number** = 1;**var** num2: **number** = --num;

¿Cuál será el valor de _num2_? 0\. ¿Por qué es 0? Porque primero se ejecuta el operador, es decir, se reduce en 1 la variable _num_ y luego se asigna a _num2_.

Pero si hacemos esto:

**var** num: **number** = 1;**var** num2: **number** = num--;

El valor de _num2_ será 1\. Pues primero se ha asignado el valor de _num_ a _num2_ y después se la ha restado uno.

Si se usa con **any** sólo tiene sentido si almacena un número o una cadena que representa un número.

**var** example: **any** = 10;example ++; // 11

**var** example: **any** = "10";example ++; // 11\. Ha convertido la cadena en un número

**var** example: **any** = "a";example ++; // NaN. No puede sumarle 1 a la letra a

### Operadores +, – {#operadores}

Sólo sirven para **number**_,_ **string,****any** y **enum**_._

Convierten un valor del tipo **any** a **number**.

**var** num: **number** = +"1"; // string “1” a number 1**var** num2: **number** = -"1"; // string “1” a number -1

El operador - también puede usarse con **number** para negativizar.

**var** num: **number** = -1;

### Operador ~ {#operador}

Es el complemento a uno. Cambia todos los bits 0 a 1 y todos los bits 1 a 0\. En la prática convierte un número en su inverso y le resta 1.

**var** x: **number** = ~10; // -11 **var** y: **number** = ~-10; // 9**var** z: **number** = ~~10; /* 10\. El complemento del complemento es el número original */

### Operador ! {#operador-0}

Sirve para negar una expresión o un tipo de datos **boolean** o _Boolean_.

Si tenemos esto:

**var** truly: **boolean** = **true**; // true**var** falsy: **boolean** = !truly; // false

Si negamos **true**, lo convertiremos en **false**. Si negamos **false** lo convertiremos en **true**.

También puede ser usado para convertir a **boolean**.

**var** truly: **boolean** = !"true";

Estamos convirtiendo el **string** “true” a **boolean****false**. Si queremos convertirlo a **boolean****true**, basta con negar dos veces.

**var** falsy: **boolean** = !!"true";

### Operador delete {#operador-delete}

Borra propiedades de objetos o elementos de un array.

Si se borra la posición de un array, éste no se redimensiona, sino que convierte esa posición en _undefined_.

Devuelve **true** o **false** dependiento de si ha podido eliminar o no el elemento.

**var** x: **number** = 1;**var** obj: Object = { x: 1 };

**delete** x; /* false. Las variables no se pueden borrar */**delete** obj["x"] // true

### Operador void {#operador-void}

Evalúa una expression cualquiera y siempre devuelve _undefined_.

Suele usarse en el _href_ de los enlaces anchor para realizar alguna acción evitando que se comporte por defecto.

&lt;a href="javascript:void(document.body.style.backgroundColor='green');"&gt;Click here for green background&lt;/a&gt;

### Operador … (spread) {#operador-spread}

Expande un _array._ Ni más ni menos. De esta forma evitamos el uso de bucles.

Se puede utilizar para añadir los elementos de un _array_ en otro en el orden que queramos:

**var** numbers: **number**[] = [1,2];**var** moreNumbers: **number**[] = [4,5,9, ...numeros,10]; // 4,5,9,1,2,10

También sirve como parámetro de una función para indicar que admite un número infinito de argumentos, además de usarse como argumento en sí mismo:

**function** sum (x: **number**, ...more: **number**[]): **void** { } // infinitos números**var** numbers: **number**[] = [4,5,9,10];sum(1, ...numbers); // pasamos el array expandido

Incluso después de usar el _array_, podemos seguir pasando argumentos:

**function** sum (a: **number**...more: **number** ): **void** { }**var** numbers: **number**[] = [4,5,9,10];sum(1,...numbers,20,300);

Pero no podemos hacer esto:

**function** sum (a: **number**, b: **number**): **void** { }**var** number: **number**[] = [4,5];sum(...numbers);

Siempre se necesita que uno de los parámetros use también el operador … Con él conseguimos pasar un _array_ como argumento hacia una función que admite infinitos parámetros, y sin usar bucles.

Realmente lo que hace es iterar el iterable (en este caso un _array_).