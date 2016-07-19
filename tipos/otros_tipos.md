## Otros tipos {#otros-tipos}

### Void {#void}

Sólo sirve para determinar que una función no devuelve ningún valor. También se podrían tipar variables con void pero carece de sentido.

### Null {#null}

No se puede tipar una variable con _Null._ Sólo puede ser el valor de la variable. Cualquier tipo de variable puede contener el valor _null_. Representa valor nulo.

```ts
let variable: Boolean = null;
```

### Undefined {#undefined}

Representa variables no inicializadas. También podemos asignar el valor _undefined_ a una variable de cualquier tipo:

```ts
let variable: Boolean = undefined;
```
### Never {#never}

Representa valores que nunca pueden ocurrir.

### [Enum](../control_del_flujo/sentencias_utiles_para_los_bucles.md#757309351116418-_Enumerados) {#enum}

Es una forma más amigable de representar los números.

```ts
enum Animals { Dog, Cat };
let dog = Animals.Dog;
```

Perro representaría el 0, Gato el 1 y así sucesivamente.

### [Function](../enumerados/obteniendo_el_nombre_del_valor.md#757309351116418-_Funciones) {#function}

En TS, como en JS, una función también es un objeto y se puede almacenar como tal.

```ts
let funcion: Function;
```

### [Array](../modulos/evitar_que_una_clase_pueda_ser_superclase.md#757309351116418-_Anexo_I._) {#array}

Los arrays son colecciones de datos. Podemos declarar un _array_ de dos formas:

```ts
let array1: Array<tipoDato>;
let array2: tipoDato[];
```

Son compatibles entre sí al 100% y se pueden asignar de forma recíproca.

tipoDato se refiere al tipo de dato de los objetos que va almacenar el array:

```ts
let array1: Array<number>;
let array2: Array<string>;
```

Incluso otro array;

```ts
let arrayDeArrays: Array<Array<number>>;
```

Para inicializarlos tenemos, a su vez, dos formas:

```ts
let array1: Array<number> = new Array<number>();
let array2: number[] = [];
```

En *array2* podríamos incluso introducir valores separados por comas:

```ts
let array2: number[] = [1, 2, 3, 4, 90];
```

No hace falta determinar el tamaño del array. Este tipo tiene un tamaño dinámico que puede ir creciendo según las necesidades.

### Object {#object}

Toda la información relevante a este tipo está disponible en [este tema](../objetos/README.md).

### Symbols {#symbols}

Sólo existen a partir de la ES6 por lo que para usarlo debes compilar TS con el target "ES6"

Son valores únicos e inmutables, es decir, una vez declarados e inicializados no se pueden modificar y no puede haber dos iguales. Para instanciarlos se usa la función *Symbol*. No es posible utilizar el operador _new_ ya que daría un _TypeError_. El tipo es **symbol**

```**var** aSymbol : **symbol** = Symbol();**var** otherSymbol : **symbol** = **new** Symbol(); // Error```

Se le puede pasar un **string** como argumento a la función _Symbol_ que sirve como identificador:

```**var** aSymbol : **symbol** = Symbol("aSymbol");```

Esto no quiere decir que si creamos dos **symbol** con un mismo indentificador, éstos sean iguales:

```Symbol("aSymbol") === Symbol("aSymbol"); // False```

