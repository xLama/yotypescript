## Acceso a los atributos {#acceso-a-los-atributos}

Desde las propias variables que hacen referencia a los elementos del DOM se puede acceder a los atributos.

**var** enlace = &lt;HTMLAnchorElement&gt; document.getElementById("enlace");enlace.href = "http://www.google.es";

La clase _HTMLAnchorElement_ posee un atributo llamado _href_ que almacena la dirección hacia donde se debe navegar una vez se ha pulsado en el enlace. De esta forma podemos asignársela o modificarla de forma dinámica.

Los estilos también se pueden modificar con el atibuto style.

enlace.style.textDecoration = "none";

De esta forma eliminamos el subrayado característico de los enlaces.