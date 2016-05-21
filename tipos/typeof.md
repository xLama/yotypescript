## typeof {#typeof}

Este operador es muy útil pues nos informa del tipo de dato de una variable. El resultado que nos devuelve es un **string**_._

**var** cadena: **string** = **typeof** "probando typeof"; // “string”

Hay que tener cuidado con esto:

**var** cadena: **string** = **typeof** **new** String("probando typeof"); // “object”

Si hacemos _typeof cadena_, el resultado será “object”. ¿Por qué? Pues porque realmente es un _object_ ya que _String_ es una clase de objeto. La única forma de poder saber el tipo de dato específico es inicializando las variables literalmente. No importa si tipas la variable con **string** o _String_, lo importante es lo que le asignes.

Devolverá **string**:

**var** cadena1: **string** = **typeof** "probando typeof";**var** cadena2: **string** = **typeof** "probando typeof";

Devolverá _object_

**var** cadena: **string** = **typeof** **new** String("probando typeof");

Esto es aplicable no sólo a _String_, sino a todos los demás como _Number_, _Boolean_…

Con este operador también podemos tipar una variable con el tipo de otra. Es lo que se conoce en TS como tipos consulta.

**var** x: **number** = 5;**var** z: **typeof** x = 2;

Incluso lo podemos hacer por inferencia.

**var** x = 5;**var** z: **typeof** x = 2;

Aunque no hayamos especificado el tipo de _x_, el intérprete sabe que es del tipo **number** por lo que podemos hacer que _z_ sea de ese tipo.