## Variables con tipo {#variables-con-tipo}

Un tipo identifica lo que almacena una variable. No es lo mismo un número que una letra.

Las variables en TS son estáticamente tipadas. Esto quiere decir que a la hora declararla podemos especificar qué tipo de datos contiene. La sintaxis es la siguiente:

**var** variable: tipo;

Podemos obviarlo ya que si no lo hacemos se hará de forma automática por [inferencia](inferencia_de_tipos.md). Mi recomendación es que se haga para aproximarnos a la forma de trabajar de muchos otros lenguajes.

Todos los tipos provienen de uno superior llamado A_ny_. El tipo A_ny_ se refiere a cualquier cosa. Si declaramos una variable sin tipar sería lo mismo que hacerlo con **any**.

**var** variable: **any**;**var** variable;

Esto hará que podamos asignarle cualquier dato: numérico, caracteres, etc.