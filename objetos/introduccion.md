## Introducción {#introducci-n}

Es la base de los tipos en TypeScript. Sin él no se entiende el resto. Esto es muy importante y se debe asimilar.

Es el tipo más básico de TS. Su uso se ha extendido ya que es la base de [JSON](../anexo_ii_strings/metodos.md#757309351116418-_Anexo_III._JSON).

```ts
let objeto1: Object; 
let objeto2: {}; // Objeto literal
```

Y se puede inicializar así:

```ts
let objeto = new Object();
let objeto = {};
let objeto = {clave: "valor", clave2: "valor2"}; // Las propiedades de éste ya no podrán ser otras
```

Es un [tipo dinámico](../clases/objetos_dinamicos.md). Esto quiere decir que le podemos crear más claves-valor en tiempo de ejecución.

```ts
let obj= {};
obj["key1"] = "value1";
```

Hay que tener en cuenta las claves sólo pueden ser numéricas o cadenas de caracteres. El campo valor, sin embargo, puede ser de cualquier tipo.

