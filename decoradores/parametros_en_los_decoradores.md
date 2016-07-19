## Parámetros en los decoradores {#par-metros-en-los-decoradores}

Los decoradores aceptan argumentos a la hora de declararlos pero para ello la función que lo implementa debe ser modificada ligeramente. Tomando como ejemplo el decorador de método:

```ts
class Person {
    @writable(false) public walk(): void {
        console.log("walk");
    }
}
function writable(writable: boolean) {
    return function (target: Object, propertyKey: string, descriptor: TypedPropertyDescriptor<any>) {
        descriptor.writable = writable;
        return descriptor;
    }
}

Person.prototype.walk = function () { }; // No tiene efecto
```

Se ha modificado para que el decorador @writable acepte un parámetro **boolean** para decidir si el método debser escribible o no. En este caso la función que hace de decorador debe devolver una función con una definición igual a la usada cuando no tiene parámetros.