## Funciones genéricas {#funciones-gen-ricas}

No sólo las clases o interfaces pueden ser genéricas, las funciones o métodos también.

La mecánica es la misma:

```ts
function arrayDeObjetos<T>(c: T, a?: T[]): T[] {
    a = a || new Array<T>();
    a.push(c); 
    return a;
}
```

Para invocarla se hace de la misma forma.


```ts
let autos = arrayDeObjetos<T>(new Automovil());
```