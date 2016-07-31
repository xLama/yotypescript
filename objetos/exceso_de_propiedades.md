## Exceso de propiedades {#exceso-de-propiedades}

El funcionamiento es el que sigue:

Un objeto literal se considera fresco en cuanto se inicializa. Esa frescura desaparece cuando se realiza una confirmación de tipo (_type assertion_). Sólo las propiedades de los objetos frescos no capturados en variables son comparados para comprobar que no tienen más propiedades que las de su tipo, siempre que éste (el tipo) no sea el objeto vacío {}, por lo que la comparación ya no se realiza.

Expliquemos paso por paso.

Objeto literal fresco es simplemente un objeto literal cualquiera.

```ts
{ name: "Carlos", age : 26};
```

Si asignamos ese objeto literal a un tipo objeto literal que no sea el objeto vacío {}, se va a comprobar que el objeto literal no tenga más propiedades que las del tipo, de lo contrario dará error:

```ts
type Person = {name: string , age: number }
let carlos : Person = { name: "Carlos", age : 26}; // Correcto
let carlos2: Person = { name: "Carlos", age : 26, nationality: "spanish" } /* Incorrecto. Tiene más propiedades. */
```
¿Por qué hace esta comparación? Hemos dicho que es un objeto fresco y, además, no está capturado en una variable previamente, sino que se ha asignado directamente. Por otra parte tampoco se ha hecho una confirmación de tipo así que no cumplen los requisitos para que la comparación de exceso de atributos se realice.

Si cumplimos con alguna de las dos, es decir, hacer una confirmación de tipo para que el objeto deje se ser fresco o capturarlo previamente en una variable cuyo tipo sea el mismo que el suyo (podemos dejar que la nferencia trabaje) la comparación de exceso no tendrá lugar:

Hacer que el objeto deje de ser fresco:

```ts
type Person = {name: string , age: number }
let carlos2: Person = { name: "Carlos", age : 26, nationality: "spanish" } as Person /* Correcto. Confirmación de tipo. */
```
Capturarlo en una variable:

```ts
type Person = {name: string , age: number }
let jc = { name: "Carlos", age : 26, nationality: "spanish" }; 
let carlos : Person = jc // Correcto

let carlos2: Person =  { name: "Carlos", age : 26, nationality: "spanish" } as Person /* Correcto. Confirmación de tipo. */
```
Se puede, sin embargo, hacer que un tipo objeto literal sea infinito y admita todos las propiedades que queramos. Para ello hay que usar la signatura índice (index signature):

```ts
type Person = {name: string , age: number,[more: string ] : any }
let carlos : Person = { name: "Carlos", age : 26, nationality: "spanish" };
```
Es correcto porque hemos indeterminado el número de propiedades haciendo que el nombre de la propiedad sea un string y su valor sea cualquier cosa.

Como esta característica puede hacer que código antiguo no funcione, se ha incluido un parámetro en el compilador para que esta comprobación no se haga nunca. Se puede configurar en el archivo tsconfig.json añadiendo "suppressExcessPropertyErrors": true