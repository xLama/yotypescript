## Decorador de parámetro {#decorador-de-par-metro}

Parámetros:

*   target : Object - El prototype de la clase.
*   propertyName : *string* | *symbol* - El nombre del atributo.
*   parameterIndex : *number* – Número que determina la posición del parámetro.

Los parámetros también se pueden decorar:

```ts
class Person {
    public name: string;
    constructor( @propertyDecorator name: string) {
        this.name = name;
    }
}
function propertyDecorator(target: {}, propertyName: string, parameterIndex: number) {
    target[propertyName] = "Carlos";
}
let person = new Person("");
person.name; // Carlos
```