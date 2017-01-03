## Decorador de atributo {#decorador-de-atributo}

Parámetros:

* target : Object - El prototype de la clase.
* propertyName : _string_ \| _symbol_ - El nombre del atributo.

Los atributos de una clase también pueden decorarse aunque con limitaciones. No se les puede cambiar la visibilidad \(público, protegido o privado\) pero sí prácticamente todo lo demás. Es muy útil para la inyección de dependencias.

```ts
class Person {
    @nameDecorator public name: string;
}

function nameDecorator(target: {}, propertyName: string) {
    target[propertyName] = "Carlos";
}

let person = new Person();
person.name; // Carlos
```

Se está inyectando el nombre _Carlos_ en todas las instancias de _Person_.

