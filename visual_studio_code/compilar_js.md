## Compilar JS {#compilar-js}

Otra de las características útiles es poder compilar los archivos JavaScript. Esto sirve para poder mover los archivos junto con los compilados de TS. Además permite pasar el código JS de una versión de ES a otra (más baja). Para hacerlo es necesario que se configure el compilador con el parámetro _allowJS_. Además es obligatorio usar también _out_ para que el destino sea otro directorio. Es lógico ya que de otra forma los archivos JS compilados reemplazarían los originales.

Con ello podemos trabajar con JavaScript y tener ciertas ventajas como información adicional de tipos si están declarados como comentario:

Además permite transpilar código de ES6 a ES5 o ES3.this