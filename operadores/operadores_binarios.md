## Operadores binarios {#operadores-binarios}

Los operadores binarios son aquéllos que necesitan dos operandos para poder ser usados.

### Operador de asignación {#operador-de-asignaci-n}

Es el _=_ \(igual\). Ya vimos que se usaba para inicializar las variables. La regla que sigue es que todo lo que hay a la derecha del = se asigna a lo que hay a la izquierda y no al revés.

No podemos hacer esto:

```ts
1 = let num: number;
```

### Operadores lógicos {#operadores-l-gicos}

Se usan para evaluar expresiones dando como resultado true o false. Son muy útiles para las [estructuras de control de flujo](#757309351116418-_Estructuras_del_control).

Son operadores llamados perezosos porque no siguen evaluando en cuanto el resultado de una expresión o conjunto de ellas es suficiente para determinar toda la condición.

#### false en TS {#false-en-ts}

0, "" \(cadena vacía\), _null_ y _undefined_

#### Operador AND {#operador-and}

Se representa: &&

Será true si, y sólo si, todas las expresiones son true.

| expresión1 | expresión2 | expresión1 && expresión2 |
| --- | --- | --- |
| true | true | true |
| true | false | false |
| false | false | false |
| false | false | false |

Si alguno de los dos se evalúa como false, el resultado será false. Una expresión puede ser una variable o una expresión compleja. Se pueden hacer todo lo extensas que se desee

… && … && ... && … &&

Incluso se puede establecer prioridades con paréntesis:

expresion1 && \(expresión2 && expresion3\)

expresion2 y expresion3 actúan como una a la hora de evaluarse de forma conjunta con expresion1

También puede usarse para una asignación condicional. Si el primer operando se evalúa como true, se asignará el valor del segundo operando. Si se evalúa como false, se asignará el valor del primero. La variable siempre quedará tipada con el tipo de dato del segundo operando.

```ts
let and = false && "str"; // false
```

Es muy útil cuando lo usamos con instancias que no sabemos si son _null/undefined_ o no.

```ts
let person: Person = null;
let name = person && person.name; // undefined
```

Como _persona_ no es una instancia de _Persona_, no tiene acceso a sus atributos, por lo que _persona.nombre_ fallará. De esta forma nos aseguramos que esto no ocurre porque si persona es _null_ \( y _null_ se evalúa como false\), se asignará a nombre el valor del primer operando sin evaluar el segundo. Si _persona_ no fuera _null_ evaluaría _persona.nombre_ y se lo asignaría a _nombre_.

#### Operador OR {#operador-or}

Se representa \|\|

Será true si alguno de los operandos es true.

| expresión1 | expresión2 | expresión1 OR expresión2 |
| --- | --- | --- |
| true | true | tue |
| true | false | true |
| false | false | true |
| false | false | false |

Al igual que con AND, se pueden hacer todo lo largas que se quiera.

También puede usarse para una asignación condicional.

```ts
let or = false || 4; // 4
let or = 10; || "or"; // 10
```

Si el primer operando se evalúa como true, se asignará a la variable. Si se evalúa como false, se asignará el segundo operando sea cual sea su valor. La variable quedará tipada como el [tipo unión](../tipos/otros_tipos.md#tipos-uni-n-union-types) entre ambos operadores.

Es muy útil para inicializar variables que no sabes si ya lo están.

```ts
let name: string;
name = name || "Carlos";
```

Evalúa _name_. Al ser _null_, y _null_ ser false, asigna el valor del segundo operando a la variable. Si _name_ ya estuviera inicializado, lo evaluaría como true y le asignaría el valor del primer operando a la variable.

### Operadores aritméticos {#operadores-aritm-ticos}

Estos operadores son exclusivos para number, any y enum

. No se pueden usar con Number. El resultado siempre será un número.

#### Operadores + y - {#operadores-y}

Son los usados para sumar y restar números respectivamente.

```ts
let x = 2;
let y = 2;
let sum = x + y; // 4
let res = x - y; // 0
```

#### Operadores \* y / {#operadores-y-0}

Son los usados para multiplicar y dividir números respectivamente.

```ts
let x = 2;
let y = 2;
let multiplicacion = x * y; // 4
let division = x / y; // 1
```

#### Operador % {#operador}

Obtiene el resto de una división.

```ts
let x = 5;
let y = 2;
let resto = x % y; // 1
```

#### Operador {#operador-0}

Obtiene la potencia siendo el primer operando la base y el segundo el exponente.

```ts
let x = 5;
let y = 2;
x  y // 5 ^ 2= 25
```

Es una especificación de ES7 por lo que los anteriores se transpilan usando el método _pow_ de la librería matemática _Math,_ por lo que el resultado de transpilarlo a JS sería el siguiente:

```ts
let x = 5;
let y = 2;
Math.pow(x, y); // 5 ^ 2= 25
```

Todos los operadores anteriores tienen la forma corta de este tipo:

```ts
let x = 1;
x *= 3; // Equivalente a x = x * 3;
```

### Operadores de bits {#operadores-de-bits}

#### Operadores lógicos bit a bit {#operadores-l-gicos-bit-a-bit}

| operador | uso |
| :--- | :--- |
| & | Realiza la operación AND bit a bit. |
| "pipe" | Realiza la operación OR bit a bit. |
| ^ | Realiza la operación XOR bit a bit |

Esto operadores realizan la operación bit a bit. Eso signfica que convierten el número a binario y van comparando uno a uno los bits de la misma posición. Dependiendo del operador usado, el resultado será 0 ó 1, lo que conformará un nuevo número.

```ts
let x: number = 15; // x: 01111 
var y: number = 20; // y: 10100
var z: number = x & y; // z: 00100 Es el número 4
var x: number = 15; // x: 01111
var y: number = 20; // y: 10100
var z: number = x | y; // z: 11111 Es el número 31

let x: number = 15; // x: 01111
var y: number = 20; // y: 10100
var z: number = x ^ y; // z: 11011 Es el número 27
```

#### Operadores &lt;&lt; y &gt;&gt; {#operadores-y-1}

Son los usados para desplazamiento de bits. Si desplazamos un bit a la izquierda el resultado es la multiplicación por 2 del número. Si desplazamos un bit a la derecha, el resultado es la división entre 2 del número. Se pueden hacer los desplazamientos que queramos y se van concatenando.

```ts
let x: number = 10;x << 3 // 80\. 10*2*2*2x >> 1 // 5\. 10/2
```

### Operadores relacionales {#operadores-relacionales}

Comparan datos. Es obligatorio que los dos operandos sean del mismo tipo. Si uno de los dos es any el otro puede ser de cualquiera tipo. El resultado siempre será un boolean: true o false.

#### Operadores &lt;, &gt;, &lt;=, &gt;=, {#operadores}

Se usan para comprobar si un dato es mayor, menor o igual que otro.

```ts
let x: number = 5;
let y: number = 2;
x > y; // true
x < y; // false
x >= y; // true
x <= y; // false
```

Se puede usar también con string. Todos los caracteres tienen un código numérico que los identifica. La comparación se haría en base a él.

```ts
"a" > "A"; // true
"b" > "A"; // true
```

Como puedes ver, “b” es mayor a “A” porque el código ASCII de la letra b minúscula es mayor que el código ASCII de la letra A mayúscula. Las letras mayúsculas tienen un código menor a las minúsculas.

Más información sobre ASCII: [http://es.wikipedia.org/wiki/ASCII](http://es.wikipedia.org/wiki/ASCII)

#### Operadores == y != {#operadores-y-2}

Se usan para comprobar si un dato es igual o distinto a otro, respectivamente. El resultado siempre será un _boolean_. Estos operadores sólo comprueban el valor y no el tipo del dato pues hace una conversión de tipos si puede.

```ts
let x: number = 5;
let y: number = 5;
x == y; // true
x != y; // false
null == undefined; // true
```

Se pueden comparar primitivos y objeto indistintamente.

```ts
let x: Number = new Number(5);
let y: number = 4;
let a:string = "A";
let b:String = new String("B");
x == y; // fals
ea != b; // true
```

#### Operadores === y !== {#operadores-y-3}

Se usan para comprobar si un dato es igual o distinto a otro respectivamente. El resultado siempre será un boolean. Estos operadores sí comprueban el tipo de datos además del valor. No hace conversión de tipos.

```ts
let x: Number = new Number(5);
let y: number = 5;
let a:string = "A";
let b:String = new String("B");
x === y; // false
a === b; // false
```

Esta vez no sólo comprueba el valor, sino también el tipo sin hacer conversion. Como number y _Number_ no son el mismo tipo ni tampoco string y _String_, el resultado de las comprobaciones del ejemplo son false.

¿Cómo se evaluaría una comprobación de igualdad entre dos _String_ \(objeto\) cuyas cadenas fueran iguales?

```ts
let a = new String("cadena");
let b = new String("cadena");
a === b; // false
a == b; // false
```

La evaluación es falseporque está comparando objetos, que son objetos referencia. Y esta comparación se hace en base a la [dirección de memoria](../tipos/destructuring_deconstruccion.md). Si las direcciones son iguales, los objetos también lo son. En el ejemplo hemos instanciado dos veces la clase _String_ por lo que tenemos dos objetos con direcciones distintas.

Para que la igualdad se pueda evaluar como true_:_

```ts
let a = new String("cadena");
let b:String = a;
a === b; // true
a == b; // true
```

En este caso a la variable _b_ se le está asignando _a,_ es decir, _b_ contiene la misma dirección que _a_ por lo que los dos apuntan al mismo espacio de memoria y son, en realidad, el mismo objeto.

Es aplicable a cualquier [tipo referencia](../tipos/tipos_nombrados_y_referencia.md), ya sea estándar del lenguaje o creado por nosotros.

Esto implica que dos variables de tipos objeto relacionados pueden ser distintos a ojos del operador pero iguales en valor. Una de las opciones para poder hacer la comparación es usar el método _toString\(\)_.

```ts
let a = new String("cadena");
let b = new String("cadena");
a.toString() === b.toString() // true
```

### Operador + de concatenación {#operador-de-concatenaci-n}

Requiere que al menos uno de los operandos sea any o string.

Si los dos operandos son number, el resultado será number_._ En este caso estaría actuando como operador suma.

Si al menos uno de ellos es string el resultado será string porque los concatena, es decir, los une. En este caso estaría actuando como operador de concatenación.

```ts
let cadena1 = "Hola, ";
let cadena2 = "Mundo";
cadena1 + cadena2; // "Hola, Mundo"
let cadena1 = "Somos";
let numero = 2;
cadena1 + numero; // "Somos 2"
```

Podemos convertir un tipo number, any o enum a string concatenándole la cadena vacía.

```ts
let x: any = 10;
x+""; // "10"
```

### Operador in {#operador-in}

Busca el valor del operando de la izquierda, que debe ser any, string o number, en el operando de la derecha, que debe ser any, _object_ o _array_ devolviendo true si lo encuentra y false en caso contrario.

No busca valor de los atributos, sino el nombre de los mismos.

```ts
let animales = ["Perro", "Gato", "Conejo"];
"Perro" in animales; /* False. Perro es un valor del íncide 0 del array */
1 in animales; /* true. El array contiene 3 valores con lo cual existe el índice 1 */
let obj = {animal:"Perro"}
"Perro" in obj; /* False. Perro es un valor del íncide “animal” */"animal" in obj; // True. Animal es un índice
```

### Operador condicional terciario {#operador-condicional-terciario}

Sirve para asignar a una variable un valor dependiendo de una cierta condición. Es un un caso específico de [if](../control_del_flujo/selectivas.md#if) que resulta muy práctico.

```ts
let x:number = 10;
let z:number = x == 10 ? 1 : 100; // 1
```

La variable _x_ vale 10. A la variable _z_ se le asigna un valor dependiendo de una condición que en este caso comprueba si la variable _x_ vale 10. Si es cierto, a _z_ se le asigna 1, en caso contrario se le asigna 100;

Para hacer un simil con \|\|, recordemos:

```ts
let name: string;
name = name || "Carlos";
```

Podríamos, también, expresarlo de la siguiente forma:

```ts
name = name ? name: "José Carlos";
```

A _name_ se le asigna un valor dependiendo de la condición dada. En este caso comprueba si _nombre_ es true o false \(nombre es _null_ que como ya sabemos se evalúa como false\). Si fuera true, a nombre se le asignaría el valor que ya tiene. Como es false se le asigna “Carlos”.

