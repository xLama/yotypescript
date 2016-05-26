## Decorador de clase {#decorador-de-clase}

Como su nombre indica decora la declaración de una clase. Esto es importante porque no decora las instancias, sino la clase en sí y en el momento de ser declarada.

Parámetros:

*   target : Function - La clase.

```ts
@decorator 
class Person{}
```

```ts
function decorator(target : Function){ 
  target["IAmDecorated"] = true;
}
Person["IAmDecorated"]; //true
```

En el decorador podemos modificar la clase añadiendo o elminando miembros. En el ejemplo hemos añadido una propiedad llamada *IAmDecorated* como miembro estático. Si quisiéramos añadirlo como membro de instancia sólo habría que usar _prototype_:

```ts
@decorator 
class Person { } 

function decorator(target: Function) { 
  target.prototype["IAmDecorated"] = true; 
} 

let person = new Person(); 
person["IAmDecorated"] //true
```