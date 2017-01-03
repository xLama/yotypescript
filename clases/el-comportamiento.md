### El comportamiento {#el-comportamiento}

¿Qué podemos hacer ahora? Darle un comportamiento a través de métodos.

¿Qué puede hacer una persona? Puede hablar, caminar, comer… El comportamiento de una clase suele definirse también como verbos. Evidentemente no todas las acciones tienen sentido en todos los contextos. Si estamos creando la clase _Persona_ para un registro de alumnos de un colegio, no tiene sentido implementar un método que se llame _caminar_. Podría tenerlo si estuviéramos desarrollando un juego.

Para el ejemplo crearemos un método llamado showName_\(\)_ que mostrará en un _alert\(\)_ el nombre de la persona junto con sus apellidos.

```ts
class Person {

    nombre: string; 
    apellido1: string; 
    apellido2: string; 
    
    constructor(nombre: string, apellido1: string, apellido2?: string) {
        this.nombre = nombre;
        this.apellido1 = apellido1;
        this.apellido2 = apellido2;
    }

    showName(): void {
        alert(this.nombre + " " + this.apellido1 + " " + this.apellido2);
    }
}
```

Puedes observar que muestra la concatenación de los atributos que hemos insertado como argumentos a la hora de instanciar la clase.

Bien, hemos creado unos atributos y un método que define un comportamiento. ¿Cómo accedemos a ellos? Con el operador “.” \(punto\).

Al instanciar la clase:

```ts
let person = new Person("Carlos", "Lama");
```

Podemos acceder a sus miembros con el nombre de la variable seguido de un punto, seguido del miembro al que deseemos acceder. 

Si es una propiedad podemos leer el valor o modificarlo.

```ts
person.nombre = "Carlos";
```

Si es una función podemos invocarla:

```ts
persona.showName();
```



