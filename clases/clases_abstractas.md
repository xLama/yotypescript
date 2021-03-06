## Clases abstractas {#clases-abstractas}

Una clase abstracta es aquélla que no se puede instanciar. Puede definir métodos los cuales delega su implementación en las clases hijas.

Para hacer que una clase sea abstracta se debe declarar con la palabra reservada _abstract_.

```ts
abstract class Human {}
```

Con esto conseguimos que clases que sólo sirven como base de otras no se puedan instanciar porque no tiene sentido hacerlo.

Hay que tener en cuenta una serie de puntos:

* Los métodos pueden ser abstractos pero al serlo no pueden contener implementación y convierte a su clase en clase abstracta:

```ts
class Human {
    // Error. La clase también debe ser abstracta.
    abstract walk(): void { } // Error. No pueden contener implementación.
}
```

* Las propiedades también pueden ser abstractas aunque a éstas si se les puede asginar un valor. De igual obliga a la clase a ser abstracta.

```ts
abstract class Human {
    abstract life = 80;
}
```

* Los métodos o propiedades abstractos son heredados de forma que en las subclases deben implementarse o bien declararlos también como abstractos:

```ts
abstract class Human {
    abstract walk(): void
}
abstract class Person extends Human { }
```

Esto sería erróneo.

```ts
abstract class Human {
    abstract walk(): void
}
class Person extends Human { } // Error
```

Lo es porque la subclase está herendando el método _walk_ el cual es abstracto y hemos dicho que una clase con algún método abstracto debe serlo también.

* Es lógico pensar que si se declaran abstractos para que sean implementados por sus subclases, no pueden ser _private_. Los modificadores de visibilidad deben preceder a _abstract_:

```ts
abstract class Human {
    private abstract walk(): void // Error
}
```

Tampoco pueden ser estáticos:

```ts
abstract class Human {
    static abstract walk(): void // Error
}
```

* Otra acción ilegal es invocar métodos de la clase padre que sean abstractos. Pero sí se pueden invocar si pertenecen a la propia clase:

```ts
abstract class Human {
    abstract walk(): void
}
abstract class Person extends Human {
    abstract talk(): void;
    public walk(): void {
        this.talk();// Ok 
        super.walk(); // Error 
    }
}
```

* Todos los métodos sobrecargados deben ser declarados abstractos o no abstractos, además deben ir todas juntas:

```ts
abstract class Person {
    public abstract walk(speed: number, direction: string): void; /* Error. Todas deben ir consecutivas */
    private _speed: number
    public walk(speed: number): void; // Error. Todos abstractos o ninguno.
}
```

* No se pueden asignar clases abstractas a clases no abstractas:

```ts
abstract class Human { }
class Person extends Human { }
let Hum : typeof Person = Human; // Error
```

Las clases abstractas son una buena forma de generalizar diseños dejando que solo sirvan como contenedores de funcionalidad sin que la propia clase sea un actor de la aplicación. Un claro ejemplo en un videojuego sería la clase _Enemy_. Ésta sería abstracta porque no necesitamos instanciarla ya que tenemos muchos tipos de enemigos los cuales van a tener cada uno su propia clase. Pero en lo que sí nos ayuda la clase Enemy es en agrupar la misma funcionalidad de todos los enemigos del juego y obligar a las subclases a implementar métodos que con obligatorios para todos, como por ejemplo el método _attack_. Resulta de grandísima utilidad cuando trabajamos con el patrón de diseño Template Method.

