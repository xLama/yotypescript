## Document {#document}

### Seleccionar elementos {#seleccionar-elementos}

Podemos referenciar elementos con variables fácilemente. De esa forma podmos manipularlos directamente desde la variable pues representa al elemento en cuestión.

#### getElementById() {#getelementbyid}

Seleccionar el elemento cuyo atributo id coincida con el proporcionado como argumento.

```ts
let div = document.getElementById("capa");
```

La variable _div_ queda tipada con _HTMLElement_ porque no es posible que por inferencia se tipe la variable _div_ de forma exhaustiva. Para ellos debemos hacer una conversión si conocemos qué elemento posee ese id.

```ts
let div =  document.getElementById("capa") as HTMLDivElement;
```

No todos los elementos tienen su propia interfaz. Algunos deben tiparse con _HTMLElement_.

#### getElementsByTagName() {#getelementsbytagname}

Selecciona todos los elementos que coincidan con el nombre de la etiqueta proporcionada como argumento.

```ts
**var** divs = document.getElementsByTagName("div");
```

Es una función especializada porque introduciendo “div” como argumento el tipo devuelto es _NodeListOf&lt;HTMLDivelement&gt;_

Devuele un _NodeListOf&lt;T&gt;_ que podemos recorrer con bucles somo si de un array se tratara.