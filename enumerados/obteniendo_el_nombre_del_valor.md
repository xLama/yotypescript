## Obteniendo el nombre del valor {#obteniendo-el-nombre-del-valor}

Con nuestro **enum** de ejemplo:

**enum** Animal { Perro, Gato, Conejo }

Podemos obtener el nombre del animal como **string** si conocemos su número.

**var** animal: **string** = Animal[1]; // Gato

Los enumerados resultan muy útiles para limitar los valores que podemos usar como, por ejemplo, si estamos desarrollando un juego 2D, el personaje sólo podrá ir arriba, abajo, izquierda, derecha.

**enum** Direcciones { Izquierda, Derecha, Arriba, Abajo };

De esta forma, cuando queramos moverlo o comprobar hacia dónde va, sabemos que sólo tiene esas 4 posibilidades y no aceptaremos una que no esté entre ellas.

Pueden usarse para tipar los parámetros de una función.

**enum** Animal { Perro, Gato, Conejo }**function** mostrarAnimal(animal:Animal):**void**{ **** console.log(Animal[animal]);}****mostrarAnimal(Animal.Perro);