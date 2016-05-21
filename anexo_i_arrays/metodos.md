## Métodos {#m-todos}

El array que usaremos para algunos ejemplos es el siguiente:

**var** numeros = [1,2,3];

### concat {#concat}

Combina dos o más arrays.

**var** numeros2 = [4, 5, 6];**var** numeros3 = numeros.concat(numeros2);// numeros3 es [1,2,3,4,5,6]

### every {#every}

Comprueba si todos los elementos del array satisfacen una función pasada como argumento.

Función como argumento: (value:T, index:number, array: T[]) => Boolean

**function** comprobarSiSon2(valor:**number**, index:**number**, array:**number**[]):**boolean**{ **var** test:**boolean** = **false**; **if** (valor == 2){ **** test = **true**; } **return** test;}numeros.every(comprobarSiSon2); // false

La función comprueba si todos los elementos del array son el número 2\. Como no es así, devuelve **false**.

### some {#some}

Comprueba si al menos uno de los elementos del array satisface una función pasada como argumento.

Función como argumento: (value:T, index:number, array: T[]) => **boolean**

**function** comprobarSiAlgunoEs2(valor:**number**, index:**number**, array:**number**[]):**boolean**{ **var** test:**boolean** = **false**; **if** (valor == 2){ **** test = **true**; } **return** test;}****numeros.some(comprobarSiAlgunoEs2); // true

La función comprueba si al menos uno de los elementos del array es el número 2\. Como uno lo es, devuelve **true**.

### filter {#filter}

Devuelve un array filtrando los elementos según una función pasada como argumento.

Función como argumento: (valor:T, index:number, array:T[]) => **boolean**

**function** filtrarSolo2(valor:**number**, index:**number**, array:**number**[]):**boolean**{ **var** filt:**boolean** = **false**; **if** (valor == 2){ **** filt = **true**; } **return** filt;}**var** arrayFiltrado = numeros.filter(filtrarSolo2); // arrayFiltrado es [2]

La función sólo da por bueno aquellos elementos que sean el número 2 descartando los que no lo sean.

### foreach {#foreach}

Recorre todos los elementos del array aplicándoles la función pasada como argumento

Función como argumento: (valor:number, index:number, array:number[]) => void

**function** recorrer(valor:**number**, index:**number**, array:**number**[]):**void**{ **** array[index] = valor + 1;}****array.forEach(recorrer);

La función suma 1 a todos los elementos del array. Si modificamos el parámetro _valor_, no surtiría efecto en el array pues los tipos primitivos se pasan por valor y no por referencia.

**function** recorrer(valor:**number**, index:**number**, array:**number**[]):**void**{ **** ++valor;}numeros.forEach(recorrer); // array es [1,2,3]

Pero si lo usáramos con objetos:

**var** array = [**new** Persona(18), **new** Persona(60)];

**function** cambiarEdad(valor:Persona, index:**number**, array:Persona[]):**void**{ **** valor.setEdad( valor.getEdad()+1 );}

numeros.forEach(cambiarEdad); /* array contiene 2 personas. Una con 19 años y otra con 61\. */

No sería necesario acceder al valor a través del array y su índice.

### indexOf {#indexof}

Recorre el array buscando el elemento pasado como argumento, devolviendo el índice de la primera ocurrencia. Devuelve -1 si no lo encuentra

**var** indice:**number** = numeros.indexOf(2); // 1

También se puede invocar el método con un argumento opcional que específica a partir de qué posición debe empezar a buscar.

**var** indice:**number** = numeros.indexOf (2, 2); // -1

### lastIndexOf {#lastindexof}

Recorre el array buscando el elemento pasado como argumento, devolviendo el índice de la última ocurrencia. Si no lo encuentra devuelve -1

**var** indice:**number** = numeros.indexOf (2); // 1

También se puede invocar el método con un argumento opcional que específica a partir de qué índice debe empezar a buscar.

**var** indice:**number** = numeros.indexOf (2, 2); // -1

### join {#join}

Devuelve el array como un **string** donde sus elementos están separados por un carácter pasado como argumento.

**var** arrayComoString:**string** = numeros.join("-"); // “1,2,3”

Hemos convertido el array en un **string** separado por guiones. Ejecuta el método _toString()_ de cada elemento del array.

### map {#map}

Recorre todos los elementos del array ejecutando el código de la función pasada como argumento a cada uno de ellos y devuelve un array con los cambios realizados sin modificar el array original.

**function** map(valor:**number**, index:**number**, array:**number**[]):**number**{ **return** ++valor;}**var** numeros2 = numeros.map(map);

El array _numeros_ sigue siendo [1,2,3] pero _numeros2_ es [2,3,4] puesto que hemos sumado uno a cada elemento.

### shift {#shift}

Elimina el primer elemento del array y lo devuelve

**var** primerElemento = numeros.shift();// primerElemento es 1

### pop {#pop}

Elimina el último elemento del array y lo devuelve

**var** ultimoElemento = numeros.pop();// ultimoElemento es 3

### push {#push}

Añade un nuevo elemento al final del array y devuelve el tamaño del array.

**var** nuevoTamano:**number** = numeros.push(8);// nuevoTamano es 4

### unshift {#unshift}

Inserta nuevos elemento al principio del array y devuelve el nuevo tamaño del array.

**var** nuevoTamano:**number** = numeros.unshift(8);//array es [8,1,2,3]

