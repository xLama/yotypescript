## TypeScript {#typescript}

TypeScript (a partir de ahora TS) es un lenguaje de programación de código abierto desarrollado por Microsoft.

La primera versión se liberó en 2012 y a fecha de la edición del libro la última es la 1.8.10.

Su estándar es el ECMAScript como lo es también de ActionScript (a partir de ahora AS). TS es un superconjunto de JS que le proporciona una capa de orientación a objetos. Por ello no existe ningún navegador que ejecute TS de forma nativa sino que todo el código es traducido a JS.

Entre sus mejores características está la compatibilidad con todo el código JS existente. Podemos usar librerías como jQuery sin problemas pues TS es JS.

### ¿Por qué TypeSript? {#por-qu-typesript}

JS se diseñó para ser un lenguaje con el que desarrollar pequeñas funcionalidades en la web. Con el paso del tiempo y la llegada de las aplicaciones ricas en Internet (RIA) su uso no sólo se ha extendido, sino que el propio lenguaje se ha visto superado por las circunstancias.

Los proyectos son cada vez más complejos y necesitan mejores funcionalidades. No era un lenguaje pensado para grandes aplicaciones por lo que la dificultad para desarrollarlas ha ido en aumento, siendo un verdadero quebradero de cabeza por sus particularidades como su singular orientación a objetos mediante prototipos. Por otro lado no es posible hacer borrón y cuenta nueva y dejar de darle soporte porque está tan arraigado al mundo web que prácticamente el 99% de las webs actuales no funcionarían, lo que obligaría a hacer nuevos desarrollos. Ante esta tesitura y la cada vez más fuerte presión de la comunidad, se intentaron hacer cambios para, de cierta manera, mitigar estos problemas que ha venido arrastrando. Alternativas como CoffeScript o LiveScript surgieron para este propósito aunque con un éxito moderado. Microsoft ha decidido dar un paso al frente y lanzar su propia adaptación, que introduce cambios significativos como el tipado estático, clases, interfaces, etc, con una sintaxis similar a Java.

### Qué es y no es TypeScript {#qu-es-y-no-es-typescript}

TS no es nada por sí mismo puesto que su código no se compila ni se interpreta, sino que se traduce a JS. Una vez traducido, estaríamos ante código JS nativo interpretable por cualquier software que lo permita, como un navegador web.

### TS es JS {#ts-es-js}

Hay ciertas características de TS que son traducibles a JS de una forma más o menos análoga, como las clases. Hay otras, en cambio, que no, como las interfaces, las cuales no generan código alguno, es decir, sólo existen para comprobaciones en tiempo de compilación.

El objetivo de TS, además de ofrecernos un lenguaje más cercano, es el de unificar las características de las distintas versiones de ECMAScript. Éstas se van sucediendo con el paso del tiempo añadiendo nuevas y buenas funcionalidades. TS intenta unificarlas añadiendo lo nuevo a las versiones anteriores, de forma que podamos usarlas en navegadores más antiguos. Es evidente que lo hace de forma que la funcionalidad en sí sea la misma, habiendo diferencias en el código generado.

Para ejemplarizarlo, podemos tener en cuenta la sentencia _let._ Ésta permite declarar una variable cuyo ámbito es de bloque y no de función. No existe en ECMAScript 3 y 5 pero sí en la 6 y superiores. Si usamos esta característica, el JS generado será distinto si lo traducimos para 3 y 5 que si lo hiciéramos para la 6. En los dos primeros, seguiría usando la sentencia *var* (_let daría un error) y la comprobación del ámbito la haría TS en tiempo de compilación. Si observamos el código generado para la 6, veremos que no cambiaría con respecto al original.

No todos los navegadores webs con compatibles con todas las funcionalidades de todos los estándares de ECMAScript, por lo que hay que tener cuidado a la hora escribir nuestro código TS, pues el uso de ciertas características lo haría inejecutable en algunos navegadores.

Aquí podemos ver una lista de ECMAScript 5 y 6 y su compatibilidad.

[http://kangax.github.io/compat-table/es5/](http://kangax.github.io/compat-table/es5/)[http://kangax.github.io/compat-table/es6/](http://kangax.github.io/compat-table/es6/)

Cada archivo .ts se compila en su homólogo .js, incluyendo en él todo el código traducido de TS a JS. Lo que normalmente conviene hacer es unificar todo el código JS resultante en un solo archivo .js que posteriormente distribuiremos. Además, también se crean de forma automática archivos .maps que relacionan los .ts con los .js. Estos son muy útiles para la [depuración](../depuracion/depurando_ts.md) de TS.

Realmente TS no se compila ni se interpreta, sino que se traduce. A lo largo del libro se usarán los términos relativos a la compilación para referirse al proceso de traducción de TS a JS. Si bien no es el uso correcto sí que es el más amigable para la mayoría de los programadores. Un herramienta de este tipo se cataloga com “transpiler” (translator + compiler) que en español podría acuñarse como trapilador (traductor + compilador).

### Requisitos {#requisitos}

El principal requsito para trabajar con TS es Node.js. Si instalamos el IDE Visual Studio 2012 ó 2013 junto con la actualización que los hace compatible con TypeScript, Node.js se instalará de forma automática. Si no, debemos bajarlo por nosotros mismos desde su web oficial:

[http://nodejs.org/](http://nodejs.org/)

Una vez lo tengamos, podemos escribir en una consola de comandos:

```
npm i -g typescript
```

Y TS se instalará de forma automática. Desde la misma consola podemos comprobar que lo tenemos con el comando _tsc_ que nos mostrará la versión del compilador y la lista de parámetros que admite. El compilador se añade de forma automática a la variable PATH del sistema por lo que podemos invocarlo desde cualquier parte.

Si queremos instalar versiones posteriores a la oficiales y que todavía están en desarrollo y no cerradas:

```
npm i -g typescript@beta
npm i -g typescript@next
```

Para compilar TS manualmente lo normal sería escribir:

```
tsc -target ES5 --removeComments --declaration --out app.ts app.js
```

Tiene bastantes opciones que son [útiles conocer](../anexo_iv_tsconfigjson.md).