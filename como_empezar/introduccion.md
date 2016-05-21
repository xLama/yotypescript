## Introducción {#introducci-n}

Cuando se generan los archivos .js a partir de los .ts, se deben incluir como si de cualquier otro .js se tratara. Ante una estructura de una página web básica:

```html
<html> 
  <head> 
    <title> Yo:TypeScript </title> 
  </head> 
  <body> 
  </body> 
</html>
```

Los archivos .js se incluyen dento de &lt;head&gt;&lt;/head&gt; de la siguiente forma:

```html
<script type="text/javascript" src="archivo.js"> </script>
```

Donde _src_ es la ruta hacia el archivo en cuestión.

Una vez lo tenemos, guardamos el archivo con cualquier nombre y con extensión .html. Sólo tenemos que abrirlo con cualquier navegador web para que se ejecute.

index.html

```html
<html>
  <head>
    <title> Yo:TypeScript </title> 
    <script type="text/javascript" src="archivo.js"></script> 
  </head> 
  <body> 
  </body> 
</html>
```

archivo.js

```js
alert("Probando JS");
```

_alert()_ muestra en una ventana emergente el texto que le proporcionamos.

Para sólo tener que incluir un archivo .js es preferible compilar y agrupar todo nuestro TS. Es algo que se puede hacer desde un editor de TS o manualmente desde el compilador con la consola de comandos. Para ello es necesario que las referencias sean correctas, es decir, que cada archivo .ts importe los otros .ts que necesite para funcionar. Esto se verá en el capítulo de Módulos

.