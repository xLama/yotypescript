## Estáticos {#est-ticos}

Hasta ahora, todos los miembros que hemos creado son de instancia. Esto quiere decir que para cada instancia que creemos de una clase, serán independientes unas de otras.

```ts
let jose = new Person("José", "Lama");
let carlos = new Person("Carlos", "Ponce");
```

Son dos instancias distintas de _Persona_ en la que sus datos no tienen relación entre sí. Si cambio el nombre de jose, _carlos_ seguirá igual que antes.

Existe un modificar llamado _static_ que es una palabra reservada del lenguaje. Con él conseguimos que un miembro sea accesible sin crear instancias de la misma.

```ts
class Person {
    /* (...) */

    public static mostrarNombre() {
        alert("estático");
    }
}
```

Para acceder a los miembros estáticos se hace directamente con el nombre de la clase seguido del operador . (punto)

_Person.mostrarNombre();_

Desde un método estático no se puede acceder a miembros no estáticos. Y tiene mucho sentido. Recordemos que los miembros no estáticos son aquéllos que pertenecen a la instancia. Si los estáticos pueden usarse sin crear ninguna instancia, ¿cómo van a poder usar miembros no estáticos?

Otra característica es que los miembros estáticos son transversales por lo que no cambian por cada instancia que creemos de la clase.