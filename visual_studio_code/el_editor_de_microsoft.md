## El editor de Microsoft {#el-editor-de-microsoft}

Visual Code es un IDE gratuito de reciente lanzamiento por parte de Microsoft. Su interfaz es sencilla y fácil de manejar. Aún se encuentra en fase “preview” pero es totalmente funcional y el soporte de TypeScript es completo. Para descargarlo debemos ir aquí: [https://code.visualstudio.com/](https://code.visualstudio.com/)

Para empezar, lo más recomendable es referenciar nuestra instalación de TS para que el editor pueda ayudarnos de forma eficaz.

Abrirmos la configuración de usuario:

![](image002.png)

Informando esto "typescript.tsdk". La ruta debe ser donde tengamos instalado TypeScript. En una instalación normal en Windows, la aplicación npm lo instala aquí:

![](image003.png)

"C:\\Users\\NUESTRO_USUARIO\\AppData\\Roaming\\npm\\node_modules\\typescript\\lib"

Ahora para usarlo simplemente debemos elegir una carpeta en la que trabajar:

![](image004.png)

Una vez hecho tendremos esta imagen:

![](image005.png)

Creamos un archivo de pruebas llamado app.ts y de forma automática tendremos la ayuda del IDE para TypeScript.

![](image006.png)

![](image007.png)


Creamos un archivo con extensión .html y le añadimos la etiqueta _script_ donde el _src_ sea el archivo .js, en este caso app.js.

![](image008.png)

Creamos el archivo _tsconfig.json_ el cual es necesario para configurar qué queremos compilar y cómo. Por ahora sólo añadimos que genere los _sourceMaps._

![](image009.png)

Pulsamos Control + Shift + B y nos saldrá esto:

![](image010.png)

Pulsamos en _Configure Task Runner_ y se creará un archivo _tasks.json_ dentro de la carpeta _.settings_. Éste es necesario para hacer funcionar el “transpiler”. En él sólo borramos esta línea, pues no vamos a introducir argumentos al compilador mediante comandos, sino que vamos a controlarlo con el archivo tsconfig.json.:

![](image011.png)

A partir de ahora, cada vez que pulsemos Control + Shift + B, el proyecto se compilará en JavaScript.

app.js compilado desde app.ts:

![](image012.png)

Si queremos ocultar de la lista los archivos .js y .map que se generan, debemos configurarlo.

![](image013.png)

Veremos esto:

![](image014.png)

En el archivo de la derecha añadimos:


![](image015.png)

```ts
{"files.exclude" : { 
  "**/.git" : true, 
  "/.DS_Store" : true, 
  "**/*.js" : { "when" : "$(basename).ts" }, 
  "**/*.map" : { } }
}
```

A partir de ahora los archivos .js que tengan su correspondiente .ts no se mostrarán. Además también ocultamos todos los .map.

Resumidamente, a estas alturas, en nuestro proyecto tendremos:

| index.html |
| --- |
| **app.ts** |
| **app.js** |

Si ejecutamos index.html:

![](image016.png)


