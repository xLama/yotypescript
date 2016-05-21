## Propiedades opcionales {#propiedades-opcionales}

Conjuntamente con las propiedades obligatorias se pueden definir opcionales. Éstas no son más que propiedades que pueden ser implementadas o no. Para ello se debe esribir una interrogación “?” al final del nombre de la propiedad:

**type** Person = {name: **string** , age?: **number** }**var** carlos2: Person = { name: "Carlos" } // Correcto.

La propiedad age es opcional y aunque no la hayamos declarado en el objeto literal no muestra ningún error.

Atención: El siguiente apartado (weak type) no es aplicable ni siquiera a la versión 1.7 del lenguaje. Se muestra aquí para dar una idea del rumbo que está tomando. Aún no hay fecha para la implementación de esta característica.

El principal problema que se plantea es qué ocurre cuando en un objeto tipo literal todas sus propiedades son opcionales. A esto se le llama un tipo débil (weak type):

**type** Person = {name?: **string** , age?: **number** }

Este tipo actúa, en un prinipio, como un objeto vacío {}

**type** Person = {name?: **string** , age?: **number** }**var** carlos: Person = {} // Correcto.

Esto que, a priori, no supone impedimento ninguno, puede ser el causante de errores en la comprobación de tipos, sobre todo cuando es un tipo de un parámetro:

**type** Person = {name?: **string** , age?: **number** }**function** foo (p:Person){}foo({}) // Correcto

Pero, como sabemos, el tipo {} está muy alto en la jerarquía de tipos en TS, por lo que casi cualquier cosa es un {}. Esto quiere decir que podríamos pasar como argumento a la función _foo_ un número, una función, etc. Realmente no es así ya que comprueba las propiedades aunque todas sean opcionales. La regla para mostrar el error es que tanto el tipo objeto literal no vacío con todas sus propiedades opcionales y el objeto que se le asigna, deben ser disjuntos, esto es que no tengan ninguna propiedad en común:

**type** Person = {name?: **string** , age?: **number** }**function** foo (p:Person){}foo(**function**(){}) // Incorrectofoo(2) // Incorrecto

El ejemplo es incorrecto porque _Function_ no tiene ninguna propiedad en común con _Person._

El segundo es incorrecto porque **number** no tiene ninguna propiedad en común con _Person_.