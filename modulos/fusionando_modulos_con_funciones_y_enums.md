## Fusionando módulos con funciones y enums {#fusionando-m-dulos-con-funciones-y-enums}

Es una posibilidad muy interesante que nos permite añadir atributos a las funciones o métodos a los enums.

### Funciones {#funciones}

```ts
function fusion():void{ 
  alert("fusión");
}

module fusion { 
  export var fusion: number = 1;
}
```

Primero se declara la función y después el módulo a fusionar con el mismo nombre. De esta forma tenemos acceso a lo exportado en el módulo desde el nombre de la función. Incluso podemos usarlo dentro de la propia función.

```ts
function fusion():void { 
  funsion.fusion;
}

module fusion { 
  export var fusion: number = 1;
}
```

### Enums {#enums}

De la misma forma que se fusionan las funciones y los módulos lo hacen los _enums_.

```ts
enum Directions { Left, Rigth, Top, Down }

module Directions {
    export function diagonal(c1: Directions) {
        // Código
    }
}

Directions.diagonal(Directions.Left);
```