Una de las grandes utilidades de los **symbol** es que pueden ser usados como [propiedades de objetos](../objetos/propiedades_computadas_computed_properties.md#propiedades-symbol). Además existen los llamados “bien conocidos” que son **symbol** predefinidos que sirven para identificar funcionalidades específicas, como los [iteradores.](../iteradores/README.md)

### Tipos Alias. (Alias Types) {#tipos-alias-alias-types}

Este tipo es simplemente llamar de otra forma a un tipo ya definido. Se usa la palabra reservada _type._ Es útil para los tipos unión e intersección

**type** numberAndString = **number** | **string**;**var** g :numberAndString // Es del tipo string | number

También es compatible con los [genéricos](../genericos/README.md):

**class** Collection&lt;T&gt; { **private** list:T[];} **type** List&lt;T&gt; = T[] | Collection&lt;T&gt; ;**type** ListNumber = List<**number**> ;

**var** list: ListNumber = []; **var** list2: ListNumber = **new** Collection<**number**>();

### Tuple Types (Tipos tupla) {#tuple-types-tipos-tupla}

Se utiliza en los _arrays_ y sirve para determinar distintos tipos según la posición del elemento dentro del array.

**var** array: [**number**, **string**];array = [5, "cadena"];

A la hora de introducir elementos en el array es obligatorio, al menos, el mismo número de ellos que de tipos declarados.

**var** array: [**number**, **string**];array = [5]; // Error

Además, si introducimos un elemento no compatible con ninguno de los declarados, nos muestra un error de compilación.

**var** array: [**number**, **string**];array = [5, "cadena", ()=>void]; // Error

Si te estás preguntando qué tipo tendría un dato introducido en una posición en la que no se ha declarado tipo, la respuesta es la unión de tipos.

**var** array: [**number**, **string**];**var** dato = array[8]; // number | string

### Tipos Unión (Union Types) {#tipos-uni-n-union-types}

Los tipos unión determinan qué tipo de datos puede albergar una variable. Normalmente tipamos las variables con un solo tipo pero con esta característica podemos hacerlo con varios.

**var** x: **number** | **string**;x = "cadena"; // Correctox = 12; // Correctox = **false**; // Error

Además se pueden crear tipos unión de forma automática en las [interfaces](../interfaces/README.md) o [clases](../clases/README.md).

**class** A{ **** x: **string;**}**class** B{ **** x: **number;**}******var** variable : A | B; variable.x // Es del tipo string | number

Cuando se habla de compatibilidad de tipos es lógico pensar que un tipo unión es compatible con todos los tipos que lo componen. Esto quiere decir que se aplica siempre que TypeScript esté comparando tipos ya sea en clases, interfaces, genéricos, etc.

### Tipos Intersección (Intersection Types) {#tipos-intersecci-n-intersection-types}

Si antes hemos visto la unión de tipos, ahora vamos a ver la intersección. El nombre puede confundir ya que podríamos entender unión de tipos como la combinación de los tipos. Realmente tiene ese nombre porque puede albergar cualquier dato de los tipos de la unión. En la intersección la mecánica es distinta. Cuando tipamos con una intersección de tipos, estamos haciendo que de forma obligatoria el valor debe ser de todos los tipos especificados:

**type** A={ x: **string** } & **{** z: **number }var** foo: A ;

Para inicilizar la variable _foo_ del ejemplo se necesita un objeto que contenga tanto la propiedad _x_ como _z_:

**type** A **=** { x: **string** } & **{** z: **number }var** foo: A = { x : "foo" , z : 5};

Si los nombres de las propiedades coinciden, el resultado sería la intersección de sus tipos.

**type** A **=** { x: **string** } & **{** x: **number }**

Un momento, **string** y **number** son primitivos por lo que el valor que le asigne a _x_ debe ser uno del tipo compatible con los dos nombrados. ¿Cuál existe que cumpla esa condición? La respuesta es: solo _null_ y _undefined_. No podemos asignar un valor que sea de dos o más tipos primitivos porque no existe, más allá de los ya expuestos. Por eso hay que tener mucho cuidado a la hora de intersecar tipos porque no podría dar un comportamiento no deseado.

Podemos intesectar clases, interfaces, etc teniendo en cuenta que sus miembros con igual nombre también se van a intersecar, y esto ocurre en todos los niveles:

**class** C{ **** x: **string;**}**class** D{ **** x: **number;**}**class** A{ **** member:C;****}**class** B{ **** member:D;****}******var** intersect : A & B; intersect.member.x = "2"; // Error. Es del tipo number & string.

Hemos interseaco A & B . Como ambos tienen un miembro llamado member, estos también se intersecan. Los miembros son del tipo C y D. Al intersecar estos tipos, los cuales también tienen un miembro del mismo nombre, x, también se intersecan. Resulta que esos miembros son primitivos por lo que al final nos da como resultado _number & string._

### Tipos Locales (Local Types) {#tipos-locales-local-types}

No son más que clases, interfaces, enumerados y tipos alias que se declaran dentro un bloque de cógido (entre llaves). Éstos son sólo accesibles en ese bloque, al igual que ocurre con las variables declaradas con el operador _let_.

**function** local(){ **if** (Math.random() > 0.5){ **interface** Baz {} } **var** bar: Bar = **new** Bar(); /*Error. Bar solo accessible dentro del if */ **class** Foo {};****}

**var** bar: Foo = **new** Foo(); /* Error. _Foo_ solo es accessible dentro de _local_() */

### Tipos de cadenas literales (String Literal Types) {#tipos-de-cadenas-literales-string-literal-types}

Son tipos definidos por una **string** literal. Así de simple. El único valor que puede contener una variable tipada con una cadena literal, es la propia cadena.

**let** name : "Lama" = "Lama";

Pero se puede usar junto con los tipos unión para darle más utilidad:

**let** movement : "up" | "right" | "down" | "left";

Así la variable movement sólo puede contener esas cadenas. Esto resulta muy interesante si lo tratamos como un enumerado, es decir, sería un enumerado de cadenas:

**let** movements : "up" | "right" | "down" | "left";**let** movement : movements = "right";// Ok**let** otherMovement : movements = "upDown"; // Error

Mucho cuidado con los tipos intersección. No tiene sentido que dos cadenas distintas se intersequen pues nunca va a existir un valor que satisfaga esa intersección.

**let** movements : "up" & "right";**let** movement : movements = "right";// Error

Para que la asignación fuera correcta la cadena como valor debe ser a up y right a la vez, cosa que no es posible. Además son tratados como cadenas (su tipo aparente es el mismo), por lo que tienen la misma interfaz, es decir, mismas propiedades y métodos.

### Guarda de tipos (Type Guards) {#guarda-de-tipos-type-guards}

Visto los los Tipos Unión y como ya veremos en el polimorfismo, es posible que un mismo parámetro pueda contener valores de distinto tipo en momentos diferentes. Eso requiere que cuando tratemos ese dato debamos saber de qué tipo es para crear un comportamiento adecuado:

**function** guards(age : **number** | **string**){}age("26");age(26);

En el ejemplo no sabemos, a la hora de construir el cuerpo de la función, el tipo del valor, ya que puede ser **number** o **string**. TS nos proporciona un mecanismo para estos casos que nos ahorra trabajo, con la guarda de tipos. Éstas son de dos formas: con [typeof](typeof.md) e [instanceof](../clases/instanceof.md). En nuestro caso:

**typeof** age === "string"; age **instanceof** String;

Ya que estamos trabajando con primitivos, la que nos interesa es el _typeof,_ puesto que el otro dará error. La guarda se realiza con sentencias de control de flujo, más concretamente con _if_ y sus derivados. Las variables dentro de las guardas son convertidas al tipo con el que comparamos:

**function** halfLife(age : **number** | **string**){ **if** (**typeof** age === "string"){ **return** +age / 2; // Aquí age es string } **else** { **return** age / 2; // Aquí age es number }}age("26");age(26);

Ya que la comparación ha sido si _age_ es un **string**, dentro de ese bloque _if,_ _age_ es convertido (las especificaciones del lenguaje lo denomina “estrechamiento”) a **string** por lo que podemos tratarlo como tal. En el else, y al solo quedar **number** como alternativa, es convertido a **number**. Si la condición hubiera sido “no es un **string**”, los roles se intercambiarían:

**function** halfLife(age : **number** | **string**){ **if** (**typeof** age !== "string"){ **return** age / 2; // Aquí age es number } **else** { **return** +age / 2; // Aquí age es string }}age("26");age(26);

El operador unario usado en un **string** convierte la cadena en un **number.**

Se puede complicar más porque es possible que el parámetro sea del Tipo Unión de más de dos:

**function** halfLife(age : **number** | **string** | { age: **number** }){ **if** (**typeof** age === "string"){ **return** +age / 2; // Aquí age es string } **else** { **return** age / 2; /* Aquí age es number | {age: number}. Error. No puede dividir {age: number} entre 2 */ }}halfLife ("26");halfLife (26);halfLife ({ age : 26});

Esta vez el bloque _else_ utiliza _age_ como si fuera un **number** **| {age: number** **} (Tipo Unión) y aunque el number** lo pueda dividir entre 2, no así el objeto. Para solucionar esto lo major es atomizar las guardas siempre y cuando los tipos no sean compatibles, como es el caso:

**function** halfLife(age : **number** | **string** | { age: **number** }){ **if** ( **typeof** age === "string"){ **return** +age / 2; // Aquí age es string } **else** if (**typeof** age === "number"){ **return** age / 2; // Aquí age es number } **else**{ **return** age.age / 2; // Aquí age es {age:number} }}halfLife ("26");halfLife (26);halfLife ({ age : 26});

Es preferible primero hacer la guarda de los primitivos y dejar para el final los tipos objeto.

### Guardas propias {#guardas-propias}

Hemos hecho guardas con operadores propios del lenguaje que son usados para comprobar tipo. Esto, aunque supone una ventaja importante, también es cierto que no es flexible ya que nos obliga a reescribir el mismo código una y otra vez si necesitamos la misma comprobación en sitios distintos. Hay una forma de crear las nuestras. Para ello hay que definir una función que actuará de guarda en el que el tipo devuelto sea la expresión “x is C” donde _x_ es el parámetro de la función y _C_ es el tipo:

**class** Person{}**class** Student **extends** Person{ studentId:**string**;}**class** Teacher **extends** Person{ teacherId:**string**;}**function** isStudent(p:Person): p **is** Student { // Aquí lo importante **return** p **instanceof** Student;}

**function** isTeacher(p:Person): p **is** Teacher { // Aquí lo importante **return** p **instanceof** Teacher;}**var** person: Person;

**if** (isStudent(person)){ person.studentId; // Aquí person es un Student } **else if** (isTeacher(person)){ person.teacherId; // Aquí person es un Teacher }

No se puede tener más de una expression de guarda por función. Si no entiendes el ejemplo te recomiendo que vuelvas a este apartado una vez hayas visto las [clases](../clases/README.md).

### Guardas basadas en this {#guardas-basadas-en-this}

Simplemente producen estrechamiento al tipo de this si se cumple la condición. Esto es útil en contadas ocasiones porque parte de la premisa que una clase padre conoce a sus clases hijas y eso, desde un punto de vista de diseño de software, no es recomendable. Pero eso no quiere decir que sea algo inútil. Las guardas basadas en this siguen la expresión “this is C”, muy parecida a la anterior “x is C”, pero ahora x es this, porque estas guardas se utilizan en métodos.

**class** Structure { isDirectory() : this **is** Directory { **return** this **instanceof** Directory} isFile() : this **is** File { **return** this **instanceof** File}}**class** File **extends** Structure {}**class** Directory **extends** Structure {}**let** file : Structure = // Código para leer una estructura

**if** (file.isFile()){ file.studentId; // Aquí file es un Directory } **else if** (file.isDirectory()){ file.teacherId; // Aquí file es un File }