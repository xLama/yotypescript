## Introducción {#introducci-n}

Cuando se generan los archivos .js a partir de los .ts, se deben incluir como si de cualquier otro .js se tratara. Ante una estructura de una página web básica:

&lt;html&gt; &lt;head&gt; &lt;title&gt;**Yo:TypeScript**&lt;/title&gt; &lt;/head&gt; &lt;body&gt; &lt;/body&gt;&lt;/html&gt;

Los archivos .js se incluyen dento de &lt;head&gt;&lt;/head&gt; de la siguiente forma:

<script type=**"text/javascript"** src=**"archivo.js"**> &lt;/script&gt;

Donde _src_ es la ruta hacia el archivo en cuestión.

Una vez lo tenemos, guardamos el archivo con cualquier nombre y con extensión .html. Sólo tenemos que abrirlo con cualquier navegador web para que se ejecute.

index.html

&lt;html&gt; &lt;head&gt; &lt;title&gt;**Yo:TypeScript**&lt;/title&gt; <script type=**"text/javascript"** src=**"archivo.js"**> &lt;/script&gt; &lt;/head&gt; &lt;body&gt; &lt;/body&gt;&lt;/html&gt;

archivo.js

alert(“Probando JS”);

_alert()_ muestra en una ventana emergente el texto que le proporcionamos.

Para sólo tener que incluir un archivo .js es preferible compilar y agrupar todo nuestro TS. Es algo que se puede hacer desde un editor de TS o manualmente desde el compilador con la consola de comandos. Para ello es necesario que las referencias sean correctas, es decir, que cada archivo .ts importe los otros .ts que necesite para funcionar. Esto se verá en el capítulo de

Módulos

.