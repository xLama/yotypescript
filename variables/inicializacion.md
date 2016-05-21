## Inicialización {#inicializaci-n}

Inicializar una variable es asignarle un valor. En TS las variables no se inicializan de forma automática como en otros lenguajes de programación donde, por ejemplo, las de tipo numérica se inicializan con el valor 0 si no le establecemos un valor explícitamente.

**var** variable; **/* undefined */**

Esto es importante porque, por ejemplo, si intentamos hacer operaciones matemáticas con una variable no inicializada, el resultado será NaN (not a number).

Para inicializarla se usa el [operador de asignación](../operadores/operadores_binarios.md#operador-de-asignaci-n) _=_.

**var** variable1 = 89;**var** variable2 = "esto es una variable";