## El estado {#estado-y-comportamiento}

Las propiedades de una clase son variables que se declaran dentro de la propia clase.

Seguimos construyendo la clase _Person_. Tenemos que pensar qué características tiene una persona cualquiera, qué es lo que nos define. En este caso hemos optado por su nombre y apellidos. También podría ser el DNI, altura, peso, todo lo que queramos o necesitemos.

```ts
class Person {
    nombre: string;
    apellido1: string;
    apellido2: string;
    constructor(nombre: string, apellido1: string, apellido2?: string) { }
}
```

Hemos declarado sus propiedades pero no están inicializados. Lo hacemos en el constructor.

```ts
class Persona {
    nombre: string;
    apellido1: string;
    apellido2: string;
    constructor(nombre: string, apellido1: string, apellido2?: string) {
        this.nombre = nombre;
        this.apellido1 = apellido1;
        this.apellido2 = apellido2;
    }
}
```

Como podemos ver lo que se introduce como argumento al constructor es lo que en su implementación se le asigna a las propiedades. Normalmente cuando instanciemos una clase debemos inicializar sus propiedades pues es lo que va a definir a ese objeto en particular y lo va a diferenciar del resto de objetos de la misma clase.

Hay que puntualizar que las clases también aceptan propiedades opcionales.

```ts
class Persona {
    nombre?: string;
    apellido1: string;
    apellido2: string /* (…) */
}
```

Esto es realmente útil si tenemos activado _strictNullChecks _ya que de esta forma el tipo de la propiedad también es _undefined_

#### Otra forma de declarar propiedades {#otra-forma-de-declarar-atributos}

Los parámetros de entrada de un constructor pueden ser miembros de la clase \(propiedades\) de forma automática sin declararlos de forma explícita.

```ts
class Persona {
    constructor(private nombre: string, private apellido1: string, private apellido2?: string) { }
    public mostrarNombre(): void {
        alert(this.nombre + " " + this.apellido1 + " " + this.apellido2);
    }
}
```

La diferencia ha sido la de escribir la palabra reservada _private_ \(con _public_ y _protected_ también funciona\) en la propia definición del método constructor. De esta forma estamos declarando de forma automática esos atributos como miembros de la clase. Y, a la hora de introducirlos como argumentos del constructor, ya se estarían inicializando.

El constructor también puede ser público, protegido o privado.

