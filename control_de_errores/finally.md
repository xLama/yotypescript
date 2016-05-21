## Finally {#finally}

Como hemos dicho, al lanzar un _Error_ con _throw_ se corta el flujo del programa y sigue por niveles superiores. Aunque podemos realizar una última acción antes de que eso ocurra con un bloque _finally_ que es un añadido al _try-catch_. Realmente el código encerrado en el _finally_ se ejecutará haya o no error.

**function** ejemploError(): **void** { **var** ejemplo = **null**; ejemplo.edad = 10;}

**try** { **** ejemploError();} **catch** (e) { **** console.error(e) /* Mostramos el error */ **throw** e; console.info("No se muestra");}

En el ejemplo no se llega a mostrar el mensaje “No se muestra” pues se ha lanzado el _Error_ con un _throw_. Pero si le añadimos el _finally_.

**function** ejemploError(): **void** { **var** ejemplo = **null**; ejemplo.edad = 10;}

**try** { **** ejemploError();} **catch** (e) { **** console.error(e) /* Mostramos el error */ **throw** e; console.info("No se muestra");}

**finally**{ **** /* Se ejecuta siempre*/ console.info("finally"); }