## Las partes de una clase {#las-partes-de-una-clase}

Una clase tiene dos partes bien diferenciadas: una de instancia y otra de clase o estática.

Si creamos una clase:

```ts
class Person {
    public static esperanza_vida: number = 80;
    public nombre: string; constructor() { }
}
```

Parte de instancia: el atributo _nombre._

Parte estática: el atributo _esperanza\_vida_ y el constructor.

La parte estática se referencia con el nombre de la clase por ello no podemos asignar la parte estática a una variable del tipo _Person_. Esto sólo sería correcto si la clase Persona no tuviera ningún miembro.

```ts
let estaticaPersona: Person = Person; // Error
```

Y no es posible porque _Person_ es un tipo en sí mismo. El tipo de _Person _es otro distinto y no _Person_. Sólo las intancias de _Person_ son del tipo _Person_. _Person_ es del tipo _typeof Person_:

```ts
let estaticaPersona: typeof Person = Person; // Correcto
```

Observando el código JS que genera es más sencillo de entender.

```ts
var Person = (function () { function Person () {} return Person;})();
var estaticaPersona = Person;
```

Podemos ver que el tipo de _Persona_ es realmente una función. Esto se puede comprobar con el operador _typeof_

```ts
typeof Person // function
```

Una vez que tenemos la referencia de la parte estática podemos acceder a su constructor y sus miembros estáticos:

```ts
let person = new estaticaPersona(); /* La inferencia tipa con Persona */
```



