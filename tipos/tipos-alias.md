### Tipos Alias \(Alias Types\) {#tipos-alias-alias-types}

Este tipo es simplemente llamar de otra forma a un tipo ya definido. Se usa la palabra reservada _type._ Es útil para los tipos unión e intersección

```ts
type numberAndString = number | string;
let numstr :numberAndString // Es del tipo string | number
```

También es compatible con los [genéricos](../genericos/README.md):

```ts
class Collection<T> {
    private list: T[];
}
type List<T> = T[] | Collection<T>;
type ListNumber = List<number>;

let list: ListNumber = [];
let list2: ListNumber = new Collection<number>();
```



