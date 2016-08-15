## Encapsulamiento {#encapsulamiento}

Todo miembro de una clase es público por defecto. Esto significa que es accesible desde fuera de la clase. Para hacer que un miembro no lo sea, hay que declararlo como privado. Las palabras reservadas son _public_ y _private_.

Normalmente los atributos deben ser siempre privados y la forma de acceder a ellos es mediante métodos públicos llamados _getters_ y _setters_.


```ts
class Person {
    private name: string;
    private surname1: string;
    private surname2: string; 
    //…
}
```

Así, si creamos una instancia de la clase _Person_ llamada _carlos_ y hacemos esto:

carlos.name = "Carlos";

Nos daría un error pues no es accesible desde fuera.

Lo mismo ocurre con los métodos.

```ts
class Person {
    //... 
    private showName(): void {
        alert(this.name + " " + this.surname1 + " " + this.surname2);
    }
}
```

Esta llamada no estaría permitida:

```ts
carlos.showName();
```

Es algo menos común el encontrarse con métodos privados. Se suelen usar para comprobación de datos dentro de la propia clase.

Como hemos dicho, todo miembro es público por defecto sin escribirlo de forma explícita aunque es aconsejable hacerlo para darle mayor legilibidad al código.

Nuestra clase quedaría así:

```ts
class Person {
    private name: string;
    private surname1: string;
    private surname2: string;

    constructor(nombre: string, surname1: string, surname2?: string) {
        this.nombre = nombre;
        this.surname1 = surname1;
        this.surname2 = surname2;
    }
    public showName(): void {
        alert(this.name + " " + this.surname1 + " " + this.surname2);
    }
}
```

Para acceder a esos atributos que hemos declarado como privados, lo que suele hacer es crear pares de métodos públicos por cada uno, llamados _setters_ y _getters_ que contenga el nombre del atributo. Ejemplo:

```ts
public getName():string{ 
    return this.name;
}

public setName(name:string):void {
    this.name = name;
}
```

El método _getName()_ devuelve el nombre, por ello el tipo de retorno debe ser el mismo que el de _nombre_. El método _setName(name:_ **string**_)_ no devuelve nada porque se usa para establecer un nuevo valor a _nombre_. Se exige pasar como argumento una variable del tipo del atributo.

¿Por qué se hace así? De esta forma podemos hacer comprobaciones antes de asignar valores a los atributos del objeto. Si pudiéramos asignar libremente, es posible que pudieran contener valores no deseados.

En este caso un nombre no puede contener números, es absurdo. Como un _string_ acepta como cadena cualquier cosa, habría que comprobar que no contiene números. En el caso de que los contenta no se asigna.

```ts
public setName(name:string):void {
    /*Comprobación de si es un nombre válido. Si no lo es, no asignar*/
    this.name = name;
}
```

Así controlamos que no tenga información errónea.

### Getters y setter implícitos (accesors) {#getters-y-setter-impl-citos-accesors}

Es una forma muy interesante de construir _getters_ y _setters_ pues sintácticamente son invisibles a la hora de acceder a los atributos.

En el apartado anterior hacíamos esto:

```ts
public getNombre():string{ 
    return this.nombre;
}

public setNombre(nombre:string):void {
    this.nombre = nombre;
}
```

Ahora podemos hacer esto:

```ts
public get nombre():string{ 
    return this.nombre;
}

public set nombre(nombre:string) {
    this.nombre = nombre;
}
```

_get_ y _set_ son palabras reservadas del lenguaje. Usadas en un método seguido de un espacio y el nombre de un atributo, lo convertimos en método.

Hay que tener en cuenta que el nombre del _getter_ y _setter_ implícito no puede coincidir con el del atributo pues nos daría un error de duplicado.

Para evitar esto lo que se suele hacer es anteponer un guion bajo en los nombres de los atributos. Así quedaría la clase _Persona_ sólo con un atributo para hacerlo más simple:

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

*   _Nota: No se especifica el tipo void como devolución de los setters implícitos, da error de compilación._

Para usarlos basta con acceder al atributo como si éste fuera público.

```ts
let carlos: Person = new Person( "Carlos");
person.name = "Carlos";
```

Así combinamos la simpleza sintáctica del acceso a atributos públicos junto con la practicidad de hacerlo mediante métodos.