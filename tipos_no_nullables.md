# Tipos no nullables


Para activar esta característica se debe hacer desde el archivo tsconfig.json strictNullChecks *true*

¿Qué es lo que hace? Hemos estudiado que hay una compatibilidad de tipos predefinida en el lenguaje, es decir, any es compatible con todos los tipos, object (sin propiedades) también,
string, number y boolean solo con los suyos y así sigue. Lo que quizás no te has percatado es que puedes asignar el valor null o undefined a cualquier tipo. Y cuando
digo cualquiera es cualquiera, incluso Function.

Esto lo que hace es separarlos y no permitir que null y undefined sean asignables a todos los tipos, sólo a los que lo especifique de forma explícita.
IMAGEN DE EJEMPLO

Ahora no podremos hacer Esto

```ts
let name : string = null;
```

Una de las grandes utilidades que tiene es evitar que se pueda pasar como argumento los valores null o undefined a una función.

```ts
function countWords(str:string){
  return str.length;
}

countWords("Carlos"); // Ok
countWords(null); // Error. 
```

Pero podemos, gracias a los tipos union, aceptarlos de esta forma:

```ts
let name: string | null = null;

function countWords(str: string | null) {
    return str.length;
}

countWords("Carlos"); // Ok
countWords(null); // Error. 
```

Pero aquí hay otro problema, y es otra de las características nuevas de TS 2.0. Es el control del flujo basado en el análisis de tipo. Recordamos que con las gardas de tipos, podíamos hacer un estrechamiento sobre tipos en particular para que dentro de un bloque de código concreto, el compilador reconociera ese tipo. 

```ts
function foo(bar: string | number) {
    if (typeof bar === "string") {
        bar // bar es string
    } else {
        bar // bar es number
    }
}
```
Ahora va un paso más allá y puede reconocer que algo podría ser undefined o null y lo avisa.

```ts
let name: string | null = null;

function countWords(str: string | null) {
    return str.length; // Error. Object (str) es posiblemente undefined
}

countWords("Carlos"); // Ok
countWords(null); // Error. 
```

Debido que el argumento podría ser *null* o *undefined*, nos avisa de que podría haber un problema con ello ya que si efectivamente lo es, el código lanzará una excepción.
Para solucionarlo habrñia que usar una guarda ya sea con *typeof* o con una simple comprobación de verdad.

```ts
function countWords(str: string | null) {
    if (str) {
        return str.length; // Error. Object (str) es posiblemente undefined
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

Para solucionar esto habría que darnos cuenta de dos cosas: podemos no pasar argumento alguna, ya que es opcional y eso lo convierte en *undefined* por defecto. Y que el argumento es un array de string que no admite valores *null* ni *undefined*

Podemos empezar por solucionar el problema con *text*

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
Con el *if* nos hemos asegurado de que *text* no es *undefined*, y si no lo es, lo único que puede ser es un array el cual podemos iterar. Pero hay otro problema. Cuando una función devuelve algo vacío, como en este caso, lo que en realidad devuelve es *undefined* y *undefined* no es asignable a *number*. Así que hay que solucionarlo:

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

Ahora se devuelve 0 si *text* es undefined. A partir de esa línea, el compilador reconocerá *text* como *string[]* y no como *string[] | undefined*

Ahora lo que queda es solucionar el problema con *count*. Simplemente hay que inicializarla:

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

¿Qué pasaría si quisiéramos que el parámetro fuera del tipo (string | null)[]? 


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

Nos daría el error en *line* pues podría ser *null*. Para solucionarlo simplemente hay que asegurarnos de que *line* no es *null*.


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
Con *if (line && line.length !== 0)* es suficiente para comprobarlo. Ahora dentro del bloque *if*, *line* es *string*.
