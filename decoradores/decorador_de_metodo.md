## Decorador de método {#decorador-de-m-todo}

Parámetros:

*   target : Object - El prototype de la clase.
*   propertyName : **string** | **symbol** - El nombre del atributo.
*   descriptor : TypedPropertyDescriptor – El descriptor del método.

Es posible modificar un método concreto que no sea el constructor:

**class** Persona{ @noWritable **public** caminar():**void**{ console.log("caminar"); }}**function** noWritable (target : Object, propertyKey: **string**,descriptor :TypedPropertyDescriptor<**any**>){ descriptor.writable = **false**; **return** descriptor}Persona**.**prototype.caminar = **function** (){}; // No tiene efecto

Con el decorador hemos marcado el método _caminar_ como no escribible, es decir, no es modificable una vez se ha declarado. Este decorador sirve no sólo para ese método, sino para todos los métodos de todas las clases, incluso estáticos:

**class** Persona{ @noWritable **public static** caminar():**void**{ console.log("caminar"); }}**function** noWritable (target : Object, propertyKey: **string**,descriptor :TypedPropertyDescriptor<**any**>){ descriptor.writable = **false**; **return** descriptor}Persona**.**caminar = **function** (){}; // No tiene efecto