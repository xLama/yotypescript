### Más parámetros {#par-metros-opcionales-y-por-defecto}

Existe una forma de aceptar una lista infinita de argumentos por parámetro. En TS se llama “el resto de parámetros”.

Es bastante sencillo:

```ts
function more(x: number, ...moreParams) {
    return x;
}
```

Como puedes observar, basta con definir un parámetro más anteponiendo… \(tres puntos suspensivos\) a su nombre. Será del tipo _Array_ de A_ny_. Podemos tiparlo para que sea un _Array_ de otra cosa pero siempre un _Array_.

```ts
function more(...moreP: number[]) { }
```

Este parámetro especial no puede ser opcional ni puede estar inicializado.

```ts
function more(...moreP?: number[]): void { }; // Error
function more(...moreP: number[] = []): void { }; // Error
```

Para usarlo lo hacemos como si de un _array_ cualquiera se tratara.

```ts
function adder(...moreP: number[]) {
    let total = 0;
    for (let num of moreP) {
        total += num;
    }
    return total;
}
let sum = adder(3, 56, 89, 12, 56); // 216
```

La función suma todos los números del array introducido como argumento y devuelve el resultado.

