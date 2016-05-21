## Inferencia de tipos {#inferencia-de-tipos}

Inferir, según la RAE se define como: “_Sacar una consecuencia o deducir algo de otra cosa_”.

En este sentido se refiere a la capacidad de deducción del compilador a la hora de asignar tipos de forma automática a variables no tipadas explícitamente, según ciertas circunstancias.

### Inferencia básica {#inferencia-b-sica}

Es la que ocurre cuando “se nos olvida” tipar una variable que hemos inicializado.

**var** str = "inferencia";

El compilador tipa de forma automática la variable cadena porque sabe que su contenido es un **string**.

Si inicializamos de forma literal, la inferencia del tipo será de primitivos. Si inicializamos con el constructor de las clases de objeto, la inferencia será del tipo de la objeto.

**var** x = 3; // Tipado con number**var** y = **new** Number(3); // Tipado con Number

### Expresiones tipadas por el contexto {#expresiones-tipadas-por-el-contexto}

El tipado contextual es una característica de TS que nos ahorra cierto trabajo.

Tenemos esta

función

:

**var** func: (x: **number**) => **string** = (x: **number**) => "func";

En ella hemos especificado todos los tipos tanto a la hora de declararla como de inicializarla. ¿Qué parte del trabajo puede hacer TS por nosotros?

**var** func: (x: **number**) => **string** = (x) => "func";

Podemos obviar el tipo del parámetro en la inicilización pues al estar en el tipo de la declaración, sabe que realmente es un **number**.

Si lo hacemos al revés, es decir, no especificamos el tipo en el parámetro de la declaración pero sí en el de la incialización, el tipo del parámetro en la declaraciçon será **any**:

**var** func: (x) => **string** = (x: **number**) => "func";

Pero si borramos por completo el tipo de la declaración, va tiparlo por inferencia de forma correcta. Aquí vemos como también tipa por inferencia el retorno de la función:

**var** func = (x: **number**) => "func"; // tipado con : (x: number) => string

Si no se tipa ni en la declaración ni en la inicialización, TS no tiene más remedio que tipar el parámetro con **any**:

**var** func = (x) => "func"; // x lo tipa con any. El retorno sí es string