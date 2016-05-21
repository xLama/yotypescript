## Las partes de una clase {#las-partes-de-una-clase}

Una clase tiene dos partes bien diferenciadas: una de instancia y otra de clase o estática.

Si creamos una clase:

**class** Persona { **public** **static** esperanza_vida: **number** = 80; **public** nombre:**string**; **constructor**(){}****}

Parte de instancia: el atributo _nombre._

Parte estática: el atributo _esperanza_vida_ y el constructor.

La parte estática se referencia con el nombre de la clase por ello no podemos asignar la parte estática a una variable del tipo _Persona_. Esto sólo sería correcto si la clase Persona no tuviera ningún miembro.

**var** estaticaPersona: Persona = Persona; // Error

Y no es posible porque _Persona_ es un tipo en sí mismo. El tipo de _Persona_ es otro distinto y no _Persona_. Sólo las intancias de _Persona_ son del tipo _Persona_. _Persona_ es del tipo _typeof Persona_:

**var** estaticaPersona: **typeof** Persona = Persona;

Observando el código JS que genera es más sencillo de entender.

**var** Persona = (**function** () { **function** Persona () {} **return** Persona;})();

**var** estaticaPersona = Persona;

Podemos ver que el tipo de _Persona_ es realmente una función. Esto se puede comprobar con el operador _typeof_

**typeof** Persona // function

Una vez que tenemos la referencia de la parte estática podemos acceder a su constructor y sus miembros estáticos:

**var** persona = **new** estaticaPersona(); /* La inferencia tipa con Persona */