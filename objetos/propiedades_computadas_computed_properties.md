## Propiedades computadas {#propiedades-computadas-computed-properties}

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



