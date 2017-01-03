### Getters y setter implícitos \(accesors\) {#getters-y-setter-impl-citos-accesors}

Es una forma muy interesante de construir _getters_ y _setters_ pues sintácticamente son invisibles a la hora de acceder a los atributos.

En el apartado anterior hacíamos esto:

```ts
public getName():string{ 
    return this.name;
}

public setName(name:string):void {
    this.name = name;
}
```

Ahora podemos hacer esto:

```ts
public get name():string{ 
    return this.name;
}

public set name(name:string) {
    this.name = name;
}
```

_get_ y _set_ son palabras reservadas del lenguaje. Usadas en un método seguido de un espacio y el nombre de un atributo, lo convertimos en método.

Hay que tener en cuenta que el nombre del _getter_ y _setter_ implícito no puede coincidir con el de la propiedad pues nos daría un error de duplicado.

Para evitar esto lo que se suele hacer es anteponer un guion bajo en los nombres de las propiedades. Así quedaría la clase _Person_ sólo con una propiedad para hacerlo más simple:

```ts
class Person {
    constructor(private _name: string) { }

    public get name(): string {
        return this._name;
    }
    public set name(name: string) {
        this._name = name;
    }
}
```

* _Nota: No se especifica el tipo void como devolución de los setters implícitos, da error de compilación._

Para usarlos basta con acceder a la propiedad como si éste fuera público.

```ts
let carlos = new Person( "Carlos");
person.name = "Carlos";
```

Así combinamos la simpleza sintáctica del acceso a propiedades públicas junto con la practicidad de hacerlo mediante métodos.

