## Constantes {#constantes}

En contraposición a las variables están las constantes, que como su nombre indica, no se les pueden modificar su valor una vez inicializadas.

Para crearlas se usa la palabra reservada **const**

**const** pi: **number** = 3.14; pi=3 // Error

Además su ámbito se comporta como una variable declarada con _let_ (ámbito de bloque).

**function** getPI(): **void** { **if**(){ **const** PI: **number** = 3.14; } **return** PI**;** // Error. PI no alcanzable.****}

Realmente esto es poco usual ya que normalmente las constantes se usan para determinar valores fijos útiles en toda la aplicación, por lo que no tiene mucho sentido que sea alcanzable desde un bloque de código en concreto.

Además las constantes [se pueden simular en algunas circunstancias](../clases/estaticos.md#757309351116418-_Constantes_mediante_estáticos).