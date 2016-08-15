## Const enums {#const-enums}

Los enumerados constantes difieren del resto en que sus elementos no pueden ser accedidos con íncide numérico:

```ts
const enum Animal { Dog, Cat, Rabbit }
Animal[0]; // Error
```

Además no generan código alguno en JS por lo que su comprobación se delega en el compilador de TS. La principal causa era un comportamiento “extraño” en los enumerados:

```ts
const enum Animal { Dog, Cat, Rabbit }
Animal[0] = "Rabbit"; 
Animal[0]; // Rabbit
```

Como los *const enum* no son accesibles por índice numérico, no es posible hacer lo de arriba. Podemos concluir que son enumerados constantes.