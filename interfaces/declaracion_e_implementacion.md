## Declaración e implementación {#declaraci-n-e-implementaci-n}

Para crear una interfaz se usa la palabra reservada _interface_.

```ts
**interface** Desplazable { }
```

Para que una clase implemente una interfaz se utiliza la palabra reservada _implements_:

```ts
**class** Persona **implements** Desplazable {**** //...}
```
La interfaz _Desplazable_ está vacía por lo que no está obligando a la clase _Persona_ a hacer nada. Pero si en _Desplazable_ definimos un método:

```ts
**interface** Desplazable {**** desplazar (): **void**;}
```
Obligamos a la clase _Persona_ a implementarlo. Si no lo hace dará error de compilación. Para ello hay que cumplir exactamente con la definición del método. Si devuelve un **number** no podemos implementar ese método devolviendo un **string**. En este caso no devuelve nada por lo que así debe ser:

```ts
**class** Persona **implements** Desplazable { **** //(...) **public** desplazar(): **void** { }****}
```
La interfaz no obliga a una implementación específica del método, esto dependerá en cada situación. Así pues 10 clases distintas pueden implementar _Bipedo_ siendo el cuerpo del método distinto en todas ellas.

Cabe decir que al contrario de la herencia de clases, sí se permite la implementación múltiple de interfaces.

```ts
**cla```ss** Persona **implements** Desplazable, Inteligente{**** //(...)}

Por otro lado no sólo puedes obligar a implementar métodos, sino también a poseer atributos.

```ts
**interface** Desplazable { **** velocidad: **number**; desplazar(): **void**;}
```
Los atributos pueden ser opcionales por lo que no obligaría a la clase a implementarlos.

```ts
**interface** Desplazable {**** velocidad?: **number**; desplazar(): **void**;}
```
Las interfaces no pueden contener miembros privados o estáticos.

```ts
**interface** Desplazable { **** velocidad?: **number**; **private** desplazar(): **void**; // Error de compilación}
```