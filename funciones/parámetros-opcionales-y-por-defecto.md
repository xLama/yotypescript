### Parámetros opcionales y por defecto {#par-metros-opcionales-y-por-defecto}

En TS podemos hacer que un parámetro de una función sea opcional, e incluso asignarle un valor por defecto. Para hacer que sea opcional escribimos el símbolo _?_ justo después del nombre del parámetro.

```ts
function sum(x: number, z?: number) {
  return x * y;
}
```

Si llamamos a la función sólo con un argumento:

```ts
sumar(10);
```

E inspeccionamos el valor de _z_, nos daría _undefined_, pues no lo hemos especificado.

Pero si llamamos a la función pasándole dos argumentos:

```ts
sumar(10,20);
```

El valor de _x_ sería 10 y el de _z_ sería 20.

También podemos asignar un valor por defecto.

```ts
function sum(x: number, z = 20):  {
  return x * z;
}
```

De esta forma, aunque llamemos a la función con sólo un argumento, la _z_ valdrá 20 y no _undefined_.

Los parámetros opciones e inicializados no pueden colocarse delante de uno no opcional ni inicializado.

```ts
function sum(x?: number, z: number) { } // Error
function sum(x = 20, z: number): { } // Error
```



