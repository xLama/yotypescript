## Introducción {#introducci-n}

Los enumerados (o _enums_) son un tipo derivado de **number** que relacionan un nombre literal con un número determinado. Es una forma más amigable que el uso de números en determinados casos.

Si queremos manejar una lista de animales podríamos asociar cada uno con un número y usar el mismo para referenciarlos. O bien podríamos guardar el nombre del animal como **string**. Pero eso no nos permite que la lista sea inamovible ni limitada y, además, es poco manejable. Si declaramos un **enum** con los nombres y los mismos se asocian de forma automática a un número, estamos consiguiendo lo que queremos.

**enum** Animal { Perro, Gato, Conejo }

La mecánica es la misma que la de los [estáticos](../clases/estaticos.md). Para acceder a los valores del **enum** se escribe el nombre del **enum** seguido de un “.” (punto) y después el nombre de uno de los contenidos.

**var** perro:Animal = Animal.Perro;

Realmente los _enums_ son números. En el **enum** de ejemplo, _Animal_, el primero, _Perro_, empieza por el 0 siguiendo una sucesión. Si queremos que ésta cambie debemos asignárselo de forma explícita:

**enum** Animal { Perro = 10, Gato, Conejo } // Perro es el 10, Gato el 11…

**enum** Animal { Perro, Gato = 10, Conejo } // Perro es el 0, Gato el 11 y Conejo el 12

Cuidado con hacer esto:

**enum** Animal { Perro = 10, Gato = 9, Conejo } // Perro es el 10, Gato el 9 y Conejo el 10

No falla en la compilación pero es un error pues podríamos confundir _Perro_ con _Conejo_ ya que internamente se manejan con el mismo número.