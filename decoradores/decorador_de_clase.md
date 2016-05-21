## Decorador de clase {#decorador-de-clase}

Como su nombre indica decora la declaración de una clase. Esto es importante porque no decora las instancias, sino la clase en sí y en el momento de ser declarada.

Parámetros:

*   target : Function - La clase.

@decorador**class** Persona{}

**function** decorador(target : Function){ target["estoyDecorado"] = **true**;}Persona["estoyDecorado"]; //true

En el decorador podemos modificar la clase añadiendo o elminando miembros. En el ejemplo hemos añadido una propiedad llamada _estoyDecorado_ como miembro estático. Si quisiéramos añadirlo como membro de instancia sólo habría que usar _prototype_:

@decorador**class** Persona{}**function** decorador(target : Function){ target.prototype["estoyDecorado"] = **true**;}**var** persona: Persona **= new** Persona();****persona["estoyDecorado"] //true