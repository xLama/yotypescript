## Introducción {#introducci-n}

¿Qué son las interfaces? Son meros “contratos” que se hacen para una clase. Realmente las interfaces son listas de miembros que obligatoriamente debe tener la clase que implementa esa interfaz.

¿Para qué se utilzan las interfaces? Ciertamente es un debate abierto en el mundo del diseño de aplicaciones. Mi opinión se deberían usar para dar un comportamiento común a clases que no pueden tener (o no tiene sentido que tengan) relación por herencia.

Podemos tener la clase *Person* y la clase *Car*. Es evidente que encontrar una relación por herencia entre esas dos clases no sólo es complicado, sino que carece de sentido. Pero lo que sí es cierto es que pueden tener algún comportamiento común. Tantos las personas como los coches se desplazan. Ambos podrían tener un método llamado _desplazar()_ que haga moverse al objeto en cuestión.

Ahora imaginemos que estamos desarrollando un juego en el que hay partes móviles en el escenario como son personas y coches. En un momento dado necesitamos que un grupo de personas y de coches se muevan. Si ambas clases implementan la interfaz _Desplazable_, basta con recorrer todos los que queramos mover y ejecutar el método _desplazar()_ sin importar si es una persona o un coche, pues la implementación del método estará definida en cada clase de una forma particular.