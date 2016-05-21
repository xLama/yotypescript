## Introducción {#introducci-n}

Los genéricos permiten parametrizar directamente las clases e interfaces. Son un paso más en la abstracción.

Hasta ahora habíamos definido clases no genéricas como _Concesionario_:

**class** Concesionario { }

Esta clase es capaz de englobar todos los concesionarios de las marcas de los coches. En ella iremos guardando una lista de los coches de cada concesionario.

¿Pero para qué marcas de automóviles diseñaremos la clase? Podemos hacerlas para todas con el uso de genéricos.

**class** Concesionario&lt;T&gt;{ **private** coches: Array&lt;T&gt;; **constructor**(){ **this**.coches = **new** Array&lt;T&gt;(); } **public** getCoche(indice: **number**): T { **return** **this**.coches[indice]; }****}

Para hacerlo se añade _&lt;T&gt;_ después del nombre de la clase. Realmente puedes escribir lo que quieras, no necesariamente una T. Ademas puedes parametrizar con una lista si te hace falta:

**class** Concesionario<T, V, K>{ }

Tenemos, por ejemplo, la clase _Seat_:

**class** Seat { }

Vamos a crear un concesionario de _Seat_:

**var** concesionarioSeat: Concesionario&lt;Seat&gt; = **new** Concesionario &lt;Seat&gt;();

Como puedes ver hemos usado la clase _Seat_ para parametrizar el genérico. De esta forma donde la clase es T, ahora es Seat.

Clase original:

**class** Concesionario&lt;T&gt;{ **private** coches: Array&lt;T&gt;;

**constructor**(){ **this**.coches = **new** Array&lt;T&gt;(); } **public** getCoche(indice: **number**): T { **return** **this**.coches[indice]; }****}

Clase al sustituir T por _Seat_:

**class** Concesionario&lt;Seat&gt;{ **private** coches: Array&lt;Seat&gt;;

**constructor**(){ **this**.coches = **new** Array&lt;Seat&gt;(); } **public** getCoche(indice: **number**): Seat { **return** **this**.coches[indice]; }****}

El compilador sustituye el parámetro genérico T por la clase que le hemos proporcionado, en este caso _Seat_. A este proceso se le llama instancia de tipo genérico.

Hemos conseguido que el _array_ de coches de la clase sea de coches de la marca _Seat_. Lo mismo si lo hacemos con otras marcas:

**class** Audi { }**class** Ferrari { }

**var** conceAudi: Concesionario&lt;Audi&gt; = **new** Concesionario &lt;Audi &gt;;

**var** conceFerrari: Concesionario&lt;Ferrari&gt; = **new** Concesionario < Ferrari >;