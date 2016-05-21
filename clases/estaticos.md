## Estáticos {#est-ticos}

Hasta ahora, todos los miembros que hemos creado son de instancia. Esto quiere decir que para cada instancia que creemos de una clase, serán independientes unas de otras.

**var** jose: Persona = **new** Persona ("José", "Lama");**var** carlos: Persona = **new** Persona ("Carlos", "Ponce");

Son dos instancias distintas de _Persona_ en la que sus datos no tienen relación entre sí. Si cambio el nombre de jose, _carlos_ seguirá igual que antes.

Existe un modificar llamado _static_ que es una palabra reservada del lenguaje. Con él conseguimos que un miembro sea accesible sin crear instancias de la misma.

**class** Persona {****/* (...) */ **public** **static** mostrarNombre():**void**{ alert("estático");}****}

Para acceder a los miembros estáticos se hace directamente con el nombre de la clase seguido del operador . (punto)

Persona.mostrarNombre();

Desde un método estático no se puede acceder a miembros no estáticos. Y tiene mucho sentido. Recordemos que los miembros no estáticos son aquéllos que pertenecen a la instancia. Si los estáticos pueden usarse sin crear ninguna instancia, ¿cómo van a poder usar miembros no estáticos?

Otra característica es que los miembros estáticos son transversales por lo que no cambian por cada instancia que creemos de la clase.