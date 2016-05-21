## Polimorfismo {#polimorfismo}

Com su nombre indica (muchas formas) es la cualidad que tiene un objeto de un tipo de comportarse como de otro tipo en un momento determinado.

Recordando el ejemplo:

Alumno Persona Mamifero SerVivo

Podemos hacer esto:

**var** ser: SerVivo = **new** Alumno();

¿Por qué? Porque Alumno es-un SerVivo

Si en una función aceptamos como parámetro un SerVivo:

**function** ejemplo(ser: SerVivo): **void** { }

¿Qué pasaría si la invocamos pasándole como argumento un _Alumno_?

ejemplo(**new** Alumno());

¿Sería correcto? Sí. Pues un _Alumno_ es un _SerVivo_. No hay riesgo de ningún tipo pues _Alumno_ ha heredado de _SerVivo_ todos los miembros públicos por lo que estamos seguros que de los métodos se van a ejecutar sin problemas.