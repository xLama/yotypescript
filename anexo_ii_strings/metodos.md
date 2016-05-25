## Métodos {#m-todos}

El **string** que usaremos para algunos ejemplos es el siguiente:

```ts
let name = "José Carlos";
```

### charAt {#charat}

Devuelve el carácter de la posición numérica pasada como argumento.

```ts
let caracter = nombre.charAt(3);//caracter3 es "é"```
```

### charCodeAt {#charcodeat}

Devuelve el códido ASCII del carácter de la posición numérica pasada como argumento.

```ts
let caracter3 = nombre.charCodeAt(3);//caracter3 es 233
```

### concat {#concat}

Devuelve un **string** que es la concatenación de dos o más.

```ts
let apellidos = "Lama Ponce";
let nombreCompleto = nombre.concat(apellidos);// nombreCompleto es "José Carlos Lama Ponce"
```

### indexOf {#indexof}

Devuelve la posición de la primera ocurrencia del **string** suministrado como argumento. Devuelve -1 si no lo encuentra.
```ts
let posicionPrimeraS = nombre.indexOf("s");// posicionPrimeraS es 2
```

Si se le proporciona una cadena y no un solo carácter, buscará la coincidencia de la cadena al completo pero devolverá la posición del primer carácter

```ts
let posicionCar = nombre.indexOf ("Car");//posicionCar es 5
```

### lastIndexOf {#lastindexof}

Devuelve la posición de la última ocurrencia del **string** suministrado como argumento. Devuelve -1 si no lo encuentra.

```ts
let posicionUltimaS:**number** = nombre.lastIndexOf("s");// posicionUltimaS es 10
```

Si se le proporciona una cadena y no un solo carácter, buscará la coincidencia de la cadena al completo pero devolverá la posición del primer carácter.

```ts
let posicionCar = nombre.indexOf ("Car");//posicionCar es 5
```

### match {#match}

Busca en una cadena una expresión regular u otra cadena. Si la encuentra devuelve las ocurrencias en forma de array.

```ts
let resultado = nombre.match(/o/g); /* Devuelve un array de 2 posiciones */
let resultado = nombre.match("o"); /* Devuelve un array de 1 posicion */
```

Si la búsqueda se hace con otra cadena, sólo devuelve la primera ocurrencia encontrada empezando por la izquierda.

### replace {#replace}

Encuentra coincidencias en la cadena a partir de una expresión regular u otra cadena para sustituirlas las ocurrencias por una nueva cadena

```ts
let nombreReal = nombre.replace("e","é")); // José Carlos

let nombre: = "J o se C ar l o s";
let nombreReal = nombre.replace(/\s/g,"")); // José Carlos. Elimina los espacios
```

### search {#search}

Busca en la cadena la cadena o expresión rgular introducida como argumento y devuelve el índide de la primera ocurrencia de izquierda de derecha. Si no la cuentra devuelve null.

```ts
let letraJ = nombre.search("J") // 1
```

### slice {#slice}

Devuelve un trozo del string proporcionando los índices como argumento. El primero determina donde empieza. El segundo donde acaba sin incluirlo.

```ts
let primeroNombre = nombre.slice(0,2);// primeroNombre es "Jo"
```

Puede empezar por el final si se proporciona el segundo argumento negativo.

```ts
let primeroNombre = nombre.slice(0,-2);// primeroNombre es "José Carl"
```

Si el índice de comienzo es negativo, comienza por el índice calculado de la longitud de la cadena + índice de comienzo

```ts
let primeroNombre = nombre.slice(-5,7);// primeroNombre es “a”/* El índice de comienzo es -5\. Sumamos la longitud que es 11 y resultaría 6\. Es equivalente a nombre.slice(6,7); */

### split {#split}

Convierte el string en un array de strings proporcionando como paráemtro el carácter separador.

```ts
let nombresSeparados = nombre.split(" ");// nombresSeparados es ["José","Carlos”]
```

Hemos “roto” el string por el espacio en blanco.

### substr {#substr}

Devuelve un trozo del string proporcionando como argumento el íncide de incio y la longitud. Si la longitud es 0 o negativa, se devuelve una cadena vacía. Si no se proporciona, avanza hacia el final de la cadena.

```ts
let primeroNombre = nombre.slice(0,-2);// primeroNombre es "Jo"
```

### substring {#substring}

Devuelve un trozo del string proporcionando los índices como argumento. El primero determina donde empieza. El segundo donde acaba sin incluirlo. Si el índice de terminación es menor al de comienzo, se intercambian.

nombre.slice(0,4) es quivalente a nombre.slice(4,0);

```ts
let primeroNombre = nombre.slice(0,4);// primeroNombre es “José ”

### toLowerCase {#tolowercase}

Convierte todos los caracteres en minúsculas.

```ts
let nombreMinusculas = nombre.toLowerCase();// nombreMinusculas es "josé carlos"
```

### toUpperCase {#touppercase}

Convierte todos los caracteres en mayúsculas

```ts
let nombreMayusculas = nombre.toUpperCase();// nombreMayusculas es "JOSÉ CARLOS"
```

### trim {#trim}

Elimina los espacios en blanco del principio y final del string.

```ts
let nombre = " José Carlos ";
let nombreSinEspacios= nombre.trim();// nombreSinEspacios es "José Carlos"
```

