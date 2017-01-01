## Métodos {#m-todos}

El array que usaremos para algunos ejemplos es el siguiente:

```ts
let nums = [1,2,3];
```

### concat {#concat}

Combina dos o más arrays.

```ts
let nums2 = [4, 5, 6];
let nums3 = nums.concat(nums2); // nums3 es [1,2,3,4,5,6]
```

### every {#every}

Comprueba si todos los elementos del array satisfacen una función pasada como argumento.

Función como argumento:

```ts
(value:T, index:number, array: T[]) => Boolean
```

```ts
function checkIfEveryAreTwo(val:number, index:number, array:number[]){ 
  return val === 2;
}
nums.every(checkIfEveryAreTwo); // false
```

La función comprueba si todos los elementos del array son el número 2. Como no es así, devuelve **false**.

### some {#some}

Comprueba si al menos uno de los elementos del array satisface una función pasada como argumento.

Función como argumento:

```ts
(value:T, index:number, array: T[]) => boolean
```

```ts
function checkIfSomeIsTwo(val:number, index:number, array:number[]){
  return val === 2;
}
nums.some(checkIfSomeIsTwo); // true
```

La función comprueba si al menos uno de los elementos del array es el número 2. Como uno lo es, devuelve **true**.

### filter {#filter}

Devuelve un array filtrando los elementos según una función pasada como argumento.

Función como argumento:

```ts
(valor:T, index:number, array:T[]) => boolean
```

```ts
function filterTwoOnly(val:number, index:number, array:number[]){ 
  return val === 2;
}
let filteredArray = nums.filter(filterTwoOnly); // filteredArray es [2]
```

La función sólo da por bueno aquellos elementos que sean el número 2 descartando los que no lo sean.

### foreach {#foreach}

Recorre todos los elementos del array aplicándoles la función pasada como argumento

Función como argumento: 

```ts
(valor:number, index:number, array:number[]) => void
```
```ts
function recorrer(valor: number, index: number, array: number[]) {
    array[index] = valor + 1;
}
array.forEach(recorrer);
```

La función suma 1 a todos los elementos del array. Si modificamos el parámetro _valor_, no surtiría efecto en el array pues los tipos primitivos se pasan por valor y no por referencia.

```ts
function recorrer(valor, index, array) { ++valor; }
nums.forEach(recorrer); // nums es [1,2,3]
```

Pero si lo usáramos con objetos:

```ts
let array = [new Person(18), new Person(60)];
array.forEach(
    (valor, index, array) => { 
        valor.setEdad(valor.getEdad() + 1); 
    }
); // array contiene 2 personas. Una con 19 años y otra con 61.
```

No sería necesario acceder al valor a través del array y su índice.

### indexOf {#indexof}

Recorre el array buscando el elemento pasado como argumento, devolviendo el índice de la primera ocurrencia. Devuelve -1 si no lo encuentra

```ts
let index = nums.indexOf(2); // 1
```

También se puede invocar el método con un argumento opcional que específica a partir de qué posición debe empezar a buscar.

```ts
let index = nums.indexOf(2, 2); // -1
```

### lastIndexOf {#lastindexof}

Recorre el array buscando el elemento pasado como argumento, devolviendo el índice de la última ocurrencia. Si no lo encuentra devuelve -1

```ts
let index = nums.lastIndexOf(2); // 1
```

También se puede invocar el método con un argumento opcional que específica a partir de qué índice debe empezar a buscar.

```ts
let index = nums.lastIndexOf(2, 2); // -1
```

### join {#join}

Devuelve el array como un string donde sus elementos están separados por un carácter pasado como argumento.

```ts
let arrayString = nums.join("-"); // "1,2,3"
```

Hemos convertido el array en un string separado por guiones. Ejecuta el método _toString()_ de cada elemento del array.

### map {#map}

Recorre todos los elementos del array ejecutando el código de la función pasada como argumento a cada uno de ellos y devuelve un array con los cambios realizados sin modificar el array original.

```ts
function map(valor, index, array) {
    return ++valor;
}
let numbers2 = nums.map(map);
```
El array _numbers_ sigue siendo \[1,2,3\] pero _numbers2_ es \[2,3,4\] puesto que hemos sumado uno a cada elemento.

### shift {#shift}

Elimina el primer elemento del array y lo devuelve

```ts
let firstElement = nums.shift(); // firstElement es 1
```

### pop {#pop}

Elimina el último elemento del array y lo devuelve
```ts
let lastElement = nums.pop(); // lastElement es 3
```

### push {#push}

Añade un nuevo elemento al final del array y devuelve el tamaño del array.
```ts
let newLenght = nums.push(8); // newLenght es 4
```

### unshift {#unshift}

Inserta nuevos elemento al principio del array y devuelve el nuevo tamaño del array.
```ts
let newLenght = nums.unshift(8); // array es [8,1,2,3]
```

### reduce {#reduce}

Aplica una función simultáneamente a dos valores de un array \(de izquierda a derecha\)

Función como argumento: \(valorPrevio:T, valorActual:T, índice:index, array:T\[\]\) =&gt; T

