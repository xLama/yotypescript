## Agregación y composición {#agregaci-n-y-composici-n}

Para empezar hay que concretar que las diferencias entre agregación y composición son conceptuales y no se reflejan en el código.

Si en la herencia establecíamos una relación de es-un, en la composición la relación es la de usa-un.

Cuando empezamos a ver los miembros de una clase, pudimos observar que no sólo podrían declararse variables de tipos primitivos o objeto, sino que podíamos usar los propios.

```ts
class Person {
    private adress: Adress;
    private id: Nif;
}
```

En la clase *Student* podemos declarar una variable dirección del tipo *Adress* que agrupe toda la información necesaria: calle, número, código postal, etc. Y otra del tipo *Nif* que contiene el número, la letra, los dígitos de control, etc. Esa relación entre *Persona* y *Adress* y *Persona* y *Nif* es lo que se conoce como usa-un.

En un principio la agregación es mucho más utilizada que la composición. La gran diferencia entre ambas es que la agregación supone una relación débil, es decir, los elementos relacionados tienen vida por sí solos. En la composición uno no se entiende sin el otro.

En nuestro ejemplo de la clase *Person* estaríamos usando la agregación con *Adress* ¿Por qué? Porque una persona seguirá siendo un persona aunque no tenga una dirección postal. Y su *Adress* perdurará aunque muera.

No ocurre lo mismo con el *Nif*. Es cierto que una persona sin *Nif* sigue siendo una persona pero si ésta muere, su *Nif* ya no será válido, por lo que desaparece legalmente. Podemos decir que el *Nif* tiene una dependencia fuerte de _Persona_.

Hay autores que opinan que el uso de la composición/agregación es un mejor camino que la de la herencia. Otros afirman lo contrario. No es objeto de este libro el intentar esclarecer cuál es mejor ni peor porque en mi opinión no es tan simple. El uso de uno u otro depende del diseño que le queramos dar a nuestra aplicación y siempre serán los problemas que se nos planteen los que decidirán. En todo caso la virtud está en el punto medio.