## Interfaces como funciones {#interfaces-como-funciones}

Podemos usar las interfaces como definiciones de funciones.

**interface** Funcion { **** (x: **number**, y: **number**): **number**;}

Podemos tipar una variable con esa interfaz e inicializarla con una función que cumpla con la definición:

**var** func: Funcion = **function** (x: **number**, y: **number**) {**return** x * y }

Su utilidad es limitada y está orientado a la creación de archivos de definición para librerías JS.