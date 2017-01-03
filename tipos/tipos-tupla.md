### Tipos tupla \(Tuple Types\) {#tuple-types-tipos-tupla}

Se utiliza en los arrays y sirve para determinar distintos tipos según la posición del elemento dentro del array.

```ts
let array: [number, string] = [5, "cadena"];
```

A la hora de introducir elementos en el array es obligatorio, al menos, el mismo número de ellos que de tipos declarados.

```ts
let array: [number, string] = [5]; // Error
```

Además, si introducimos un elemento no compatible con ninguno de los declarados, nos muestra un error de compilación.

```ts
let array: [number, string] = [5, "cadena", () => {}]; // Error
```

Si te estás preguntando qué tipo tendría un dato introducido en una posición en la que no se ha declarado tipo, la respuesta es la unión de tipos. ¿No te lo estabas preguntando? Deberías haberlo hecho:

```ts
let array: [number, string];
let dato = array[8]; // number | string
```