### reduce {#reduce}

Aplica una función simultáneamente a dos valores de un array (de izquierda a derecha)

Función como argumento: (valorPrevio:T, valorActual:T, índice:index, array:T[]) => T

**function** reduce(valorPrevio:**number**, valorActual:**number**, índice:**number**, array:**number**[]):**number**{ **return** valorPrevio + valorActual;}

**var** sumaArray:**number** = numeros.reduce(reduce);

De esta forma el valor previo es el primer elemento del array y el valor actual el segundo.

Primera iteración:

valorPrevio = 1, valorActual = 2\. Resultado: 3

Segunda iteración

valorPrevio: 3 (es el resultado de la iteración anterior), valor actual = 3\. Resultado: 6

Si se inserta un segundo argumento a _reduce_, ese argumento sería el _valorPrevio_ en la primera iteración y el _valorActual_ sería el primer elemento del array

**var** sumaArray:**number** = array.reduce(reduce,50);

Primera iteración:

valorPrevio = 50, valorActual = 1\. Resultado: 51

Segunda iteración

valorPrevio: 51 (es el resultado de la iteración anterior), valor actual = 2\. Resultado: 53

Tercera iteración

valorPrevio: 53 (es el resultado de la iteración anterior), valor actual = 3\. Resultado: 56

### reduceright {#reduceright}

Aplica una función simultáneamente a dos valores de un array (de derecha a izquierda) para reducirlo a un único valor.

Definición del método: (valorPrevio:T, valorActual:T, índice:number, array:T[]) => T

**function** reduceRight(valorPrevio:**number**, valorActual:**number**, índice:**number**, array:**number**[]):**number**{ **return** valorPrevio + valorActual;}

**var** sumaArray:**number** = numeros.reduceRight(reduceRight);

De esta forma el valor previo es el último elemento del array y el valor actual el penúltimo.

Primera iteración:

_valorPrevio_ = 3, _valorActual_ = 2\. Resultado: 3

Segunda iteración:

_valorPrevio_: 3 (es el resultado de la iteración anterior), _valor actual_ = 1\. Resultado: 6

Si se inserta un segundo argumento a _reduceRight_, ese argumento sería el _valorPrevio_ en la primera iteración y el _valorActual_ sería el último elemento del array

**var** sumaArray:**number** = numeros.reduceRight(reduceRight,50);

Primera iteración:

_valorPrevio_ = 50, _valorActual_ = 1\. Resultado: 51

Segunda iteración:

_valorPrevio_: 51 (es el resultado de la iteración anterior), _valor actual_ = 2\. Resultado: 53

Tercera iteración:

_valorPrevio_: 53 (es el resultado de la iteración anterior), _valor actual_ = 3\. Resultado: 56

### reverse {#reverse}

Devuelve el array original dándole la vuelta al orden de sus elementos.

**var** arrayReverse = numeros.reverse();// arrayReverse es [3,2,1];

### slice {#slice}

Devuelve un trozo del array estableciendo como argumentos los índices de principio y fin, ambos opcionales. Si no se establece ninguno, hace una copia completa del array.

**var** trozoArray = numeros.slice(1); // trozoArray es [2,3]

### sort {#sort}

Ordena un array mediante el criterio dado por una función. Si se omite la función serán ordenados de forma ascendente mediante caracteres ASCII.

**var** array = [4,7,1,3,9,6];array.sort();// array es [1,3,4,6,7,9]

Función como argumento: (a:T, b:T) => number

La función debe devolver un número:

0 = si los elementos son iguales 1 = si el primer elemento parametrizado es mayor al segundo-1 = si el primer elemento parametrizado es menor al segundo.

Con esto obtendríamos un orden ascendente. Si queremos un orden descendente sólo debemos cambiar el 1 por el -1, y el -1 por el.

**function** ordenarDescendente(n1: **number**, n2: **number**): **number** {

**var** orden: **number** = 0; **if** (n1 > n2) { **** orden = 1; } **else** **if** (n1 < n2) { **** orden = -1

} **return** orden;}numeros.sort(ordenarDescendente);// numeros es [9,7,6,4,3,1]

### splice {#splice}

Elimina elementos del array pudiendo sustituirlos por otros. Devuelve un array con los elementos eliminados.

**var** eliminados = numeros.splice(0,1); /* Empieza en el 0 y avanza uno. eliminados es [1] */

**var** eliminados = array.splice(0,1, 9); /* Empieza en el 0 y avanza uno e inserta 9 en su lugar. eliminados es [1] array es [9,2,3] */

### toString {#tostring}

Devuelve el Array en forma de cadena de caracteres separados por coma. Ejecuta el método _toString()_ de cada objeto si lo posee.

**class** Persona{ **constructor**(**private** nombre:**string**){} toString():**string**{ **return** **this**.nombre; }****}

**var** array:Array&lt;Persona&gt; = [**new** Persona("José"),**new** Persona("Carlos")];

array.toString() // "José, Carlos"

Si no poseyera el método toString(), devolvería _[object Object]_

**class** Persona{ **constructor**(**private** nombre:**string**){}****}

**var** array:Array&lt;Persona&gt; = [**new** Persona("José"),**new** Persona("Carlos")];

array.toString() // [object Object],[object Object]

Esto ocurre porque no sabría cómo convertir las instancias de esa clase en un _String_. Los tipos primitivos y objeto poseen el método _toString()_.