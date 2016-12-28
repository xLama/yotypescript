## Propiedades computadas \(Computed properties\) {#propiedades-computadas-computed-properties}

Existe otra posibilidad a la hora de nombrar las propiedades de un objeto de forma que éstas sean el resultado de una expresión. A eso se le llama propiedades computadas/calculadas \(_computed properties\)_. Para ello se debe encerrar la expresión entre corchetes \[\]:

```ts
let obj = { ["property"+"name"] : 1};
```

Es posible hacerlo de forma compleja:

```ts
let name = "carlos";
let obj = { [name.toUpperCase()] : "carlos"};
```

También es posible hacerlo en clases e interfaces:

```ts
class Person{ 
  ["name"] : string;
}

interface Person{ 
  ["age"] : number;
}
```

### Propiedades Symbol {#propiedades-symbol}

Los [**symbol**](../tipos/otros_tipos.md#symbols) pueden ser usados como propiedades de objetos:

```ts
let sym : symbol = Symbol("sym");
let obj: {} = { [sym] : "symbol"};
```

¿Qué nos aporta? Las propiedades que sean _symbol_ no son accesibles de forma habitual, esto es a través de _JSON.stringify_, usando el método _Object.getOwnPropertyNames_ o iterándolo con un for. Es “invisible” por lo que podría usarse para identificar a un objeto \(o grupo de ellos\) de forma unívoca a la vez que su valor no es manipulable de una forma sencilla:

```ts
let metadata : symbol = Symbol("medatada");
let obj: {} = { [medatada] : { date: Date.now() }};
JSON.stringify(obj); // {}
Object.getOwnPropertyNames(obj) // []
for (let value in obj){ 
  console.log(value) // No muestra metadata
}
```

La forma de obtener las propiedades que sean _symbol_ es la siguiente:

```ts
Object.getOwnPropertySymbols(obj); // [Symbol(medatada)]
```

Por supuesto podemos obtener su valor con el _symbol:_

```ts
obj[metadata]; // {date: /*...*/}
```



