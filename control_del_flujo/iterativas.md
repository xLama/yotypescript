## Iterativas {#iterativas}

Un bucle es una repetición limitada o no (los bucles infinitos no son buena idea) de un bloque de código. Si, por ejemplo, queremos mostrar por pantalla los 100 primeros números y no usáramos bucles, tendríamos que escribirlos todos a mano. Absurdo, ¿no crees?

### while {#while}

El bucle _while_ se ejecuta mientras la condición sea **true**.

**var** x: **number** = 0;**while** (x < 10) { **** x++; // x va incrementándose en 1 en cada iteración}

Cuando llegue a 10, se evaluará como **false** y el bucle dejará de ejecutarse.

### do-while {#do-while}

Es similar a _while_ pero mientras el while no se ejecuta si no se cumple la condición, el _do while_ se itera al menos una vez, y las siguientes si cumple la condición.

**var** x: **number** = 0; **do** { **** x++;// Se ejecuta una vez al menos } **while** (x < 10);

Se ejecutará mientras _x_ sea mejor de 10\. En cuanto sea 10, se saldrá del bucle.

### for {#for}

Es un bucle un tanto distinto a _while_ pues en su definición se declara una variable numérica que sirve de índice.

**for** (declaración; condición; actualización) { **** // Código}

**var** nombres: Array<**string**> = ["José", "Carlos", "Lama"]

**for** (**var** i: **number** = 0; i < nombres.length - 1; i++) { console.log(nombres[i]);}

Se va iterando sobre el array de forma que el índice _i_ va aumentando en uno cada iteración y así vamos obteniendo los valores de las distintas posiciones del array.

No está restringido a una sola declaración, condición y actualización. Ni siquiera esta última debe ser una sucesión creciente.

Podemos declarar más de una variable y hacer que la condición sea más compleja con operadores lógicos. Además en la actualización podemos usar cualquier operador matemático. La única restricción es que el índice ha de ser numérico entero.

### for-in {#for-in}

Es similar al _for_ pero no se declara un índice numérico y recorre la estructura de principio a fin, sin condiciones.

**var** nombres: Array<**string**> = ["Carlos", "José", "Lama"];

**for** (**var** indice **in** nombres) { console.log(nombres[indice]);}

Va volcando el índice de _nombres_ de la variable temporal _indice_. La ventaja es que no importa de qué tipo sea el índice: numérico, cadena de caracteres, etc.

Existe un problema al recorrer _arrays_ de esta forma. Debido a que recorre todas las propiedades de _array_, es posible que incluso itere por las intrínsceas (como length) lo que daría lugar a comportanmientos inesperados. Para ello debe debe usarte una precondición dentro del bucle que nos asegure de que exista:

**var** nombres: Array<**string**> = ["Carlos", "José", "Lama"];

**for** (**var** indice **in** nombres) { **if** ( nombres.hasOwnProperty(indice) ){ console.log(nombres[indice]); } }

Para evitarnos problemas, lo mejor sería usar el _for_ común.

### for-of {#for-of}

Esta forma de _for_ es casi idéntica al _for-in,_ con la salvedad de que en cada iteracción lo que se vuelca en la variable temporal es el valor de la posición y no el índice.

**var** name: Array<**string**> = ["Carlos", "José", "Lama"];

**for** (**var** name **of** names) { console.log(name);}

Si compilamos para ES6, es necesario que la estructura que estemos iterando implemente un método _[Symbol.iterator]()_