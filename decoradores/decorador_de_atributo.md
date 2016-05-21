## Decorador de atributo {#decorador-de-atributo}

Parámetros:

*   target : Object - El prototype de la clase.
*   propertyName : **string** | **symbol** - El nombre del atributo.

Los atributos de una clase también pueden decorarse aunque con limitaciones. No se les puede cambiar la visibilidad (público, protegido o privado) pero sí prácticamente todo lo demás. Es muy útil para la inyección de dependencias.

**class** Persona{ @nombre **public** nombre:**string**}**function** nombre (target : {}, propertyName: **string**){ target[propertyName] = "Carlos";}**var** persona : Persona = **new** Persona();****persona.nombre; // Carlos

Se está inyectando el nombre _Carlos_ en todas las instancias de _Persona_.