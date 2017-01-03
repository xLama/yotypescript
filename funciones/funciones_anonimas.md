## Funciones anónimas {#funciones-an-nimas}

Las funciones anónimas son aquéllas que no tienen ningún nombre especificado.

```ts
(): void => { } function () { } // Falla por no especificar un nombre
```

Cuando declaramos una función con la palaba reservada _function_ seguido de un identificador es lo mismo que si asignáramos una función anónima a una variable pues internamente el identificar es una declaración de variable.

```ts
let add = function () { } // es equivalente a, excepto por hoisting
function add() { }
```

El ejemplo no compila pues da un error de identificador duplicado.

El problema de no tener ninguna referencia a la función es no poder invocarla más de una sola vez.

### Tipado literal de una función {#tipado-literal-de-una-funci-n}

Hemos visto que una función puede almacenarse en un objeto, ya sea mediante expresiones estándar o flechas.

La cuestión que se nos plantea es que si en TS todo está tipado, ¿cómo se tipan las funciones? Podemos pensar que con el tipo _Function_ ya sería suficiente. En un principio podría ser así ya que funciona perfectamente pero su gran inconveniente es que con él no se puede tipar de una forma más restrictiva, esto es definiendo una cabecera de función exacta.

En nuestro ejemplo:

```ts
let square = (x: number) => x * x;
```

La variable _cuadrado_ ha sido tipada por [inferencia](../tipos/inferencia_de_tipos.md#expresiones-tipadas-por-el-contexto). Si no fuera así, y se nos olvidara tiparla, resultaría que a la hora de invocarla no tendríamos la ayuda del editor para saber qué parámetros tiene.

Podríamos hacer esto:

```ts
let square: Function = (x: number): number => x * x;
```

Pero el tipado no sería tan específico y no sabríamos, a la hora de invocar la función, que parámetros acepta y qué tipo de datos devuelve, si es que devuelve alguno.

Nosotros podemos tiparla de forma explícita:

```ts
let square: (x: number) => number;
```

Esta vez la flecha no se usa para indicar el cuerpo de la función, pues estamos tipando. Sino que se utiliza para especificar el tipo devuelto. Sólo podemos tipar funciones de esta forma con expresiones flecha. Una función estándar también queda tipada por una expresión flecha:

```ts
let square: (x: number) => number = function (x: number): number { return x * x }
```

### Tipado mediante objetos literales {#tipado-mediante-objetos-literales}

Además de las formas de declarar una función que conocemos mediante _function_ o las expresiones _lambda_, podemos hacerlo mediante un objeto.

```ts
let funcion: { (x: number): string };
```

Su equivalencia es forma corta es:

```ts
let funcion: (x: number) => string;
```

Lo que aquí nos permite la primera forma es poder sobrecargar la función con más definiciones. La segunda forma sólo permite una.

```ts
let funcion: { (x: number): string; (x: string): number } = sobrecargada

function sobrecargada(x: string): number
function sobrecargada(x: number): string
function sobrecargada(x: any): any {
    return "sobrecargada";
}
```

Hemos sobrecargado la _function_ funcion con otra definición. Hay que tener en cuenta que en el tipo no hay que definir una función que englobe a las demás.

### Definición de función por parámetro {#definici-n-de-funci-n-por-par-metro}

Ahora imagina que tenemos una función cualquiera que tiene como parámetro otra función pero con una determinada definición. ¿Cómo lo haríamos?

```ts
function ejemplo(func: (x: string) => number): void {  
  //(...)
}
```

La función _ejemplo_ acepta como parámetro una función sólo si esa función acepta como parámetro un dato del tipo _string_ y devuelve uno del tipo _number_.

### Funciones anónimas autoejecutables {#funciones-an-nimas-autoejecutables}

Este tipo de funciones se pueden invocar de forma automática encerrándolas entre paréntesis y añadiendo \(\) al final. Mucho cuidado con hacer esto si queremos declarar y ejecutar de forma automática más de una función porque en este caso sí es necesario acabar la sentencia con ; \(punto y coma\)

```ts
( (): void => { alert("función flecha")} )(); // ; necesario
(function () { alert("función") })();
```



