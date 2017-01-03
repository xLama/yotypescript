## Herencia {#herencia}

Existe también la herencia de interfaces mediante _extends_ como vimos en el tema de las clases.

```ts
interface Desplazable extends Motriz { }
```

Si una clase implementa la interfaz _Desplazable_, no sólo debe implementar todo lo que le obliga _Desplazable_, sino también todo lo de _Motriz_. Las reglas de sobreescritura son las mismas que para las clases.

Una clase que herede de otra clase que implemente una interfaz, estaría también implementándola de forma implícita.

```ts
class Person implements Desplazable, Inteligente {
    //(...)
}

class Student extends Person {
    //(...)
}
```

La clase _Student_ estaría implementando las interfaces _Desplazable_ y _Motriz_ a través de _Person_, que es clase padre.

