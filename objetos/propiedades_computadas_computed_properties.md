## Propiedades computadas (Computed properties) {#propiedades-computadas-computed-properties}

Existe otra posibilidad a la hora de nombrar las propiedades de un objeto de forma que éstas sean el resultado de una expresión. A eso se le llama _computed properties_ (propiedades computadas/calculadas). Para ello se debe encerrar la expresión entre corchetes []:

**var** obj: {} = { ["nombre"+"de"+"propiedad"] : 1};

Es posible hacerlo de forma compleja:

**var** name ="carlos";**var** obj: {} = { [name.toUpperCase()] : "carlos"};

También es posible hacerlo en clases e interfaces:

**class** Person{ ["name"] : **string**;}

**interface** Person{ ["age"] : **number**;}

### Propiedades Symbol {#propiedades-symbol}

Los [**symbol**](../tipos/otros_tipos.md#symbols)pueden ser usados como propiedades de objetos:

**var** sym : **symbol** =Symbol("sym");**var** obj: {} = { [sym] : "symbol"};

¿Qué nos aporta? Las propiedades que sean **symbol** no son accesibles de forma habitual, esto es a través de JSON.stringify, usando el método Object.getOwnPropertyNames o iterándolo con un for. Es “invisible” por lo que podría usarse para identificar a un objeto (o grupo de ellos) de forma unívoca a la vez que su valor no es manipulable de una forma sencilla:

**var** metadata : **symbol** =Symbol("medatada");**var** obj: {} = { [medatada] : { date: Date.now() }};JSON.stringify(obj); // {}Object.getOwnPropertyNames(obj) // []**for** (**let** value **in** obj){ console.log(value) // No muestra metadata}

La forma de obtener las propiedades que sean **symbol** es la siguiente:

Object.getOwnPropertySymbols(obj); // [Symbol(medatada)]

Por supuesto podemos obtener su valor con el **symbol:**

obj[metadata]; // {date: /*...*/}