## Módulos externos {#m-dulos-externos}

Estos son usados normalmente junto con otras librerías como RequireJS o trabajando con Node.js. La idea es que la carga sea bajo demanda, es decir, sólo cuando lo necesitemos.

### Exportando {#exportando}

Lo primero que hay que hacer es declarar algún módulo como exportado para que pueda ser importando posteriormente. Lo habitual es tener un módulo por archivo, aunque no es obligatorio.

Persona.ts:

**export** **class** Persona { }

También podemos exportarlos de esta forma.

Persona.ts

**class** Persona { }**export** { Persona };

Si tenemos más de un miembro con el mismo nombre, se exportarán ambos.

Persona.ts:

**export** **class** Persona { }**export** **interface** Persona { }**export** { Persona };

Además podemos renombrar un miembro al ser exportado.

Persona.ts:

**export** **class** Persona { }**export** { Persona as Person };

Una forma más fácil de exportar uno miembro es con la plabara reservada _default_. Sólo puede haber un miembro _default_ por módulo ya que con él se marca el único o más relevante del mismo.

Persona.ts

**export** **class** Persona { }**export** { Persona as default };

Sería equivalente a.

Persona.ts:

**export** **default** **class** Persona { }

### Importando {#importando}

Ya que hemos aprendido a exportar miembros, debemos aprender a importarlos para poder usarlos. Para ello es tan fácil como lo que sigue.

App.ts

**import** { Persona } from"./Persona";**var** persona:Persona;

Por supuesto también podemos renombrarlo.

App.ts:

**import** { Persona as Person } from"./Persona";**var** persona:Person;

Si se quiere importar todo el módulo con todos los miembros exportados podemos hacerlo con el * y nombrándolo como nos convenga. Para usar los miembros debemos referenciarlos con el nombre elegido en el renombrado seguido del nombre del miembro, separado por un punto.

App.ts

**import** * as P from"./Persona";**var** persona:P.Persona;

Si delaramos un miembro como _default_ a la hora de exportarlo, nos va a facilitar las cosas al importarlo. De esta forma no es necesario que encerremos entre llaves el miembro a importar.

**import** Persona from"./Persona";**var** persona:Persona;

Sería equivalente a esto.

App.ts:

**import** { default as Persona } from"./Persona";**var** persona:Persona = **new** Persona();

Si te estás preguntando cómo importar el mimebro _default_ y el resto, se hace así.

App.ts

**import** Persona, { otroMiembro } from"./Persona";**var** persona:Persona = **new** Persona();

### Cómo generarlos {#c-mo-generarlos}

Es importante aclarar que la sintaxis de los módulos externos vista hasta ahora es de la ECMAScript 6\. Eso quiere decir que si configuramos el compilador para que genere código ES6 el resultado será invariable. Es así porque el nuevo ES6 incorpora una gestión de módulos propia, cosa que hasta día de hoy debían hacer herramientas externas.

No ocurre así si compilamos para ES3 o ES5\. En ese caso necesitamos librerías externas para su uso, además de parametrizar el compilador con el tipo de módulo a utilizar, dándonos cuatro opciones. Éste se debe cambiar en el archivo tsconfig.json con el parámetro _module_

“commonjs” : Normalmente si usamos Node.js “amd” : Necesitamos la librería RequireJS para que funcione. Ésta debe estar agregada en el &lt;head&gt; del HTML como otro archivo .js cualquiera.

“umd” : Debido a que podríamos querer compilarlo como commonjs como amd, esta opción nos provee una forma que aglutina a ambos.

“system” : Es otra forma utilizar módulos de manera universal pero requiere otra librería, System.js.

Si bien el caso típico de una aplicación para navegador sería el uso de módulos amd con la librería RequireJS: [http://requirejs.org/](http://requirejs.org/)

TypeScript nos provee un nivel más de abstracción al agrupar los métodos de modularización más populares de JS a la vez que lo hace compatible con la nueva versión del estándar.

### Compatibilidad con la antigua sintaxis {#compatibilidad-con-la-antigua-sintaxis}

La forma de tratar los módulos ha cambiado a partir de la versión 1.5 de TS. Debido al trabajo ya generado en versiones anteriores, se ha mantenido cierta compatibilidad a la antigua sintaxis. Se recomienda usar siempre la nueva pues la otra está obsoleta y no se sabe a ciencia cierta cuándo dejará de estar operativa.

Persona.ts:

**class** Persona { }**export** = Persona;

Esta forma de exportación no se puede utilizar si ya se está exportando con la nueva sintaxis. Además para importalo se debe usar también la antigua

App.ts:

**import** Persona = require("Persona") MAL**var** persona:Persona = **new** Persona();

Lo único compatible es la exportación de módulos internos

Persona.ts:

**module** Humano { **export** **class** Persona { }}**export** = Humano;

App.ts

**import** { Persona } from"./Persona";**var** persona:Persona = **new** Persona();

El nombre del módulo _Humano_ no se usa en la importación, es decir, al hacer export = Humano lo que se exporta realmente son los miembros declarados como _export_ del módulo _Humano_ y no el módulo en sí. Para importar el módulo completo:

App.ts

**import** * as Humano from"./Persona";**var** persona:Humano.Persona = **new** Humano**.**Persona();

Es preciso indicar que esta forma de importación no es posible si lo exportado no es un módulo o una variable

Persona.ts

**export** **class** Persona { }**export** = Persona;

App.ts

**import** * as Persona from"./Persona"; // Error**var** persona: Persona = **new** Persona();