### Tipos Locales \(Local Types\) {#tipos-locales-local-types}

No son más que clases, interfaces, enumerados y tipos alias que se declaran dentro un bloque de cógido \(entre llaves\). Estos son sólo accesibles en ese bloque, al igual que ocurre con las variables declaradas con el operador _let_.

```ts
function local() {
    if (Math.random() > 0.5) {
        interface Baz { }
    }
    let bar: Bar = new Bar(); /*Error. Bar solo accessible dentro del if */
    class Foo { };
}

let bar: Foo = new Foo(); /* Error. Foo solo es accessible dentro de local() */
```



