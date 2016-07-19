## Clase de utilidad {#clase-de-utilidad}

En este tema vamos a hacer una sencilla clase llamada *Ajax* para manejar las peticiones de una forma más versátil.

Como hemos dicho es imprescindible usar la clase *XMLHttpRequest* para realizar peticiones al servidor.

```ts
class Ajax { 
  private xmlR: XMLHttpRequest;
}
```

Los métodos de interacción los vamos a hacer estáticos para evitar instanciar la clase _Ajax_ de forma manual cada vez que queramos usarla.

```ts
class Ajax {
    private xmlR: XMLHttpRequest;
    private success: (data: any) => void;

    private static init = () => {
        var ajax = new Ajax();
        ajax.xmlR = new XMLHttpRequest();
        ajax.xmlR.addEventListener("readystatechange", ajax.onReadyState, true);
        return ajax;
    }
}
```

En el método instanciamos la clase _Ajax_.Inicializamos el atributo privado _xmlR_. Aunque sea privado es accesible porque estamos dentro de la clase.Registramos el _listenener_ con el evento _readystatechange_ que es el que se lanza cuando hay alguna noticia de la comunicación. El _handler_ utilizado es _onReadyState_ que veremos después.

Ajax tiene dos formas de comunicarse con el servidor: _post_ y _get_. Normalmente se utiliza _post_ por ser más seguro. El servidor recibiría los datos por _get_ en forma de parámetros en la url. Vamos a hacer sólo el _Post_ para simplicar el tema.

```ts
public static post = (url: string, success?: (data: any) => void): void => {
    let ajax = Ajax.init();
    ajax.success = success;
    ajax.xmlR.open("post", url, false);
}
```

Es estático público para que el programador pueda usarlo sin problemas. Por parámetro tenemos:

La url hacia donde se hará la petición y la fuunción de nombre _success_ que se ejecutará si todo ha ido bien, la cual se guarda en la instancia.

En el cuerpo del método se instancia la clase _Ajax_ a través de _init()_Asignamos la función _success_ al atributo de la instancia. Abrimos la comunicación con el servidor.

Para controlar la comunicación nos falta el método _onReadyState()_

```ts
private onReadyState = (evt: Event) => {
    let xmlR: XMLHttpRequest = this.xmlR;
    switch (xmlR.readyState) {
        case 4: 
          if (xmlR.status == 200) {
              this.success(xmlR.responseXML);
          }
          else if (xmlR.status == 404) { }

          else if (xmlR.status == 500) { }
         break;
    }
}
```

Recuperamos el objeto _XMLHttpRequest_ que hemos usado para la petición. Cabe decir que este método va a ejecutarse varias veces en todo el proceso pues se lanzarán varios eventos distintos. Por ello hemos hecho un _switch_ con _xmlR.readyState_ que es donde se almacena el estado de la petición. En 4 indica que ya ha sido procesado aunque debemos inspeccionar el valor de _xmlR.status_. 200 es el indicador de que todo ha ido bien. Si es así procedemos a ejecutar la función _success_ pasándole como argumento los datos obtenidos los cuales hemos supuesto que son XML. Si es texto plano o JSON se haría con _xmlR.responseText._

Esta clase es muy mejorable. Por ejemplo, usando _enums_ para el _readyState_, creando el método para peticiones _get_, etc. Dejo en tus manos el mejorarla con los conocimientos que has adquirido.