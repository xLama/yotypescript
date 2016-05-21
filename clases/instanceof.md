## instanceOf {#instanceof}

Es un operador binario muy útil para el manejo de clases. Comprueba si un objeto es de un tipo determinado. Sólo funciona con los tipos referencia, es decir, no funciona con los primitivos.

**var** x: Number = **new** Number(5);x **instanceof** Number; // true

No funciona con los tipos primitivos, sólo con los objeto. No podemos hacer esto:

**var** y: **number** = 5;y **instanceof** **number**; // No compila

Además, esto dará false:

**var** num: Number = 5num **instanceof** Number // false

El resultado de los tipos objeto inicializados de forma literal será **false**. Para que sea **true** deben haber sido inicializados con su constructor como se muestra en el primer ejemplo.

También pueden ser usados para nuestras propias clases.

**class** A{}**class** B **extends** A{}**var** a:A = **new** A();**var** b:B = **new** B();

a **instanceof** A // truea **instanceof** B // falseb **instanceof** A // true

El último ejemplo es **true** porque al ser B una subclase de A, las instancias de _B_ son a la vez del tipo _A_ y _B_.

No sirve para interfaces. Es algo que sí funciona en otros lenguajes pero en TS no.