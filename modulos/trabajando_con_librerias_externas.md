## Trabajando con librerías externas {#trabajando-con-librer-as-externas}

Una de las grandes ventajas de TS es su compatibilidad con librerías escritas en JS. No es necesario reescribirlas en TS para que podamos usar sus ventajas.

Para “tipar” una librería externa se debe generar un archivo de definiciones que nos provea de las entidades para ser consumidas.

Estos archivos se usan en el caso de trabajar con la librería directamente en JS. Este archivo trabaja como una interfaz en la que se nos presenta las funcionalidades y posibilidades de la librería y se nos da la posibilidad de interactuar con ella.

En este sentido se está llevando a cabo un excelente trabajo de la comunidad para crear achivos de definiciones de cientos de librerías. Es de código libre y está alojado en Github.

[https://github.com/borisyankov/DefinitelyTyped](https://github.com/borisyankov/DefinitelyTyped)

En él podemos encontrar definiciones para librerías tan conocidas como jQuery, AngularJS etc.

Cuando creamos nuestra aplicación directamente en TS, el compilador genera un archivo de definiciones de forma automática pero esta funcionalidad es experimental y contiene aún bastantes bugs por resolver.

## Archivos de definiciones

Nosotros podemos crear nuestros propios archivos de definiciones de forma manual.

Básicamente lo que se hace es escribir en un archivo de extensión _.d.ts_ todas nuestras clases, interfaces, enums, funciones, módulos y variables que queremos publicar para que puedan ser usados.

Para ello se utiliza la palabra reservada _declare_ seguido de la entidad que sea: clase, enum, función, módulo o variable pero sin implementar, es decir, no se reescribe el cuerpo sólo su cabecera. Con las interfaces no es necesario.

```ts
declare class Person { 
  constructor(private age:number);
}
```

Así podremos usar _Persona_ en nuestra aplicación TS para instanciarla, extenderla, etc.

