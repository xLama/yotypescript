## Introducción {#introducci-n}

Los generadores son funciones que pueden ser pausadas y continuadas. El contexto se guarda en cada pausa.

Tiene 3 aplicaciones principales aunque de momento, en TypeScript, sólo sirven para hacer iteradores.

Para declarar una función como generador se usa el operador * (asterisco):

**function*** generator() {}

Para hacer que se pause se utiliza la palabra reservada **yield.**

**function*** generator() { **yield**;}

Realmente ahora mismo esa función generadora no hace nada. Para ilustrar un ejemplo sencillo podemos hacer esto:

**function*** generator() { console.log("José") **yield;** console.log("Carlos")}

Para utilizar esta función se hace como cualquier otra con una salvedad: siempre devuelve un objeto con el método _next()_ que a su vez devuelve otro objeto:

**function*** generator() { console.log("José") **yield;** console.log("Carlos")}**var** gen = generator();gen.next(); // devuelve {value: undefined, done: false}"José"**gen.next();** // devuelve {value: undefined, done: true}"Carlos"

El objeto que devuelve _next()_ es el mismo que vimos en los iteradores.

En el ejemplo podemos ver que al ejecutar _next()_ se ha mostrado por consola el texto _José._ Como la siguiente sentencia de la función es **yield**, ésta se pausa. ¿Hasta cuándo? Pues hasta que se invoca de nuevo el método _next()._ En ese caso la función continúa hasta que termine o hasta que encuentre otra sentencia **yield** donde de nuevo se pausaría.

Si te fijas, cuando llega al final de la función, el valor de la propiedad _done_ del objeto devuelto por _next()_ es **true**.

Puedes crear funciones generadoras allí donde puedes crear funciones: declaraciones de funciones, expresiones de funciones, clases y funciones pertenecientes a objetos.

Para devolver valores en la propiedad _value_ se debe escribir el valor después de **yield**:

**function*** generator() { **yield** "José"; **yield** "Carlos";}**var** gen = generator();gen.next(); // {value: José, done: false}**gen.next();** // {value: Carlos, done: true}

Podemos hacer que la función devuelva un valor con **return** que se comportará de la misma forma que **yield** con la diferencia de que la función ya no puede ser continuada, es decir, **return** no la pausa.

**function*** generator() { **yield** "José"; **yield** "Carlos"; **return** "Lama"; **yield** "Ponce";}**var** gen = generator();gen.next(); // {value: José, done: false}**gen.next();** // {value: Carlos, done: false}**gen.next();** // {value: Lama, done: true}**gen.next();** // {value: undefined, done: true}

Las funciones generadoras son, a su vez, iterables. Se puede comprobar con el operador de expansión (…) o con la destructuración:

**function*** generator() { **yield** "José"; **yield** "Carlos";}**var** values : [] = ...generator();values // José, Carlos

Para demostrar las ventajas de los genereadores vamos a hacer el mismo iterador del tema Iteradores.

**function*** numIterator(num: **number**) { **var** n = parseInt(num.toString()).toString(); **var** length = n.length; **for** (**var** i = length - 1; i >= 0 ; --i){ **yield** n.charAt(i); } }**for** (**var** n **of** numIterator(2387)){ console.log(n) // 7, 8, 3, 2}

Es bastante más simple que el uso de iteradores. De esta forma tenemos la función generadora fuera del prototipo por lo que no podemos iterar directamente el número, ya sea con **for-of** o con el operador de expansión (…). Si queremos que también sea posible:

**function*** numIterator(num: **number**) { **var** n = parseInt(num.toString()).toString(); **var** length = n.length; **for** (**var** i = length - 1; i >= 0 ; --i){ **yield** n.charAt(i); } }Number.prototype[Symbol.iterator] = **function**() { **return** numIterator(**this**.valueOf());}**var** num = 2387;**for** (**var** n **of** num){ console.log(n) // 7, 8, 3, 2}

Hemos reutilizado la función generadora la cual se devuelve en el método _Symbol.iterator_ de _Number_. Esto es así porque cuando queremos iterar un número realmente lo que hace es ejecutar el método _Symbol.iterator._ Como este método devuelve la ejecución de una función generadora, y ésta se puede iterar, lo que hace es realmente es iterar el iterador, cosa que es posible como ya hemos visto.