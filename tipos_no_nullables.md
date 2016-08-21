# Tipos no nullables


Para activar esta característica se debe hacer desde el archivo tsconfig.json stricnullshceck true...

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
¿Qué ventajas supone? Una de las grandes ventajas es que , gracias al control del fujo, podemos evitar busg que de otra forma solo serian detectables 
en tiempo de ejecución.

Un ejemplo sencillo para ir entrando en materia.

function getLast(name: string){
    return name....  // Error. Object es posiblemente undefined


}

¿Por qué ese error? Como hemos dicho, ni null ni undefined son asignables a string
