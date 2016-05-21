## Comparando clases {#comparando-clases}

El tipado estructural permite comparar clases o intercambiarlas aunque no tengan una relación de herencia entre ellas.

Los miembros estáticos y el constructor se ignoran a la hora de la comparación.

**class** Person { **static** EV: **number;** name: **string**;}**class** Dog { **** name: **string**;}

**var** person: Person;**var** dog: Dog;person = dog; // Correctodog = person; // Correcto

Si alguna de las clases tiene algún miembro privado o protegido la comparación difiere:

**class** Persona { **private** nombre: **string**;}

**class** Perro { **private** nombre: **string**;}

**var** persona: Persona;**var** perro: Perro;

persona = perro; // Incorrectoperro = persona; // Incorrecto

No son compatibles porque tienen un miembro privado. No importa si lo tienen los dos o sólo uno, lo que importa es que lo tienen. Para que dos clases sean iguales teniendo miembros privados éstos deben ser los mismos.

**class** Animal { **private** nombre: **string**;}

**class** Perro **extends** Animal { }

**var** animal: Animal;**var** perro: Perro;animal = perro; // Correctoperro = animal; // Correcto

Es correcto porque el miembro privado de _Perro_ (aunque parezca que no tenga porque recordemos que los miembros privados no se heredan) es el mismo que el de _Animal_ ya que hereda de él. Si a _Perro_ le añadimos un miembro privado con el mismo nombre que el de _Animal_, no compilaría pues se llama igual y no lo permite.

Si a _Perro_ le añadimos un miembro privado de distinto nombre:

**class** Animal { **private** nombre: **string**;}**class** Perro **extends** Animal { **private** raza: **string**;}

**var** animal: Animal;**var** perro: Perro;animal = perro; // Correctoperro = animal; // Incorrecto

A _animal_ se le puede asignar _perro_ porque _Perro_ tiene todo lo de _Animal_, aunque también posee miembros adicionales. Pero a _perro_ no se le puede asignar _animal_ porque a _Animal_ le falta el miembro privado adicional que posee _Perro_, _raza_. La mecánica es la misma que en el apartado de las interfaces y objetos literales: el objeto con más miembros puede ser asignado al objeto con menos pero no al revés. Si los miembros fueran _protected_, el comportamiento sería el mismo.