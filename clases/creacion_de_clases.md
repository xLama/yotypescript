## Creación de clases {#creaci-n-de-clases}

### Declaración {#declaraci-n}

Es la forma clásica de creación de clases y la más extendida en los lenguajes orientados a objetos.

Se usa la palabra reservada _class_.

**class** Person { }

La convención de nombre para las clases es la primera letra de cada palabra es en mayúsculas. Es lo que se conoce como _lowerCamelCase_

Más información: [http://es.wikipedia.org/wiki/CamelCase](http://es.wikipedia.org/wiki/CamelCase)

Al crear nuestra propia clase (o tipo, si así se entiende mejor) podemos tipar una variable de la misma forma que haríamos con los primitivos y objeto.

**var** carlos: Person;

Con esto conseguimos que la variable de nombre _carlos_ sea del tipo _Person_.

### Expresión {#expresi-n}

ES6 introduce una sintaxis para crear clases, similar a como ya existe en las funciones. Se trata de las clases expresiones de clases. En ella se puede asignar una clase a una variable:

**var** Person **= class** { }

Pero hay una gran diferencia. No podemos usarla para tipar. No podemos hacer esto:

**var** carlos: Person;

A su vez podemos crear una clase mediante una expresión y asignándole un nombre:

**var** Person **= class** Person{ }

Pero el nombre de la clase sólo estaría disponible dentro de la propia clase y no fuera.

**var** Person **= class** Person{ /* Aquí sí podemos usar Person */} **var** carlos: Person; // Error

Esto permite crear clases anónimas de tal forma que podemos crearlas en el momento de usarlas, tal como ocurre con las funciones:

**function** foo ( classy : any ){} foo (**class** Person **{}**)