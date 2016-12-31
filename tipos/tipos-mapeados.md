### Tipos mapeados \(Mapped Types\)

Sirven para crear plantillas de tipos. Pueden ser de 4 formas:

```ts
{ [ P in K ] : T }
{ [ P in K ] ? : T }
{ readonly [ P in K ] : T }
{ readonly [ P in K ] ? : T }
```

P siempre debe estar presente y significa "property".  
K es la lista sobre la que P puede tomar valores y debe ser compatible con _string_  
T es el tipo genérico que se devuelve.

Ejemplos tomados de Anders Hejlsberg en el Github oficial de Typescript.

Crea una tipo con las propiedades _x_ e _y_ las cuales son _number_

```ts
type T1 = { [P in "x" | "y"]: number };  // { x: number, y: number }
```

Crea una tipo con las propiedades _x_ e _y_ las cuales son del mismo tipo que P. En este caso serían "x" e "y", ya que son tipos string literales:

```ts
type T2 = { [P in "x" | "y"]: P };  // { x: "x", y: "y" }
```

Se puede combinar con el operador _keyof_ para facilitarnos la vida.  
Crea un tipo con las propiedades de _Item_ manteniendo el mismo tipo de cada propiedad, es decir, no altera el tipo original en nada.

```ts
type Item = { a: string, b: number, c: boolean };
type T5 = { [P in keyof Item]: Item[P] };  // { a: string, b: number, c: boolean }
```

Crea un tipo con las propiedades de _Item_ cambiado el tipo de cada propiedad a _Date_

```ts
type T4 = { [P in keyof Item]: Date };  // { a: Date, b: Date, c: Date }
```

Tanto ? como readonly funcionan de la misma manera, es decir, crean plantillas pero en el que las propiedades son opciones o de sólo lectura.

```ts
type T6 = { readonly [P in keyof Item]: Item[P] };  // { readonly a: string, readonly b: number, readonly c: boolean }
type T7 = { [P in keyof Item]: Array<Item[P]> };  // { a: string[], b: number[], c: boolean[] }
```

Podemos deducir que su utilidad reside, más que en crear tipos totalmente nuevos, en modificar los ya existentes que de otra forma requerirían repetir código.

El lenguaje tiene definidos 4 tipos mapeados genéricos muy interesantes que nos evitan tener que declararnos por nosotros mismos. Esto son: Partial, Readonly, Record, y Pick. Esto se pueden usar en cualquier momento pues forman parte de la librería de Typescript.

**Partial **convierte todas las propiedades de un tipo en opcionales.

```ts
type Partial<T> = {
    [P in keyof T]?: T[P];
};
 type Item = { a: string, b: number, c: boolean };
 type ItemPartial = Partial<Item>;
```

**Readonly **convierte todas las propiedades de un tipo en en propiedades de sólo lectura:

```ts
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

type Item = { a: string, b: number, c: boolean };
type ItemReadOnlye = Readonly<Item>;
```

**Pick **crea un tipo a partir de las propiedades de otro tipo manteniendo el tipo de dichas propiedades. Más concretamente crea un subconjunto de otro tipo.

```ts
type Pick<T, K extends keyof T> = {
    [P in K]: T[P];
}
type ItemReadOnlye = Pick<Item, "a">;
```

**Record **crea un tipo a partir de las propiedades especificadas pudiendo establecer el tipo de dichas propiedades.

```ts
type Record<K extends string, T> = {
    [P in K]: T;
}
type myType= Record<"b" | "c" | "d", number>; // {b: number, c: number, d:number}
```

Se puede combinar con el operador _keyof _para construir el tipo a partir de otro

```ts
type Item = { a: string, b: number, c: boolean };
type ItemNumber= Record<keyof Item, number>; // {a: number, b: number, c:number}
```

Partial, Readonly, Pick y Record puden ser usados entre sí para crear tipos más complejos.

Vamos a crear un subtipo de _Item_ tomando sólo dos propiedades a las que le vamos a cambiar el tipo y las vamos a hacer opcionales y de sólo lectura:

```ts
type ItemAll = Readonly<Partial<Record<keyof Pick<Item, "a">, Date>>>
// {readonly a?: Date}
```
Si vamos a usarlos todo es aconsejable seguir un orden concreto con el que podamos hacernos un mapa mental. Mi consejo personal es que primero filtremos las propiedades que queramos con Pick. Acto seguido cambiarle el tipo a esas propiedades con Record y ya por último hacelos opcionales con Partial y de sólo lectura con Readonly.

