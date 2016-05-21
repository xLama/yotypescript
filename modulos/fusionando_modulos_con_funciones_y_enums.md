## Fusionando módulos con funciones y enums {#fusionando-m-dulos-con-funciones-y-enums}

Es una posibilidad muy interesante que nos permite TS por la podemos añadir atributos a las funciones o métodos a los enums.

### Funciones {#funciones}

**function** fusion():**void**{ alert("fusión");}

**module** fusion { **export var** fusion: **number** = 1;}

Primero se declara la función y después el módulo a fusionar con el mismo nombre. De esta forma tenemos acceso a lo exportado en el módulo desde el nombre de la función. Incluso podemos usarlo dentro de la propia función.

**function** fusion():**void** { funsion.fusion;}

**module** fusion { **export var** fusion: **number** = 1;}

### Enums {#enums}

De la misma forma que se fusionan las funciones y los módulos lo hacen los _enums_.

**enum** Direcciones { Izquierda, Derecha, Arriba, Abajo }**module** Direcciones { **export** **function** diagonal(c1: Direcciones) { **** // Código}****}****Direcciones.diagonal(Direcciones.Izquierda);