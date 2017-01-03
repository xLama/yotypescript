## Eventos visuales {#eventos-visuales}

En el estándar de la w3c estos eventos siguen un camino determinado.Imagina que tenemos un enlace _A_ dentro de un _Div_ y éste dentro del _Body_.

Body

Div

A Div Body

A

### Fase de captura {#fase-de-captura}

Cuando el usuario pulsa el enlace, un evento del tipo _click_ es lanzado desde el punto más alto de la jerarquía del enlace. El punto más alto de esta jerarquía siempre es window.

window document html body div

Su forma de propagación es lineal. De esta forma va recorriendo todos esos elementos uno tras otro.

### Fase de objetivo {#fase-de-objetivo}

El evento llega a quien lo disparó, en este caso el enlace.

### Fase de burbuja {#fase-de-burbuja}

El evento vuelve hacia _window_ por el mismo camino que llegó pero en sentido contrario.

Div body html document window

### Añadir respuesta a los eventos. {#a-adir-respuesta-a-los-eventos}

Cuando un evento se va propagando por los distintos elementos y fases, se van ejecutando los _handlers_ que tiene asociados.

Seguimos con nuestro enlace. Suponiendo que hemos guardado su referencia en una variable de nombre _enlace_, la forma de añadir una respuesta a un evento determinado sería añadiendo lo que se denomina _listener_ \(oyente\):

```ts
enlace.addEventListener(tipoEvento:string, handler:Function, captura:boolean);
```

El tipo de evento es un _string_, en este caso podría ser _click_. El _handler_ es la función que se ejecutará cuando el evento llegue al enlace. _Captura_ es un _boolean \_que determina si el \_handler_ se va a ejecutar en la fase de captura.

```ts
enlace.addEventListener("click", respuestaClick, true);
function respuestaClick(evt: Event) {
    alert("enlace");
}
```

Puedes registrar tantos como quieras para el mismo evento o para otros pero debes tener en cuenta que los _listeners_ se registran en orden.

Cada vez que pulsemos, saltará una ventana con el texto “Pulsado”.

Podemos hacer que se ejecuten _handlers_ asociados a elementos de la jerarquía del botón durante el camino de este evento. Suponiendo que el div que contiene al botón lo hemos referenciado mediante una variable llamada _capa_…

```ts
capa.addEventListener("click", respuestaClickCapa, true);
enlace.addEventListener("click", respuestaClickBoton, true);
function respuestaClickCapa(evt: Event) {
    alert("capa");
}
function respuestaClickBoton(evt: Event) {
    alert("botón");
}
```

Como hemos visto, al hacer _click_ sobre el botón el evento recorre el camino que va desde _window_ al propio botón. _Capa_ contiene a _enlace_ por lo que se le notificará el evento _click_. Como hemos asociado un _handler_, en el momento en el que pulsemos el botón, se ejecutará _respuestaClickCapa_ en primer lugar y _respuestaClickBoton_ en segundo lugar. ¿Por qué? Porque al añadir el _listener_, pasamos true como argumento a _capture_ que quiere decir que se ejecutará en la fase de captura. Recordemos que la fase de captura es anterior a la de objetivo.

Si en vez de pasar true, hubiéramos pasado false, primero se ejecutaría el _handler_ de _botón_ y después el de _capa_ pues la fase de burbuja es posterior a la de objetivo.

### Parámetros de los handlers {#par-metros-de-los-handlers}

Las funciones que se ejecutan en respuesta a algún evento pueden tener en su definición un parámetro del tipo _Event_. En nuestro ejemplo sería del tipo _MouseEvent_.

```ts
enlace.addEventListener("click", respuestaClickBoton, true);
function respuestaClickBoton(evt: MouseEvent) {
    alert("enlace");
}
```

El argumento es pasado por el motor de eventos del navegador sin que nosotros tengamos que intervenir.

Resulta de gran ayuda pues contiene información muy valiosa y, a la vez, permite influir sobre el evento.

### Target y currentTarget {#target-y-currenttarget}

Una de las propiedades más útiles de un objeto del tipo _Event_ \(y todos sus hijos\) es _target_ y _currentTarget_.

_Target_ es el elemento que disparó el evento y _currenTarget_ es el elemento por donde está pasando el evento en esos momentos.

