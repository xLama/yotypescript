# Tipos no nullables

Para activar esta característica se debe hacer desde el archivo tsconfig.json estableciendo _strictNullChecks  a true_

¿Qué es lo que hace? Hemos estudiado que hay una compatibilidad de tipos predefinida en el lenguaje, es decir, any es compatible con todos los tipos, object \(sin propiedades\) también._ String, number y boolean_ solo con ellos mismo, etc. Lo que quizás no te has percatado es que puedes asignar el valor \_null \_o \_undefined \_a cualquier tipo. Y cuando digo cualquiera es cualquiera, incluso Function.

El esquema sería así:

![](/assets/TypeScript - JavaScript that scales. - Google Chrome.jpg)

Esto lo que hace es separarlos y no permitir que \_null \_y \_undefined \_sean asignables a todos los tipos, sólo a los que lo especifique de forma explícita y a ellos mismos.

De esta forma:

![](/assets/TypeScript - JavaScript that scales. - Google Chrome_2.jpg)

Ahora no podremos hacer esto

```ts
let name : string = null;
```

Una de las grandes utilidades que tiene es evitar que se pueda pasar como argumento los valores _null _o _undefined _a una función.

```ts
function countWords(str:string){
  return str.length;
}

countWords("Carlos"); // Ok
countWords(null); // Error.
```

Pero podemos, gracias a los tipos unión, aceptarlos de esta forma:

```ts
let name: string | null = null;

function countWords(str: string | null) {
    return str.length;
}

countWords("Carlos"); // Ok
countWords(null); // Error.
```

Pero aquí hay otro problema, y es otra de las características nuevas de TS 2.0. Es el control del flujo basado en el análisis de tipo. Recordamos que con las guardas de tipos podíamos hacer un estrechamiento sobre tipos en particular para que dentro de un bloque de código concreto el compilador reconociera ese tipo.

```ts
function foo(bar: string | number) {
    if (typeof bar === "string") {
        bar // bar es string
    } else {
        bar // bar es number
    }
}
```

Ahora va un paso más allá y puede reconocer que algo podría ser _undefined _o _null _y lo avisa.

```ts
let name: string | null = null;

function countWords(str: string | null) {
    return str.length; // Error. Object (str) es posiblemente undefined
}

countWords("Carlos"); // Ok
countWords(null); // Error.
```

Debido que el argumento podría ser _null_ o _undefined_, nos avisa de que podría haber un problema con ello ya que si efectivamente lo es, el código lanzará una excepción, pues el tipo _undefined _no tiene la propiedad_ length_.  
Para solucionarlo habría que usar una guarda ya sea con _typeof_ o con una simple comprobación de verdad.

```ts
function countWords(str: string | null) {
    if (str) {
        return str.length; // Ok
    }
}
```

¿Qué ventajas supone? El control de bugs, como has podido observar. Además son bugs que hasta ahora sólo eran detectables en tiempo de ejecución.

Un ejemplo más elaborado explicado paso a paso tomado de una conferencia que dio Anders Hejlsberg:

```ts
function countLines(text?: string[]): number {
    let count: number;
    for (const line of text) { // Object (text) es posiblemente undefined
        if (line.length !== 0) {
            count = count + 1; // count usada antes de ser inicializada
        }
    }
    return count; // count usada antes de ser inicializada
}

let a = countLines(["one", "two", "", "three"]);
let b = countLines(["hello", null, "world"]); // El array no admite nullos.
let c = countLines();
```

Para solucionar esto habría que darnos cuenta de dos cosas: podemos no pasar argumento alguna, ya que es opcional y eso lo convierte en _undefined_ por defecto. Y que el argumento es un array de string que no admite valores _null_ ni _undefined_

Podemos empezar por solucionar el problema con _text_

```ts
function countLines(text?: string[]): number {
    if (!text) return;

    let count: number;
    for (const line of text) { // Object (text) es posiblemente undefined
        if (line.length !== 0) {
            count = count + 1;
        }
    }
    return count;
}
```

Con el _if_ nos hemos asegurado de que _text_ no es _undefined_, y si no lo es, lo único que puede ser es un array el cual podemos iterar. Pero hay otro problema. Cuando una función devuelve algo vacío, como en este caso, lo que en realidad devuelve es _undefined_ y _undefined_ no es asignable a _number_. Así que hay que solucionarlo:

```ts
function countLines(text?: string[]): number {
    if (!text) return 0; 

    let count: number;
    for (const line of text) { 
        if (line.length !== 0) {
            count = count + 1;
        }
    }
    return count;
}
```

Ahora se devuelve 0 si _text_ es undefined. A partir de esa línea, el compilador reconocerá _text_ como _string\[\]_ y no como _string\[\] \| undefined_

Ahora lo que queda es solucionar el problema con _count_. Simplemente hay que inicializarla:

```ts
function countLines(text?: string[]): number {
    if (!text) return 0; 
    let count = 0;
    for (const line of text) { 
        if (line.length !== 0) {
            count = count + 1;
        }
    }
    return count;
}
```

Y con esto el código no tiene bugs.

¿Qué pasaría si quisiéramos que el parámetro fuera del tipo \(string \| null\)\[\]?

```ts
function countLines(text?: (string | null)[]): number {
    if (!text) return 0; 
    let count = 0;
    for (const line of text) { 
        if (line.length !== 0) { // Object (line) es posiblemente null
            count = count + 1;
        }
    }
    return count;
}
```

Nos daría el error en _line_ pues podría ser _null_. Para solucionarlo simplemente hay que asegurarnos de que _line_ no es _null_.

```ts
function countLines(text?: (string | null)[]): number {
    if (!text) return 0; 
    let count = 0;
    for (const line of text) { 
        if (line && line.length !== 0) { 
            count = count + 1;
        }
    }
    return count;
}
```

Con _if \(line && line.length !== 0\)_ es suficiente para comprobarlo. Ahora dentro del bloque _if_, _line_ es _string_.

