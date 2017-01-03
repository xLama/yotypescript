## Introducción {#introducci-n}

Los genéricos permiten parametrizar directamente las clases e interfaces. Son un paso más en la abstracción.

Hasta ahora habíamos definido clases no genéricas como _Concesionario_:

```ts
class Concesionario { }
```

Esta clase es capaz de englobar todos los concesionarios de las marcas de los coches. En ella iremos guardando una lista de los coches de cada concesionario.

¿Pero para qué marcas de automóviles diseñaremos la clase? Podemos hacerlas para todas con el uso de genéricos.

```ts
class Concesionario<T>{
    private coches: T[];
    constructor() {
        this.coches = []
    }
    public getCoche(indice: number): T {
        return this.coches[indice];
    }
}
```

Para hacerlo se añade _&lt;T&gt;_ después del nombre de la clase. Realmente puedes escribir lo que quieras, no necesariamente una T. Ademas puedes parametrizar con una lista si te hace falta:

```ts
class Concesionario<T, V, K>{ }
```

Tenemos, por ejemplo, la clase _Seat_:

```ts
class Seat { }
```

Vamos a crear un concesionario de _Seat_:

```ts
let concesionarioSeat = new Concesionario<Seat>();
```

Como puedes ver hemos usado la clase _Seat_ para parametrizar el genérico. De esta forma donde la clase es T, ahora es Seat.

Clase original:

```ts
class Concesionario<T>{
    private coches: T[];

    constructor() {
        this.coches = []
    }

    public getCoche(indice: number): T {
        return this.coches[indice];
    }
}
```

Clase al sustituir T por _Seat_:

```ts
class Concesionario<Seat>{
    private coches: Seat[];

    constructor() {
        this.coches = []
    }
    public getCoche(indice: number): Seat {
        return this.coches[indice];
    }
}
```

El compilador sustituye el parámetro genérico T por la clase que le hemos proporcionado, en este caso _Seat_. A este proceso se le llama instancia de tipo genérico.

Hemos conseguido que el array de coches de la clase sea de coches de la marca _Seat_. Lo mismo si lo hacemos con otras marcas:

```ts
class Audi { }
class Ferrari { }

let conceAudi = new Concesionario<Audi>();
let conceFerrari = new Concesionario<Ferrari>();
```



