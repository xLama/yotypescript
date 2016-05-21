## Sobrecarga {#sobrecarga}

La sobrecarga de funciones consiste en declarar dos o más funciones con el mismo nombre pero con distinto número de parámetros. En TS no existe la sobrecarga de funciones como tal.

No podemos hacer esto:

**function** sobreCarga(x: **number**): **number** { **return** x; }**function** sobreCarga(x: **number**, z:**number**): **number** { **return** x * z; }

Pero lo que sí existe es una misma implementación para varias declaraciones de una función con el mismo nombre si tenemos una definición que englobe a todas las demás.

**function** sobreC(x: **number**): **numberfunction** sobreC(x: **number**, z:**number**): **numberfunction** sobreC(x: **number**, z?: **number**): **number** { **return** x;}

El gran inconveniente es que tenemos que controlar los valores en el cuerpo de la función. No podemos operar con _z_ si no sabemos si realmente tiene algún valor distinto a _undefined_ o _null_.

Esta función devuelve el valor _x_ si sólo se introduce _x_. Si también se introduce _z_, devolverá la suma de ambos.

**function** sumar(x: **number**): **numberfunction** sumar(x: **number**, z:**number**): **numberfunction** sumar(x: **number**, z?: **number**): **number** { **var** total: **number** = x; **if** (z !== undefined) {**** total = x + z;} **return** total;}

Como _z_ es el parámetro que puede estar vacío y darnos problemas, tenemos que comprobar que realmente contiene algún valor antes de operar. En este caso vemos si y es distinto de _undefined_.