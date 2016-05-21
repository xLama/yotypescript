## Selectivas {#selectivas}

### if {#if}

Sirve para tomar decisiones bajo alguna condición. Aquí es donde resultan imprescindibles los [operadores lógicos](../operadores/operadores_binarios.md#operadores-l-gicos).

**if** **(/*condición*/)** { **// Código** }**var** x = 5;**if** (x == 5) { /* Se ejecuta si x es igual a 5 */ **// Código**}

Se puede usar el bloque _else_ que engloba todo lo que no lo hace la condición original.

**if**(x == 5) {**** /* Se ejecuta si x es igual a 5 */}**else**{ **** /* Si no es igual a 5 entra aquí */}

Además se puede usar el bloque _else if_ para determinar más casos.

**if**(x == 5){ // Se ejecuta si x es igual a 5 // Código}**else** **if** (x == 6) { // Si es igual a 6 } **else** { // Si no es igual ni a 5 ni a 6}

En la condición puedes usar todos los operadores de comparación que quieras junto con operadores lógicos.

**var** x: **number** = 5;**var** y: **number** = 10;**if** (x == 5 && y == 10) { /* Se ejecuta si x es igual a 5 y, además, y es igual a 10 */}

### switch {#switch}

Es una estructura de elección que puede sustituirse por _if-else_ pero que en ciertas circustancias resulta más práctico.

**var** x: **number** = 1;**switch** (x) { **case** 0: // Hacer algo si x vale 0 **break**; **case** 2: // Hacer algo si x vale 2 **break**; **default**: /* Hacer algo en el caso de que no sea ninguno de los anteriores */ **break**;}

Es importante el _break_ porque sin él también se ejecutaría el siguiente caso aunque no lo cumpliera.

También puedes agrupar casos para un mismo código.

**var** x: **number** = 1; **switch** (x) { **case** 0: **case** 1: **case** 2: // Hacer algo si x vale 0, 1 ó 2 **break**; **default**: /* Hacer algo en el caso de que no sea ninguno de los anteriores */ **break**;}