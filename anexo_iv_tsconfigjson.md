# Anexo IV. tsconfig.json {#anexo-iv-tsconfig-json}

tsconfig.json es un archivo en formato JSON que contiene un objeto que a su vez contiene propiedades usadas por el compilador para configurarse. Si bien no es obligatorio ya que se podrían usar los parámetros por efecto, es muy recomendable su uso ya que en cada nueva versión de TS sus posibilidades van aumentando dándonos así una gran flexibilidad.

El esquema de este archivo lo podemos encontrar aquí:

[http://json.schemastore.org/tsconfig](http://json.schemastore.org/tsconfig)

Un prototipo básico sería como sigue:

```json
{
  "compilerOptions" : {}, 
  "files" : [],
  "exclude" : []
}
```

_files_ no es más que un array de los archivos .ts que queremos que se compilen.

_exclude_ es un array de archivos .ts que no queremos que se incluyan en la compilación. _files_ y _exclude_ no pueden estar a la vez declarados.

Se pueden escribir comentarios con la misma sintaxis que TypeScript/JavaScript.

La verdadera configuración se realiza en _compilerOptions_:

| Parámetro | Descripción | Tipo |
| --- | --- | --- |
| charset | El juego de caracteres de los archivos a compilar. | _string_ |
| declaration | Si queremos generar el archivo de definición d.ts | _boolean_ |
| emitBOM | Especifica si debe generar los archivos .js con BOM al comienzo. | _boolean_ |
| listFiles | Imprime en la consola los archivos compilados. | _boolean_ |
| locale | Idioma de los errores de compilación | _string_ |
| mapRoot | Directorio donde generar los .maps | _string_ |
| module | Tipo de módulos externo. | _enum : “commonjs”, “amd”, “umd”, “system” ,“es6”_ |
| noEmit | Especifica si se deben crear los archivos .js al compilar. | _boolean_ |
| noEmitError | Especifica si debe generar los archivos .js si ocurre algún error en el proceso. | _boolean_ |
| noImplicitAny | Especifica si todo ha de estar tipado. En caso contrario da un error de compilación. | _boolean_ |
| noLib | Especifica si incluir el archivo de definiciones lib.s.ts. | _boolean_ |
| noLibCheck |  |  |
| noResolve | Especifica si debe resolver las rutas de los archivos referenciados mediante /// | _boolean_ |
| out | Compila todo los .ts en un solo .js | _string_ |
| outDir | Directorio donde generar los archivos .js | _string_ |
| preserveConstEnums | Genera el JS correspondiente como si no fuera un enum constante | _boolean_ |
| removeComments | Especifica si los archivos .js se deben generar con comentarios. | _boolean_ |
| sourceMap | Especifica si debe generar los archivos .map | _boolean_ |
| sourceRoot | Directorio donde el depurador debe buscar los archivos .ts | _string_ |
| suppressImplicitAnyIndexError | Especifica si debe suprimir los errores de any implícito en los objetos indizados. noImplicitAny debe estar activo para que tenga efecto. | _boolean_ |
| target | Versión de ECMAScript de la compilación | _“ES3”, “ES5”, “ES6”_ |
| watch | Especifica si se debe compilar al guardar los cambios. | _boolean_ |
| newLine | Final de secuencia usada en los archivos .js generados. | _"CRLF", "LF"_ |
| noEmitHelpers | Especifica si debe generar el código .js que sirve de ayuda en distintas implementaciones. Un ejemplo claro es __extends usado para realizar la herencia. | _boolean_ |
| inlineSourceMap | Especifica si debe generar el contenido de los .maps dentro del propio archivo .js | _boolean_ |
| inlineSources |  |  |
| emitDecoratorMetadata | Especifica si debe generar el decorador __metadata al usar decoradores. | _boolean_ |
| experimentalDecorators | Especifica si se pueden usar los decoradores, aún en fase experimental. | _boolean_ |
| isolaredModules | Especifica si debe generar los archivos .js aunque no pueda resolver la importación del módulo. | _boolean_ |
| rootDir | Directorio donde se encuentran los archivos .ts a compilar. | _string_ |
| project | Directorio donde se encuentran los archivos .ts a compilar. | _string_ |
| experimentalAsyncFunctions | Especifica si se pueden usar las function asíncronas. | _boolean_ |
| jsx | Especifica el modo de generación del código jsx. | _enum : “preserve”,”react”_ |
| suppressExcessPropertyErrors | Especifica si debe suprimir la comprobación de exceso de propiedades en los objetos literales | _boolean_ |
| noImplicitReturns | Especifica si se debe declarar returns en todos los casos | _boolean_ |
| allowUnreachableCode | Especifica si se permite código inalcanzable. | _boolean_ |
| noImplicitUseStrict | Especifica si debe emitir \"use strict\" en los módulos. | _boolean_ |
| allowSyntheticDefaultImports | Especifica si un módulo sin una exportación por defecto puede ser importado como tal. | _boolean_ |
| allowJS | Especifica si se permiten compilaciones JavaScript. | _boolean_ |
| noFallthroughCasesInSwitch |  | _boolean_ |
| allowUnusedLabels |  | _boolean_ |

Imagen de cómo quedaría un tsconfig.json: