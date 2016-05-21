## Tipos primitivos y tipos objeto {#tipos-primitivos-y-tipos-objeto}

Los tipos primitivos son los elementales que nos proporciona un lenguaje de programación y cuyos valores son guardados en la posición de memoria que se le asigna.

A su vez tenemos los tipos objeto que no son más que [clases](../clases/README.md) que se han construido alrededor de estos primitivos para dotarlos de más funcionalidades.

En TS los tipos primitivos y los objetos poseen el mismo nombre pero con la diferencia de que estos últimos se escriben con la primera letra en mayúsculas.

| Primitivo | Objeto | Uso |
| --- | --- | --- |
| **number** | Number | Números: enteros y decimales |
| **string** | String | Caracteres o cadenas |
| **boolean** | Boolean | Sólo admiten _true_ o _false_ |
| **undefined** | Undefined | Sólo puede usarse como valor |
| **null** | Null | Sólo puede usarse como valor |
| **void** | Void | Ausencia de valor |
| **symbol** | Symbol | Valores únicos usados como token. |

Si declaramos una variable con un tipo primitivo, no la podemos inicializar con el tipo objeto aunque sí se puede hacer lo inverso.

```**var** variable1: Boolean = **new** Boolean(**true**); // Correcto**var** variable2: **boolean** = variable1;// Incorrecto boolean/Boolean

**var** variable3: **boolean** = **true**; // Correcto**var** variable4: Boolean = variable3; // Correcto```

### Inicialización literal {#inicializaci-n-literal}

Consiste es asignarle el valor directamente a una variable sin usar ningún [constructor](../clases/constructores.md). Tanto los primitivos como los objetos pueden ser inicializados de forma literal.

```**var** cadena: **string** = "Esto es una cadena";**var** cadena3: String = "Esto es una cadena";**var** numero: **number** = 2;**var** numero2: Number = 2;**var** boolean: **boolean** = **true**;**var** boolean2: Boolean = **true**;```

El por qué de esto se ve mejor con un ejemplo

TS:

```**var** cadena: **string** = "Esto es una cadena";**var** cadena2: String = "Esto es una cadena";```

JS:

```**var** cadena = "Esto es una cadena";**var** cadena2 = "Esto es una cadena";```

Lo que en TS son dos variables de tipos distintos, una primitiva y otra objeto, en JS son dos variables sin tipo. El hecho de que no podamos inicializar una variable primitiva usando el constructor de su equivalente objeto es una comprobación del compilador de TS realizada para mantener la consistencia pero que en JS no ocurre.

TS:

```**var** cadena: **string** = **new** String("Cadena"); // Error```

JS:

```**var** cadena = **new** String("Esto es una cadena"); // Correcto```

Al tipar la variable con **string**_,_ en TS ya estamos indicando que debe contener un tipo primitivo o literal y no va a permitir algo distinto. Como en JS no tipamos la variable, podemos inicializarla con el primitivo o el objeto.

Un apunte a tener en cuenta es que las cadenas de caracteres (**string**) se pueden inicializar tanto con dobles comillas como con las simples:

```**var** cadena: **string** = "Esto es una cadena";**var** cadena2: **string** = 'Esto es una cadena';**var** cadena3: String = "Esto es una cadena";**var** cadena4: String = 'Esto es una cadena';```

### Template Strings (cadenas plantilla) {#template-strings-cadenas-plantilla}

Como hemos visto en el apartado anterior, una cadena de caracteres se inicializa de forma literal con “ (comillas dobles) o ‘ (comillas simple). Existe una tercera forma de inicialización con el acento grave `.

`esto es una cadena`

Esto permite escribir texto en distintas líneas sin usar el operador de concatenación +:

`esto es una cadenaen variaslíneas`

Pero su potencial reside en la inclusión de expresiones de una forma sencilla:

**var** a: **number** = 2;**var** b: **number** = 2;console.log(`La suma de 2+2 es ${a + b}`)

${a + b} no se muestra de forma literal, sino que es una expresión que se evalúa y se devuelve el resultado. En este caso es 4\.

Podemos ir un paso más allá y controlarlo con una función:

Pero su potencial reside en la inclusión de expresiones de una forma sencilla:

**var** a: **number** = 50;**var** b: **number** = 10;**function** suma (strings : **string**[], ...valores : **number**[]):**number{ return** valores.reduce( (previo,actual, indice, array) => previo + actual **)}**suma `La suma de a y b es ${a + b} y la multiplicación es ${a * b}`****// Resultado: 560

La definición de la función requiere un argumento del tipo **string**[] y otros del tipo del resultado de las expresiones, en este caso **number** De esa forma, al ejecutarse la función _suma_ con la plantilla, la parte correspondiente a cadenas de caracteres sería conseguible desde el primer parámetro. El segundo sirve para conseguir los resultados de las expresiones entre llaves. El cuerpo de la función, aunque no sea necesario saber qué hace ahora, suma todos los números contenidos en el _array_ y devuelve el resultado.

De una forma más gráfica:

**var** a: **number** = 50;**var** b: **number** = 10;**function** suma (strings : **string**[], ...valores : **number**[]):**void{** strings[0]// “La suma de a y b es” strings[1]// “y la multiplicación es” **valores[0]** // a + b = 60 **valores[1]** // a * b = 500**}**suma `La suma de a y b es ${a + b} y la multiplicación es ${a * b}`

No es obligatorio que el segundo parámetro sea del tipo “resto de parámetros” pero sí conveniente para reutilizar la función sin importar el número de expresiones de la plantilla. En el ejemplo anterior esto sería totalmente funcional:

**var** a: **number** = 50;**var** b: **number** = 10;**function** suma (strings : **string**[], x: **number**, y : **number**):**void{** strings[0]// “La suma de a y b es” strings[1]// “y la multiplicación es” **x** // a + b = 60 **y** // a * b = 500**}**suma `La suma de a y b es ${a + b} y la multiplicación es ${a * b}`

### ¿Primitivo u objeto? ¿Cuál usar? {#primitivo-u-objeto-cu-l-usar}

Vayamos por partes:

Con respecto a **number** _/Number,_ con el primero se pueden usar los [operadores aritméticos](../operadores/operadores_binarios.md#operadores-aritm-ticos) y con el segundo no. Es algo exclusivo de TS ya que en JS es perfectamente válido por lo que estamos ante otra comprobación en tiempo de compilación. Esto supone un gran inconveniente.

**var** x: Number = **new** Number(1);**var** y: Number = **new** Number(1);**var** z: Number = x + y; // Error

Para los tipos **boolean**_/Boolean_ y **string** _/String_ la elección es más complicada. No existen diferencias más allá de las incompatibilidades de inicialización. Pero teniendo en cuenta que es preferible usar **number** a _Number_, son recomendables **boolean** y **string** para conseguir coherencia en el código.

Además los objetos también nos permiten usar los métodos útiles que incorporan los tipos objeto por lo que no perdemos funcionalidad. Esto es así porque JS hace una [conversión de tipos](../clases/confirmaciones_de_tipo__type_assertions.md).

A su vez también hace lo inverso, convertir los objetos a primitivos. Eso es necesario para poder usar los operadores aritméticos. Pero aunque JS lo permita, TS lo comprueba en tiempo de compilación y lo muestra como un error. Si queremos obtener el valor primitivo de un objeto debemos usar el método _valueOf():_

**var** objeto:String = **new** String("cadena objeto");**var** primitivo = objeto.valueOf();

Ese método devuelve el tipo _Object_ de TS

**var** objeto:String = **new** String("cadena objeto");**var** primitivo:Object = objeto.valueOf(); // Correcto**var** primitivo2:**string** = objeto.valueOf(); // Error

Si queremos hacer cálculos con _Number_ lo más fácil, en realidad, es convertirlos:

**var** objeto:Number = **new** Number(2);**var** objeto2: Number = **new** Number(2);**var** suma:**number** = +objeto + +objeto2;