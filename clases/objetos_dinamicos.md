## Objetos dinámicos {#objetos-din-micos}

Todo objeto en TS es dinámico. Esto quiere decir que podemos añadirle atributos en tiempo de ejecución con la sintaxis adecuada.

**class** Persona{}**var** carlos:Persona = **new** Persona();carlos["edad"] = 26;**var** edad = carlos["edad"]; // any

A la instancia llamada _carlos_ le hemos añadido un atributo de nombre _edad_ que inicializamos con el número 26\. Esto es totalmente válido y podemos añadir cuantos queramos.

Es evidente que de esta forma perdemos todo resquicio de tipado pues no sabemos qué va a devolver una vez accedamos al atributo _edad_ por eso la inferencia tipa la variables _edad_ con **any**. TS intenta controlar esto con los diccionarios.

**class** Persona { **** [index: **string**]: **number**;}

**var** carlos: Persona = **new** Persona();carlos["edad"] = 26;**var** edad = carlos["edad"]; // number

Conseguimos saber qué tipo de datos va a devolver que en este caso es **number**_._ La inferencia ha hecho su trabajo.

Podemos tener como máximo dos indexaciones: una por **string** y otra **number**_._

**class** Diccionario { **** [index: **string**]: **string**; [index: **number**]: **string**;}

La única restricción es que el tipo devuelvo por la numérica sea compatible con el de **string**.

**class** Diccionario {**** [index: **string**]: **string**; [index: **number**]: **number**; // Error}

El tipo devuelto por _[index:_ **number**_]_ es **number** que no es compatible con **string**.

Si queremos que el índice por **string** pueda contener valores de distinto tipo, podemos recurrir a los tipos union:

**class** Diccionario {**** [index: **string**]: **string** | **number**;}

Ahora podemos añadir valores que sean tanto cadenas como números:

**class** Diccionario {**** [index: **string**]: **string** | **number**;}**var** dicc: Diccionario = **new** Diccionario ();dicc["spanish"] = "español";dicc["SpainPopulation"] = 45000000;

La compatibilidad se gestiona de la misma forma que ya hemos estudiado las compatibilidades de primitivos, objetos, etc.

De esta forma podríamos crear lo que en otros lenguajes, como PHP, se llaman arrays asociativos, donde el íncide no es numérico, sino una cadena de caracteres.