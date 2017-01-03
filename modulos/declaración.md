## Declaración {#introducci-n}

Para crear uno basta con encerrar el código que queramos en un bloque _module o namespace_:

```ts
module M {
  // Código
}
```

Es similar a:

```ts
namespace M { 
  // Código
}
```

> Esto responde a una estrategia en las nuevas versiones de TypeScript debido a que los módulos externos en ECMAScript 6 se llaman modules y es una forma de distinguirlos sintácticamente Además namespace es una palabra más usada en los lenguajes orientados a objetos por lo que se busca cercanía.

Añadimos nuestras clases o interfaces normalmente. Para que sean accesibles desde fuera del módulo necesitamos declararlas como _export_.

```ts
namespace M { 
  export class A { }
}
```

Para acceder a ella basta con escribir el nombre del módulo seguido del nombre de la clase.

```ts
var a: M.A = new M.A();
```

También pueden contener variables ya inicializadas o no.

```ts
namespace M { 
  export class A { } 
  export var a = 1;
}
```

Se puede declarar una ruta completa para un módulo de la forma:

```ts
namespace M.A.B {
  export class A { }
}
```

Y para acceder a la clase _A_ habría que escribir: M.A.B.A

