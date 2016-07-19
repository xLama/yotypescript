## this en los decoradores {#this-en-los-decoradores}

Hay que tener en cuenta que la sentencia **this** dentro de un decorador hace referencia a Window si no usamos el modo estricto o a undefined si lo usamos. No hace referencia ni a la clase ni a la instancia.

Tomando el ejemplo del decorador de clase:

```ts
class Person {
    @propertyDecortator public name: string;
}

function propertyDecortator(target: {}, propertyName: string) {
    this; //Window 
    target[propertyName] = "Carlos";
}
let person = new Person();
person.name; // Carlos
```