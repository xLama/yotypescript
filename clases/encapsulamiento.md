## Encapsulamiento {#encapsulamiento}

Todo miembro de una clase es público por defecto. Esto significa que es accesible desde fuera de la clase. Para hacer que un miembro no lo sea, hay que declararlo como privado o protegido. Las palabras reservadas son _public, protected y_ _private_.

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

El método _getName\(\)_ devuelve el nombre, por ello el tipo de retorno debe ser el mismo que el de _nombre_. El método _setName\(name:_ _string\)_ no devuelve nada porque se usa para establecer un nuevo valor a _name_. Se exige pasar como argumento una variable del tipo de la propiedad.

¿Por qué se hace así? De esta forma podemos hacer comprobaciones antes de asignar valores a las propiedades del objeto. Si pudiéramos asignar libremente, es posible que pudieran contener valores no deseados.

En este caso un nombre no puede contener números, es absurdo. Como un _string_ acepta como cadena cualquier cosa, habría que comprobar que no contiene números. En el caso de que los contenta no se asigna.

```ts
public setName(name:string):void {
    /*Comprobación de si es un nombre válido. Si no lo es, no asignar*/
    this.name = name;
}
```

Así controlamos que no tenga información errónea.

