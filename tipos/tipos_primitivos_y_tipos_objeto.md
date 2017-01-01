## Tipos primitivos y objeto {#tipos-primitivos-y-tipos-objeto}

Los tipos primitivos son los elementales que nos proporciona un lenguaje de programación y cuyos valores son guardados en la posición de memoria que se le asigna.

A su vez tenemos los tipos objeto que no son más que [clases](../clases/README.md) que se han construido alrededor de estos primitivos para dotarlos de más funcionalidades.

En TS los tipos primitivos y los objetos poseen el mismo nombre pero con la diferencia de que estos últimos se escriben con la primera letra en mayúsculas.

| Primitivo | Objeto | Uso |
| :--- | :--- | :--- |
| **number** | Number | Números: enteros y decimales |
| **string** | String | Caracteres o cadenas |
| **boolean** | Boolean | Sólo admiten _true_ o _false_ |
| **undefined** | Undefined | Sin valor |
| **null** | Null | Valor nulo |
| **void** | Void | Ausencia de valor |
| **never** | - | Valores que no pueden ocurrir |
| **symbol** | Symbol | Valores únicos usados como token. |

Si declaramos una variable con un tipo primitivo, no la podemos inicializar con el tipo objeto aunque sí se puede hacer lo inverso.

```ts
let variable1: Boolean = new Boolean(true); // Correcto
let variable2: boolean = variable1; // Incorrecto boolean/Boolean

let variable3: boolean = true; // Correcto
let variable4: Boolean = variable3; // Correcto
```

### Inicialización literal {#inicializaci-n-literal}

Consiste es asignarle el valor directamente a una variable sin usar ningún [constructor](../clases/constructores.md). Tanto los primitivos como los objetos pueden ser inicializados de forma literal.

```ts
let str: string = "Esto es una cadena";
let str2: String = "Esto es una cadena";
let num: number = 2;
let num2: Number = 2;
let bool: boolean = true;
let bool2: Boolean = true;
```

El por qué de esto se ve mejor con un ejemplo

TS:

```ts
let str: string = "Esto es una cadena";
let str2: String = "Esto es una cadena";
```

JS:

```js
var str = "Esto es una cadena";
var str2 = "Esto es una cadena";
```

Lo que en TS son dos variables de tipos distintos, una primitiva y otra objeto, en JS son dos variables sin tipo. El hecho de que no podamos inicializar una variable primitiva usando el constructor de su equivalente objeto es una comprobación del compilador de TS realizada para mantener la consistencia pero que en JS no ocurre.

TS:

```ts
let str: string = new String("Cadena"); // Error
```

JS:

```js
let cadena = new String("Esto es una cadena"); // Correcto
```

Al tipar la variable con _string_, en TS ya estamos indicando que debe contener un tipo primitivo o literal y no va a permitir algo distinto. Como en JS no tipamos la variable, podemos inicializarla con el primitivo o el objeto.

Un apunte a tener en cuenta es que las cadenas de caracteres se pueden inicializar tanto con dobles comillas como con las simples:

```ts
let str: string = "Esto es una cadena";
let str2: string = 'Esto es una cadena';
let str3: String = "Esto es una cadena";
let str4: String = 'Esto es una cadena';
```

### Template Strings \(cadenas plantilla\) {#template-strings-cadenas-plantilla}

Como hemos visto en el apartado anterior, una cadena de caracteres se inicializa de forma literal con “ \(comillas dobles\) o ‘ \(comillas simples\). Existe una tercera forma de inicialización con el acento grave \`.

```ts
`esto es una cadena`
```

Esto permite escribir texto en distintas líneas sin usar el operador de concatenación +:

```ts
`esto es una cadena
en varias
líneas`
```

Pero su potencial reside en la inclusión de expresiones de una forma sencilla:

```ts
let a: = 2;
let b: = 2;
console.log(`La suma de a y b es ${a + b}`)
```

${a + b} no se muestra de forma literal, sino que es una expresión que se evalúa y devuelve el resultado. En este caso es 4.

Podemos ir un paso más allá y controlarlo con una función:

```ts
let a = 50;
let b = 10;
function sum(strings : string[], ...values : number[]){ 
  return values.reduce( (prev,actual ) => previo + actual )
}
let total = sum `La suma de a y b es ${a + b} y la multiplicación es ${a * b}`
let total; // Resultado: 560
```

La definición de la función requiere un argumento del tipo _string\[\]_ y otros del tipo del resultado de las expresiones, en este caso _number_. De esa forma, al ejecutarse la función _sum_ con la plantilla, la parte correspondiente a cadenas de caracteres sería conseguible desde el primer parámetro. El segundo sirve para conseguir los resultados de las expresiones entre llaves. El cuerpo de la función, aunque no sea necesario saber qué hace ahora, suma todos los números contenidos en el array y devuelve el resultado.

De una forma más gráfica:

```ts
let a = 50;
let b = 10;
function sum (strings : string[], ...valores : number[]){
  strings[0]// "La suma de a y b es" 
  strings[1]// "y la multiplicación es" 
  valores[0] // a + b = 60 
  valores[1] // a * b = 500
}
sum `La suma de a y b es ${a + b} y la multiplicación es ${a * b}`
```

No es obligatorio que el segundo parámetro sea del tipo “resto de parámetros” pero sí conveniente para reutilizar la función sin importar el número de expresiones de la plantilla. En el ejemplo anterior esto sería totalmente funcional:

```ts
let a = 50;
let b = 10;
function suma(strings : string[], x: number, y : number){ 
  strings[0]// "La suma de a y b es" 
  strings[1]// "y la multiplicación es" 
  x; // a + b = 60
  y; // a * b = 500
}
suma `La suma de a y b es ${a + b} y la multiplicación es ${a * b}
```

### ¿Primitivo u objeto? ¿Cuál usar? {#primitivo-u-objeto-cu-l-usar}

Vayamos por partes:

Con respecto a _number/Number_, con el primero se pueden usar los [operadores aritméticos](../operadores/operadores_binarios.md#operadores-aritm-ticos) y con el segundo no. Es algo exclusivo de TS ya que en JS es perfectamente válido por lo que estamos ante otra comprobación en tiempo de compilación. Esto supone un gran inconveniente.

```ts
let x: Number = new Number(1);
let y: Number = new Number(1);
let z: Number = x + y; // Error
```

Para los tipos _boolean/Boolean_ y _string/String_ la elección es más complicada. No existen diferencias más allá de las incompatibilidades de inicialización. Pero teniendo en cuenta que es preferible usar _number_ a _Number_, son recomendables _boolean_ y _string_ para conseguir coherencia en el código.

Además los primitivos también nos permiten usar los métodos útiles que incorporan los tipos objeto por lo que no perdemos funcionalidad. Esto es así porque JS hace una [conversión de tipos](../clases/confirmaciones_de_tipo__type_assertions.md).

A su vez también hace lo inverso, convertir los objetos a primitivos. Eso es necesario para poder usar los operadores aritméticos. Pero aunque JS lo permita, TS lo comprueba en tiempo de compilación y lo muestra como un error. Si queremos obtener el valor primitivo de un objeto debemos usar el método _valueOf\(\)_:

```ts
let obj:String = new String("cadena objeto");
let primitive = obj.valueOf();
```

Si queremos hacer cálculos con _Number_ lo más fácil, en realidad, es convertirlos:

```ts
let obj:Number = new Number(2);
let obj2: Number = new Number(2);
let sum:number = +objeto + +objeto2;
```



