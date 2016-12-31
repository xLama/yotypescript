## Cómo tipar {#variables-con-tipo}

Un tipo identifica lo que almacena una variable. No es lo mismo un número que una letra.

Las variables en TS son estáticamente tipadas. Esto quiere decir que a la hora declararlas podemos especificar qué tipo de datos contienen. La sintaxis es la siguiente:

```ts
let variable: tipo;
```

Podemos obviarlo ya que si no lo hacemos se hará de forma automática por [inferencia](inferencia_de_tipos.md). Mi recomendación es que sólo se haga cuando la inferencia no pueda. Esto sigue la filosofía "no te repitas" \(don´t repeat yourself\).

Todos los tipos provienen de uno superior llamado _Any_. El tipo _Any_ se refiere a cualquier cosa. Si declaramos una variable sin tipar sería lo mismo que hacerlo con _Any_.

```ts
let variable: any;
let variable;
```

Esto hará que podamos asignarle cualquier dato: numérico, caracteres, etc.

