## Funciones genéricas {#funciones-gen-ricas}

No sólo las clases o interfaces pueden ser genéricas, las funciones o métodos también.

La mecánica es la misma:

**function** arrayDeObjetos&lt;T&gt;(c: T, a?: T[]): T[] { **** a = a || **new** Array&lt;T&gt;(); a.push(c); **return** a;}

Para invocarla se hace de la misma forma.

**var** autos : Automovil[] = arrayDeObjetos &lt;Automovil&gt; (**new** Automovil());