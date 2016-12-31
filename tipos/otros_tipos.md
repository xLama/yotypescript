## Otros tipos {#otros-tipos}

### Void {#void}

Sólo sirve para determinar que una función no devuelve ningún valor. También se podrían tipar variables con void pero carece de sentido.

### Null {#null}

No se puede tipar una variable con _Null._ Sólo puede ser el valor de la variable. Cualquier tipo de variable puede contener el valor _null_. Representa valor nulo.

```ts
let variable: Boolean = null;
```

### Undefined {#undefined}

Representa variables no inicializadas. También podemos asignar el valor _undefined_ a una variable de cualquier tipo siempre que no tengamos activado strictNullChecks::

```ts
let variable: Boolean = undefined;
```

### Never {#never}

Representa valores que nunca pueden ocurrir.

### [Enum](../control_del_flujo/sentencias_utiles_para_los_bucles.md#757309351116418-_Enumerados) {#enum}

Es una forma más amigable de representar números.

```ts
enum Animals { Dog, Cat };
let dog = Animals.Dog;
```

_Dog_ representaría el 0, _Cat_ el 1 y así sucesivamente.

### [Function](../enumerados/obteniendo_el_nombre_del_valor.md#757309351116418-_Funciones) {#function}

En TS, como en JS, una función también es un objeto y se puede almacenar como tal.

```ts
let funcion: Function;
```

### [Array](../modulos/evitar_que_una_clase_pueda_ser_superclase.md#757309351116418-_Anexo_I._) {#array}

Los arrays son colecciones de datos. Podemos declarar un array de dos formas:

```ts
let array1: Array<tipoDato>;
let array2: tipoDato[]; /* Personalmente uso esta forma */
```

Son compatibles entre sí al 100% y se pueden asignar de forma recíproca.

tipoDato se refiere al tipo de dato de los objetos que va almacenar el array:

```ts
let array1: number[];
let array2: string[];
```

Incluso otro array;

```ts
let arrayDeArrays: number[][];
```

Para inicializarlos tenemos, a su vez, dos formas:

```ts
let array1: Array<number> = new Array<number>();
let array2: number[] = [];
```

En _array2_ podríamos incluso introducir valores separados por comas:

```ts
let array2 = [1, 2, 3, 4, 90];
```

No hace falta determinar el tamaño del array. Este tipo tiene un tamaño dinámico que puede ir cambiando según las necesidades.

### Object {#object}

Toda la información relevante a este tipo está disponible en [este tema](../objetos/README.md).

### Symbols {#symbols}

Sólo existen a partir de la ES6 \(ES2015\).

Son valores únicos e inmutables, es decir, una vez declarados e inicializados no se pueden modificar y no puede haber dos iguales. Para instanciarlos se usa la función _Symbol_. No es posible utilizar el operador _new_ ya que daría un _TypeError_. El tipo es _symbol_

```ts
let aSymbol  = Symbol();
let otherSymbol = **new** Symbol(); // Error
```

Se le puede pasar un _string_ como argumento a la función _Symbol_ que sirve como identificador:

```ts
let aSymbol = Symbol("aSymbol");
```

Esto no quiere decir que si creamos dos _symbol_ con un mismo indentificador, estos sean iguales:

```ts
Symbol("aSymbol") === Symbol("aSymbol"); // False
```

Una de las grandes utilidades de los _symbol_ es que pueden ser usados como [propiedades de objetos](../objetos/propiedades_computadas_computed_properties.md#propiedades-symbol). Además existen los llamados “bien conocidos” que son _symbol_ predefinidos que sirven para identificar funcionalidades específicas, como los [iteradores.](../iteradores/README.md)

