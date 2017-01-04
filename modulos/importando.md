## Importando {#m-dulos-externos}

Ya que hemos aprendido a exportar miembros, debemos aprender a importarlos para poder usarlos. Para ello es tan fácil como lo que sigue. Atención al ./ ya que sin él no lo buscaría en un archivo, sino que lo trataría como un módulo ambiental.

App.ts

```ts
import { Person } from"./Person"; /
var person : Person;
```

Por supuesto también podemos renombrarlo.

App.ts:

```ts
import { Person as Persona } from "./Person";
let persona: Persona;
```

Si se quiere importar todo el módulo con todos los miembros exportados podemos hacerlo con el \* y nombrándolo como nos convenga. Para usar los miembros debemos referenciarlos con el nombre elegido en el renombrado seguido del nombre del miembro, separado por un punto.

App.ts

```ts
import * as P from "./Person";
let person:P.Person;
```

Si delaramos un miembro como _default_ a la hora de exportarlo, nos va a facilitar las cosas al importarlo. De esta forma no es necesario que encerremos entre llaves el miembro a importar.

```ts
import Person from"./Person";
let person: Person;
```

Sería equivalente a esto.

App.ts:

```ts
import { default as Person } from "./Person";
let person: Person;
```

Si te estás preguntando cómo importar el mimebro _default_ y el resto, se hace así.

App.ts

```ts
import Person, { other } from "./Person";
```

### Cómo generarlos {#c-mo-generarlos}

Es importante aclarar que la sintaxis de los módulos externos vista hasta ahora es de la ECMAScript 6. Eso quiere decir que si configuramos el compilador para que genere código ES6 el resultado será invariable. Es así porque el nuevo ES6 incorpora una gestión de módulos propia, cosa que hasta día de hoy debían hacer herramientas externas.

No ocurre así si compilamos para ES3 o ES5. En ese caso necesitamos librerías externas para su uso, además de parametrizar el compilador con el tipo de módulo a utilizar, dándonos cuatro opciones. Éste se debe cambiar en el archivo tsconfig.json con el parámetro _module_

* commonjs : Normalmente si usamos Node.js

* amd : Necesitamos la librería RequireJS para que funcione. Ésta debe estar agregada en el &lt;head&gt; del HTML como otro archivo .js cualquiera.

* system : Es otra forma utilizar módulos de manera universal pero requiere otra librería, System.js.

* umd : Debido a que podríamos querer compilarlo como commonjs como amd, esta opción nos provee una forma que aglutina a ambos.

Si bien el caso típico de una aplicación para navegador sería el uso de módulos amd con la librería RequireJS: [http://requirejs.org/](http://requirejs.org/)

TypeScript nos provee un nivel más de abstracción al agrupar los métodos de modularización más populares de JS a la vez que lo hace compatible con la nueva versión del estándar.

### Compatibilidad con la antigua sintaxis {#compatibilidad-con-la-antigua-sintaxis}

La forma de tratar los módulos ha cambiado a partir de la versión 1.5 de TS. Debido al trabajo ya generado en versiones anteriores, se ha mantenido cierta compatibilidad a la antigua sintaxis. Se recomienda usar siempre la nueva pues la otra está obsoleta y no se sabe a ciencia cierta cuándo dejará de estar operativa.

Person.ts:

```ts
class Person { }
export = Person;
```

Esta forma de exportación no se puede utilizar si ya se está exportando con la nueva sintaxis. Además para importalo se debe usar también la antigua

App.ts:

```ts
import Person = require("Person") // Error
let person: Person;
```

Lo único compatible es la exportación de módulos internos

Person.ts:

```ts
namespace Human {
    export class Person { }
}
export = Human;
```

App.ts

```ts
import { Person } from "./Person";
let person: Person;
```

El nombre del módulo _Human_ no se usa en la importación, es decir, al hacer export = Human lo que se exporta realmente son los miembros declarados como _export_ del módulo _Humano_ y no el módulo en sí. Para importar el módulo completo:

App.ts

```ts
import * as Human from "./Person";
let person: Human.Persona;
```

Es preciso indicar que esta forma de importación no es posible si lo exportado no es un módulo o una variable

Person.ts

```ts
export class Person { } 
export = Person;
```

App.ts

```ts
import * as Person from "./Person"; // Error
let person: Person;
```



