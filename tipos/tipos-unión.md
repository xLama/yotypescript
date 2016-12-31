### Tipos Unión \(Union Types\) {#tipos-uni-n-union-types}

Los tipos unión determinan qué tipo de datos puede albergar una variable. Normalmente tipamos las variables con un solo tipo pero con esta característica podemos hacerlo con varios.

```ts
let x: number | string = "cadena"; // Correcto
x = 12; // Correcto
x = false; // Error
```

Además se pueden crear tipos unión de forma automática en las [interfaces](../interfaces/README.md) o [clases](../clases/README.md).

```ts
class A {
    x: string;
}

class B {
    x: number;
}
let variable: A | B;
variable.x // Es del tipo string | number
```

Cuando se habla de compatibilidad de tipos es lógico pensar que un tipo unión es compatible con todos los tipos que lo componen. Esto quiere decir que se aplica siempre que TypeScript esté comparando tipos ya sea en clases, interfaces, genéricos, etc.

