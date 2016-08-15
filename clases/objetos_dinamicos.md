## Objetos dinámicos {#objetos-din-micos}

Todo objeto en TS es dinámico. Esto quiere decir que podemos añadirle atributos en tiempo de ejecución con la sintaxis adecuada.

```ts
class Persona { }
let carlos = new Persona();
carlos["edad"] = 26;
let edad = carlos["edad"]; // 
```

A la instancia llamada _carlos_ le hemos añadido un atributo de nombre _edad_ que inicializamos con el número 26\. Esto es totalmente válido y podemos añadir cuantos queramos.

Es evidente que de esta forma perdemos todo resquicio de tipado pues no sabemos qué va a devolver una vez accedamos al atributo _edad_ por eso la inferencia tipa la variables _edad_ con _any_. TS intenta controlar esto con los diccionarios.

```ts
class Persona { [index: string]: number; }
let carlos = new Persona();
carlos["edad"] = 26;
let edad = carlos["edad"]; // number
```

Conseguimos saber qué tipo de datos va a devolver que en este caso es _number_. La inferencia ha hecho su trabajo.

Podemos tener como máximo dos indexaciones: una por _string y otra number_.

```ts
class Diccionario {
    [index: string]: string;
    [index: number]: string;
}
```

La única restricción es que el tipo devuelvo por la numérica sea compatible con el de _string_.

```ts
class Diccionario {
    [index: string]: string;
    [index: number]: number; // Error
}
```

El tipo devuelto por _[index:_ number_]_ es number _que no es compatible con _string_.

Si queremos que el índice por string pueda contener valores de distinto tipo, podemos recurrir a los tipos union:

```ts
class Diccionario {
    [index: string]: string | number;
}
```

Ahora podemos añadir valores que sean tanto cadenas como números:

```ts
class Diccionario { [index: string]: string | number;}
let dicc = new Diccionario();
dicc["spanish"] = "español";
dicc["SpainPopulation"] = 45000000;
```

La compatibilidad se gestiona de la misma forma que ya hemos estudiado las compatibilidades de primitivos, objetos, etc.

De esta forma podríamos crear lo que en otros lenguajes, como PHP, se llaman arrays asociativos, donde el íncide no es numérico, sino una cadena de caracteres.