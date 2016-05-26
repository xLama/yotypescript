## Tipos de errores {#tipos-de-errores}

Hay algunos ya predefinidos que resultan muy útiles. Cabe decir que todos heredan de _Error_.

* **_EvalError_**_:_ Indica un error al ejecutar la función global eval().

* **_RangeError_**_:_ Indica que estamos tratando de acceder a un índice que no existe. Es aplicable a los arrays y a los objecs.

* **_ReferenceError_**_:_ Indica que estamos referenciando a una variable no declarada.

* **_SyntaxError_**_:_ Indica que hay un error de sintaxis.

* **_TypeError_**_:_ Indica que estamos tratando de acceder a miembros de algo que vale _null_ o que no hemos pasado la variable con el tipo correcto como argumento.


Todos comparten una serie de atributos como el _message_, que describe el error de forma literal.

Normalmente, los navegadores modernos describen estos errores de forma automática en su consola sin necesidad de que el desarrollador lo tenga que hacer de forma explícita.