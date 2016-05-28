## Relación con las interfaces {#relaci-n-con-las-interfaces}

Todo lo mostrado en este tema puede realizarse mediante [interfaces](../interfaces/README.md). La diferencia más notable es que una clase no puede implementar un tipo objeto literal, ni éste puede hacer uso de la herencia. El resto es exactamente igual.

Todos los ejemplos que hacen uso del tipo _Person_ en este tema, podrían haber escrito de la siguiente forma sin modificar de ninguna manera la semántica.

```ts
interface Person { 
  name: string; 
  age: number;
}
```