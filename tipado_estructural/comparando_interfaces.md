## Comparando interfaces {#comparando-interfaces}

La comparación de interfaces se hace igual que la comparación de clases: miembro a miembro. Aunque resulta más simple por no tener miembros privados ni protegidos.

Esto es correcto:

```ts
interface A {
    name: string;
}

interface B {
    name: string;
}

let a: A;
let b: B;
a = b;
b = a;
```

De nuevo se aplica la máxima en las comparaciones de objetos: el objeto con más miembros puede ser asignado al objeto con menos, pero no al revés.

```ts
interface A { 
    name: string; print(); 
}
interface B { 
    name: string; 
}
let a: A; 
let b: B = b; // Error
b = a;
```