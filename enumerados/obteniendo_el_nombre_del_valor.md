## Obteniendo el nombre del valor {#obteniendo-el-nombre-del-valor}

Con nuestro **enum** de ejemplo:

```ts
enum Animal { Dog, Cat, Rabbit }
```

Podemos obtener el nombre del animal como **string** si conocemos su número.

```ts
let animal = Animal[1]; // Cat
```

Los enumerados resultan muy útiles para limitar los valores que podemos usar como, por ejemplo, si estamos desarrollando un juego 2D, el personaje sólo podrá ir arriba, abajo, izquierda, derecha.

```ts
enum Direcctions { Left, Rigth, Up, Down };
```

De esta forma, cuando queramos moverlo o comprobar hacia dónde va, sabemos que sólo tiene esas 4 posibilidades y no aceptaremos una que no esté entre ellas.

Pueden usarse para tipar los parámetros de una función.

```ts
enum Animal { Dog, Cat, Rabbit }

function showAnimal(animal:Animal){
  console.log(Animal[animal]);
}
showAnimal(Animal.Dog);
```