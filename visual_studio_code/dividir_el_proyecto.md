## Dividir el proyecto {#dividir-el-proyecto}

Es evidente que si creamos nuestras clases, interfaces, etc, no lo vamos a hacer en el mismo .ts, sino que, como es lo normal en la programación orientada a objetos, cada clase esté en un archivo único. Por ello, ante esta hipotética estructura:

app.ts clase.ts

Si en app.ts usamos clase.ts, lo [referenciaremos de la forma adecuada](../modulos/un_mismo_modulo_en_distintos_archivos.md) en app.ts. A la hora de compilar TS todo se concentrará en un único archivo .js. Esto haría que por cada página donde queramos añadir código tendríamos compilar el código específico para esa página junto con todas las utilidades que hayamos creado. No es recomendable porque rompe totalmente con la filosofía de la reutilización. Lo mejor es hacer un proyecto TS donde tengamos todas nuestras creaciones y sea el resultado de ello lo que usemos en cada página.

A modo de ejemplo:

| pagina1.html | pagina2.html |
| --- | --- |

Imagina que tenemos dos páginas con esos nombres donde queremos añadir código JS. Creamos un archivo .ts por cada una (y su .js):

| pagina1.html | pagina2.html |
| --- | --- |
| **pagina1.ts** | pagina2.ts |
| **pagina1.js** | pagina2.js |

Si en cada .ts hemos usado nuestras propias clases, interfaces, etc, lo añadimos a modo de librería:

| pagina1.html | pagina2.html |
| --- | --- |
| **libreria.js** | libreria.js |
| **libreria.d.ts** | libreria.d.ts |
| **pagina1.ts** | pagina2.ts |
| **pagina1.js** | pagina2.js |

De esta forma usaremos nuestra propia [librería como externa](../modulos/trabajando_con_librerias_externas.md), mediante el archivo de definiciones. Así conseguimos reutilizarla en todas las páginas que queramos y separaremos el código específico de cada una.