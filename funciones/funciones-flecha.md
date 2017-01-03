### Funciones flecha \(Expresiones lambda\) {#expresiones-lambda-funciones-flecha}

TS nos proporciona otra sintaxis a la hora de declarar una función que resulta bastante interesante, llamada funciones flecha.

Siguiendo con el ejemplo anterior, otra forma de declarar _sumar_ sería:

```ts
let example = (x: number) => {
    return 0;
};
```

Entre paréntesis se especifica la lista de parámetros seguido de : \(dos puntos\) para especificar el tipo devuelto por la función. Por último el =&gt; para definir el cuerpo de la función. Realmente no es necesario encerrarlo entre llaves {} pero si se hace debe aparecer la palabra clave _return_

Son equivalentes:

```ts
let example = (x: number): number => {
    return 0;
};
let example = (x: number) => 0;
```

Incluso podemos usar los parámetros en el cuerpo sin llaves:

```ts
let square = (x: number) => x * x;
```

En el caso de las funciones flecha la única posibilidad es la de asignarla a una variable pues su sintaxis no permite darle un nombre en la propia declaración

```ts
let funcion = (): void => { }
```

### Contexto {#contexto}

Este apartado se encuentro mejor explicado [aquí](/this.md)

