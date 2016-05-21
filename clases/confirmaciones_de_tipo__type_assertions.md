## Confirmaciones de tipo ( Type Assertions ) {#confirmaciones-de-tipo-type-assertions}

Siguiendo con el ejemplo anterior, podemos hacer que la variable _ser_ se convierta en un _Alumno_ para poder ejecutar todo lo que _Alunno_ implementa y _SerVivo_ no, porque en la invocación de la función introdujimos como argumento un _Alumno_. Ocurre que sintácticamente no tenemos disponible los métodos de _Alumno_ porque el parámetro de la función es del tipo _SerVivo,_ por lo que hay que forzarlo.

**function** ejemplo(ser: SerVivo): **void** { **var** alumno: Alumno = &lt;Alumno&gt;ser;}

A esto se le llama _type assertion_ (es conceptualmente parecido a los _castings_ o conversiones de tipo disponibles en otros lenguajes) y consiste en convertir un tipo en otro siempre y cuando estén relacionados.

**interface** A { }**interface** B **extends** A { }**class** C **implements** B { }**function** conversion(casting: A): **void** { **var** c: C = &lt;C&gt; casting; // Equivalente var c : C = casting as A}

conversion (**new** C());

Los _type assertions_ se hacen encerrando el tipo al que queremos convertir entre &lt;&gt; seguido de la variable que queremos convertir o con la sentencia **as**

En el caso en el que queramos usar un método del tipo de la variable a la que queremos convertir directamente sin asignarlo a otra variable tenemos que usar los paréntesis.

**class** C{**** hacer(): **void** { }****}**function** convertir(casting: A): **void** { **** (&lt;C&gt; casting).hacer();}

convertir(**new** C());

Como TS se basa en el [tipado estructural](../genericos/comparando_genericos.md#757309351116418-_Tipado_estructural), es posible hacer conversiones de tipos que no tengan relación declarativa pero sean estructuralmente análogos.

**class** A{ **public** mostrarA():**void**{ **** alert("A"); }****}

**class** B{ **public** mostrarA():**void**{ **** alert("A");}

**public** mostrarB():**void**{ **** alert("B"); }****}

**function** mostrarLetra(letra:A):**void**{ **** (&lt;B&gt;letra).mostrarB();}

mostrarLetra(**new** B());

El código perfectamente válido y se ejecuta sin problemas. El parámetro del tipo _A_ de la función _mostrarLetra_ acepta como parámetro un objeto del tipo _B_ porque _B_ tiene todo lo de _A_. A partir de ahí B puede implementar todos los métodos que quiera.