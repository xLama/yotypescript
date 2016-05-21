## Comprobar si una clase implementa una interfaz {#comprobar-si-una-clase-implementa-una-interfaz}

Como ya vimos, los operadores _instanceof_ y _typeof_ no funcionan con las interfaces entre otros motivos porque no existen en JS. Es un invento de TS que no produce código alguno al compilar por lo que todas las comprobaciones son en tiempo de compilación.

Eso nos plantea un problema a tener cuenta pues no podemos, a priori, comprobar si un objeto es del tipo de una interfaz concreta porque TypeScript tiene un sistema de tipado estructural.

La única forma de comprobar que una clase implementa una interfaz es comprobar si todos los miembros de una interfaz cualquiera están presentes en la clase en cuestión. Esto puede hacer que creamos que la clase implemente interfaces para las que no estaba preparada. Es así y no se puede cambiar tal y como está diseñado este lenguaje.