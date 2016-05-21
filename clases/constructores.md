## Constructores {#constructores}

¿Qué es el constructor? Realmente es un método de la clase que nos permite instanciarla. TS provee un constructor por defecto, sin parámetros.

**class** Person {}

Si queremos crear uno debemos usar la palabra reservada _constructor_.

**class** Person { **constructor**() { }****}

De esta forma hemos creado nuestro constructor para la clase _Persona_. Se comporta de la misma forma que cualquier función por lo que puede ser [sobrecargada](../funciones/sobrecarga.md), aceptar parámetros obligatorios, opcionales o con valor por defecto.

**class** Person { **constructor**(nombre: **string**, apellido1: **string**, apellido2?: **string**) { }****}

El constructor de la clase _Persona_ ahora tiene como parámetros obligatorios el nombre y el primer apellido. El segundo apellido es opcional.

**var** carlos: Persona = **new** Persona ("Carlos", "Lama");

En el cuerpo del constructor podemos usar estos valores como si de cualquier función se tratara.