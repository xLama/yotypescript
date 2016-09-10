## Clases implementando otras clases {#clases-implementando-otras-clases}

```ts
class A {
    name: String;
    doSomething() { }
}

class B implements A {
    name: String;
    doSomething() { }
}
```

Para ello se hace como si de una interfaz se tratara, con la palabra reservada *implements*. La clase que implementa otra se comporta como una interfaz, es decir, debe implementar sus métodos y atributos.

En nuestro ejemplo, la clase _B_ debería implementar el método *doSomething()*. Los estáticos y privados no se tienen en cuenta del mismo modo que en una interfaz no se pueden declarar.