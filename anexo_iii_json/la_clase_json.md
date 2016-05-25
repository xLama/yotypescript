## La clase JSON {#la-clase-json}

### De JSON a JS {#de-json-a-js}

Es útil cuando trabajamos con Ajax y recibimos la respuesta del servidor en JSON. Ésta no es reconocible directamente por JS pues es una cadena de caracteres. Para convertir esa cadena en una estructura de datos real debemos usar _JSON.parse()_

Es un método estático al que se le pasa como argumento el string que queremos convertir.

```ts
JSON.parse('{}'); // {}
JSON.parse('false'); // false
JSON.parse('"algo"'); // "algo"
JSON.parse('[10, 5, "false"]'); // [1, 5, "false"]
JSON.parse('null'); // null
```

### De JS a JSON {#de-js-a-json}

Si queremos enviar datos en formato JSON al servidor o a cualquier otra aplicación que los acepte, debemos convertir nuestra estructura en un **string** que esté bien formado para que la otra parte pueda reconocerlo sin problemas. Se hace con JSON.stringify()

```ts
JSON.stringify({});// '{}'
JSON.stringify(true); // 'true'
JSON.stringify("cadena"); // '"cadena"'
JSON.stringify([1, "false", false]); // [1,"false",false]'
JSON.stringify({ x: 5 }); // '{"x":5}'
```

Ambas poseen un segundo parámetro del tipo _function_ que es opcional y su definición es la siguiente:

(key:any, value:any) => any

La función tiene como parámetros el índice y el valor de ese índice. Y debe devolver algo. Lo que hace es sustituir el valor correspondiente por uno que queramos.

```ts
let products: string; // Es el JSON de ejemplo de este anexo.

function sustituir(key:string, value:any){ 
  if (key === "modeloA"){
    return 200; 
  } else { 
    return value; 
  }
}
let datosProductos = JSON.parse(productos, sustituir);
```

Hemos sustituido el precio del _modeloA_ a 200.