**function** reduce\(valorPrevio:**number**, valorActual:**number**, índice:**number**, array:**number**\[\]\):**number**{ **return** valorPrevio + valorActual;}

let sumaArray:**number** = numeros.reduce\(reduce\);

De esta forma el valor previo es el primer elemento del array y el valor actual el segundo.

Primera iteración:

valorPrevio = 1, valorActual = 2. Resultado: 3

Segunda iteración

valorPrevio: 3 \(es el resultado de la iteración anterior\), valor actual = 3. Resultado: 6

Si se inserta un segundo argumento a _reduce_, ese argumento sería el _valorPrevio_ en la primera iteración y el _valorActual_ sería el primer elemento del array

let sumaArray:**number** = array.reduce\(reduce,50\);

Primera iteración:

valorPrevio = 50, valorActual = 1. Resultado: 51

Segunda iteración

valorPrevio: 51 \(es el resultado de la iteración anterior\), valor actual = 2. Resultado: 53

Tercera iteración

valorPrevio: 53 \(es el resultado de la iteración anterior\), valor actual = 3. Resultado: 56

### reduceright {#reduceright}

Aplica una función simultáneamente a dos valores de un array \(de derecha a izquierda\) para reducirlo a un único valor.

Definición del método: \(valorPrevio:T, valorActual:T, índice:number, array:T\[\]\) =&gt; T

**function** reduceRight\(valorPrevio:**number**, valorActual:**number**, índice:**number**, array:**number**\[\]\):**number**{ **return** valorPrevio + valorActual;}

let sumaArray:**number** = numeros.reduceRight\(reduceRight\);

De esta forma el valor previo es el último elemento del array y el valor actual el penúltimo.

Primera iteración:

_valorPrevio_ = 3, _valorActual_ = 2. Resultado: 3

Segunda iteración:

_valorPrevio_: 3 \(es el resultado de la iteración anterior\), _valor actual_ = 1. Resultado: 6

Si se inserta un segundo argumento a _reduceRight_, ese argumento sería el _valorPrevio_ en la primera iteración y el _valorActual_ sería el último elemento del array

let sumaArray:**number** = numeros.reduceRight\(reduceRight,50\);

Primera iteración:

_valorPrevio_ = 50, _valorActual_ = 1. Resultado: 51

Segunda iteración:

_valorPrevio_: 51 \(es el resultado de la iteración anterior\), _valor actual_ = 2. Resultado: 53

Tercera iteración:

_valorPrevio_: 53 \(es el resultado de la iteración anterior\), _valor actual_ = 3. Resultado: 56

### reverse {#reverse}

Devuelve el array original dándole la vuelta al orden de sus elementos.

```ts
let arrayReverse = nums.reverse();// arrayReverse es [3,2,1];
```

### slice {#slice}

Devuelve un trozo del array estableciendo como argumentos los índices de principio y fin, ambos opcionales. Si no se establece ninguno, hace una copia completa del array.

```ts
let partialArray = nums.slice(1); // partialArray es [2,3]
```

### sort {#sort}

Ordena un array mediante el criterio dado por una función. Si se omite la función serán ordenados de forma ascendente mediante caracteres ASCII.

let array = \[4,7,1,3,9,6\];array.sort\(\);// array es \[1,3,4,6,7,9\]

Función como argumento: \(a:T, b:T\) =&gt; number

La función debe devolver un número:

0 = si los elementos son iguales 1 = si el primer elemento parametrizado es mayor al segundo-1 = si el primer elemento parametrizado es menor al segundo.

Con esto obtendríamos un orden ascendente. Si queremos un orden descendente sólo debemos cambiar el 1 por el -1, y el -1 por el.

**function** ordenarDescendente\(n1: **number**, n2: **number**\): **number** {

let orden: **number** = 0; **if** \(n1 &gt; n2\) { **\*\* orden = 1; } **else** **if** \(n1 &lt; n2\) { \*\*** orden = -1

} **return** orden;}numeros.sort\(ordenarDescendente\);// numeros es \[9,7,6,4,3,1\]

### splice {#splice}

Elimina elementos del array pudiendo sustituirlos por otros. Devuelve un array con los elementos eliminados.

```ts
let remove = nums.splice(0, 1); // Empieza en el 0 y avanza uno. remove es [1]
```


### toString {#tostring}

Devuelve el Array en forma de cadena de caracteres separados por coma. Ejecuta el método _toString()_ de cada objeto si lo posee.

```ts
class Person {
    constructor(private nombre: string) { }
    toString() { return this.nombre; }
}

let array = [new Person("José"), new Person("Carlos")];
array.toString\(\) // "José, Carlos"
```


Si no poseyera el método toString(), devolvería _[object Object]_

```ts
class Person {
    constructor(private nombre: string) { }
}

let array = [new Person("José"), new Person("Carlos")];
array.toString() // [object Object],[object Object]
```

Esto ocurre porque no sabría cómo convertir las instancias de esa clase en un _String_. Los tipos primitivos y objeto poseen el método _toString()_.

