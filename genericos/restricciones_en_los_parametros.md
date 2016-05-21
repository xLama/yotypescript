## Restricciones en los parámetros {#restricciones-en-los-par-metros}

Vamos un paso más allá y vamos a restringir qué clases pueden ser parámetros de _Concesionario_.

La restricción del tipo de clase se hace por herencia.

**class** Concesionario<T **extends** Automovil>{**** //(...)}

De esta forma sólo aceptamos como parámetros para la clase _Concesionario_ una clase que herede de _Automovil_ porque en nuestros concesionarios no se venden otra cosa.

**class** Avion { }**class** Automovil { }**class** F18 **extends** Avion { }**var** conce: Concesionario<F18> = **new** Concesionario < F18>; // Error

Es erróneo porque _F18_ no hereda de _Automóvil_ por lo que no cumple con la restricción.

Podemos llevarlo más allá y establecer una restricción con los propios tipos de los parámetros. Sólo tiene sentido si tenemos, como mínimo, dos genéricos:

REVISAR

**class** MergeConcesionarios<T **extends** U, U **extends** Concesionario>{**** //(...)}