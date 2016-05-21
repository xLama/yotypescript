## Lanzando errores manualmente {#lanzando-errores-manualmente}

Podemos crear instancias de alguna clase de _Error_ y lanzarlos para mejorar la robustez de nuestro código.

Imagina que estamos creando un índice en el que el número no puede ser menor de 0.

**function** getVal(index: **number**): **string** { **if** (index < 0) { **throw** **new** RangeError("El íncide no puede ser menor de 0");} **** // (...) **return**;}

Como ves, hemos lanzado nuestro propia _RangeError_ para informar de que el índice no puede ser menor de 0.Es decisión del programador capturar o no el error mediante _try-catch_ y tratarlo de forma adecuada.