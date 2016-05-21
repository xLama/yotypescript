## Async y await. {#async-y-await}

Son dos las palabras reservadas para usarlas: async y await. Para declarar una función como asíncrona se debe anteponer la palabra a function.

**async function** asyncFunction{}

¿Qué conseguimos con esto? Lo que conseguimos es que lo devuelto por la función se envuelva en un Promise de forma automática y transparente para el desarrollador. Pero hay que tener claro que lo que devuelve en realidad no es un objeto Promise, sino el valor en sí.

**async function** asyncFunction{ **return** 1}

Pero la verdadera potencia no radica ahí, sino en el await. Await para la ejecución de la función hasta que se resuelva la operación. Para usar await la función debe devolver un Promise, ya sea de forma explícita o porque esa misma función también sea async:

**async function** otherAsyncFunction(){ **return** [0,1,2]; // 3}**async function** asyncFunction(){ **var** results = **await** otherAsyncFunction();// 2 **var** n = 1; // 5}asyncFunction(); // 1**var** name = "Lama"; // 4

Ejecutamos asyncFunction. Al llegar a la primera línea, se encuentra con un await, lo que hace ejecutar la función otherAsyncFunction() y para el flujo de esa función hasta que se resuelva, devolviendo el control de la ejecución a la siguiente línea posterior a la invocación de asyncFunction(). El ejemplo es muy sencillo pero sirve para esquematizar lo que ocurre. Los números reflejan el orden de ejecución en un caso normal, puesto que no sabemos cuánto va a tardar en devolver una respuesta otherAsyncFunction(). Como se ha sido antes, al acabar la ejecución de otherAsyncFunction(), la variable results no será un Promise, sino el array [0,1,2].

Para detectar si algo ha ido mal, se debe encerrar el código en un bloque try-catch.

**async function** otherAsyncFunction(){ **return** [0,1,2]; }**async function** asyncFunction(){ **try**{ **await** otherAsyncFunction(); **var** n = 1; **}** **catch (error){** // Algo ha ido mal **}**}asyncFunction(); **var** name = "Lama";

Es muy útil para las llamadas a servicios externos que no sabemos cuándo deolverán una respuesta:

**async function** callService(){ **try**{ **var** results = **await** externalService.request(); **catch (error){** // Algo ha ido mal **}** // Hacemos algo con results si ha ido bien}

La forma de hacerlo con callbacks sería así:

**function** callService(){ **var** results;externalService.request(**function** (done){ results = done; }, **function** (fail){ // Algo ha ido mal });}

Como vemos, con las funciones asíncronas el código queda mucho más limpio. Cuanto más se compliquen, más notoria será la limpieza.