```ts
capa.addEventListener("click", respuestaClickCapa, true);
enlace.addEventListener("click", respuestaClickEnlace, true);
function respuestaClickCapa(evt: Event) {
    evt.target // Es el enlace pues es quien disparó el vento
    evt.currentTarget // Es el div capa, pues es por donde está pasando el evento 
}
function respuestaClickEnlace(evt: Event) {
    evt.target // Es el enlace pues es quien disparó el evento
    evt.currentTarget // Es el botón, pues es por donde está pasando el evento
}
```

Como habrás podido observar, _target_ y _currentTarget_ son el mismo elemento cuando el evento llega al quien lo disparó.

Esas dos propiedades son del tipo _node_ al que podemos hacer un _casting_ para convertirlos en el elemento del tipo original.

```ts
function respuestaClickCapa(evt: Event) {
    let capa = <HTMLDivElement>evt.currentTarget;
}
```

### El uso del this {#el-uso-del-this}

Cuando se ejecuta un _handler_ en respuesta a un evento, _this_ referencia al elemento al que se le registró el _listener_.

```ts
function respuestaClickBoton(evt: Event) {
    // Aquí this sería igual a evt.target
}
```

Eso supone un problema importante si se registran métodos de un objeto donde se invoquen otros métodos del propio objeto.

```ts
class A {
    respuesta() {
        this.algo();
    }
    algo() { }
}
var a: A = new A();
enlace.addEventListener("click", a.respuesta, true);
```

Cuando se pulse _enlace_, se ejecutará _a.respuesta\(\)_ que en su implementación llama a _this.algo\(\)_. El problema es que esto fallará porque ese _this_ no hará referencia a la instancia, sino que será _enlace_.

Para evitarlo se deben usar [expresiones lambda.](../funciones/funciones_anonimas.md#expresiones-lambda-funciones-flecha)

En JS es común usar el _this_ para trabajar con quien disparó el evento. Mi recomendación es que siempre se usen las propiedades _target_ y _currentTarget_ que nos proporciona _Event_.

### Parar la propagación de un evento {#parar-la-propagaci-n-de-un-evento}

En cada _handler_ que se ejecuta se puede parar la propagación del evento y hacer que deje de seguir su curso natural. Para ello ejecutamos el método _stopPropagation\(\)_ de _Event_.

```ts
capa.addEventListener("click", respuestaClickCapa, true);
enlace.addEventListener("click", respuestaClickEnlace, true);
function respuestaClickCapa(evt: Event) {
    evt.stopPropagation();
}
function respuestaClickEnlace(evt: Event) {
    // No se ejecuta
}
```

_capa_ tiene asociado un _listener_ en captura por lo que se ejecutará antes que el de _enlace_. Si en la función de respuesta ejecutamos el método _stopPropagation\(\)_ del evento disponible como parámetro, éste interrumpirá su camino y nunca llegará a _enlace_.

### Parar la propagación hacia otros listeners del mismo elemento y evento {#parar-la-propagaci-n-hacia-otros-listeners-del-mismo-elemento-y-evento}

Si _stopPropagation\(\)_ para la propagación del evento totalmente, _stopInmediatePropagation\(\)_ sólo evita la ejecución de otros _handlers_ del mismo tipo de evento y elemento.

```ts
capa.addEventListener("click", respuestaClickCapa, true);
capa.addEventListener("click", respuestaClickCapa2, true);
enlace.addEventListener("click", respuestaClickEnlace, true);
function respuestaClickCapa(evt: Event): void {
    evt.stopImmediatePropagation();
}
function respuestaClickCapa2(evt: Event): void { }
function respuestaClickEnlace(evt: Event): void {
    // No se ejecuta
}
```

Hemos registrado dos _handlers_ para el mismo evento en el mismo elemento, _capa_. Como vimos antes, los _handlers_ se ejecutan en el orden en el que se registraron por lo que al hacer _click_ en boton se ejecutará primero _respuestaClickCapa\(\)._ En esa función hemos invocado el método _stopInmediatePropagation\(\)_ del objeto del tipo _Event_ que ha entrado por parámetro. Eso no evita que el evento se siga propagando hacia los demás elementos visuales, sino que se consigue que los otros _handlers_ registrados del mismo evento para el mismo elemento no se ejecuten. En este ejemplo no se ejecutaría _respuestaClickCapa2\(\)._

