## Decorador de parámetro {#decorador-de-par-metro}

Parámetros:

*   target : Object - El prototype de la clase.
*   propertyName : **string** | **symbol** - El nombre del atributo.
*   parameterIndex : **number** – Número que determina la posición del parámetro.

Los parámetros también se pueden decorar:

**class** Persona{ **public** nombre: **string** **constructor**(@nombrenombre:**string**){ **this.**nombre = nombre **** } }**function** nombre (target : {}, propertyName: **string**,parameterIndex: **number**){ target[propertyName] = "Carlos";}**var** persona : Persona = **new** Persona();****persona.nombre; // Carlos