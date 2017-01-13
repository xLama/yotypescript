## Módulos externos {#m-dulos-externos}

Estos son usados normalmente junto con otras librerías como RequireJS o trabajando con Node.js. La idea es que la carga sea bajo demanda, es decir, sólo cuando lo necesitemos.

Cuando escribimos código TS, podemos vernos en la situación en la que dupliquemos nombres de clases, interfaces, variables, etc. Aunque lo declaremos en archivos distintos, el compilador nos lo advertirá. Sin embargo, al usar módulos externos, y para ello sólo hay que declarar una exportación o una importación, el compilador aislará ese archivo, evitando así polucionar el ámbito general de la aplicación.



