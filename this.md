### This {#operador-this}

Habrás podido ver el operador \_this \_en el tema de las clases.

Es una fuente de errores de concepto porque si bien se llama igual que en el resto de lenguajes orientados a objetos, su comportamiento no es el mismo. _this_ se refiere a la clase en sí misma donde se escribe y es la forma de referenciar a los miembros de la instancia. Si se intentara acceder a un miembro de instanciasin anteponer _this_, fallaría la compilación.

La forma de utilizarlo es la misma con la que accedemos a los métodos públicos de una clase por medio de una instancia de la misma, con _this._ \(punto\).

#### Contexto {#contexto}

El _this_ en JS funciona de una forma distinta a como lo hace en la mayoría de los lenguajes orientados a objetos pues se refiere al contexto donde se ha ejecutado en ese momento y no donde se ha declarado. Es un tema que puede traerte de cabeza si no sabes bien cómo funciona.

| Llamada | Valor de _this_ |
| --- | --- |
| **ejecutar\(\);** | Objeto al que pertenece |
| **let objeto = new Objeto\(\);** | La nueva instancia |

El operador _this_ sólo tiene sentido dentro de las funciones \(y en las clases porque como hemos visto una clase en JS es, en realidad, una función\) pues fuera de éstas su valor siempre es _window_ \(excepto en el modo estricto que sería _undefined_\). Ya una vez dentro de la función el valor de _this_ será el objeto al que pertenezca esa función en el momento de ser ejecutada. Podemos decir que las funciones son las únicas que crean nuevos contextos.

```ts
let thisExample = { 
  name: "José",
  surname: "Lama", 
  nameAndSurname: this.name +" "+ this.surname
}
thisExample.nameAndSurname // undefined undefined
```

La propiedad _nameAndSurname_ del ejemplo es _undefined undefined_ pues _this_ está referenciando a _window_ y éste no tiene las propiedades _name_ y _surname_.

En el caso de que lo usemos dentro de una función.

```ts
function thisExample(){ 
  this; // window
}
thisExample();
```

De nuevo this es _window_ porque _thisExample\(\)_ no pertenece a ningún objeto de forma explícita, por lo que es parte de _window_.

El operador _new_ cambia este comportamiento y hace que el contexto sea la instancia.

```ts
function thisExample(){ 
  this; // object. La instancia.
}
let example = new thisExample();
```

Teniendo en cuenta la primera fila de la tabla, podemos hacer esto:

```ts
let thisExample = {
    name: "José",
    surname: "Lama",
    nameAndSurname: function () {
        return this.name + " " + this.surname
    }
}
thisExample.nameAndSurname(); // José Lama
```

En esta ocasión, la función sí pertenece a un objeto de forma explícita en el momento de su ejecución por lo que ese _this_ referencia al contexto de la función, que es _thisExample, el objeto._

Algo a muy tener encuenta es lo siguiente.

```ts
let thisExample = function () {
    let name = "José";
    let surname = "Lama";
    let nameAndSurname = function () {
        console.log(this.name + " " + this.surname)
    }

    nameAndSurname();
}
thisExample()// undefined undefined
```

Si echamos un vistazo a la tabla, es de suponer que _this_ _name_ y _this.surname_, que se encuentran dentro de la función _nameAndSurname\(\),_ deberían ser correctos pues el contexto de la función es otra función superior que sí posee esas propiedades, es decir, _nameAndSurname\(\)_ pertecene a un objeto \(que en este caso es una función\). Pero esto realmente no es así. El ejemplo no funciona como parece y en su lugar muestra _undefined undefined._ La conslusión final es que las funciones crean contexto pero no pueden formar parte de él a menos que se use el operador _new. \_Esto es importante para controlar bien el contexto de las \_closures._

#### this en las funciones flecha {#this-polim-rfico}

Una función flecha conserva el contexto donde se ha declarado.

```ts
class A {
    show() {
        this.showLetter();
    }
    showLetter() {
        alert("A");
    }
}

let a: A = new A(); 
let show = a.show; 
show();
```

La ejecución fallará porque el contexto de la ejecución _show\(\)_ es _window_ por lo que asigna _this_ a _window_. _Window_ no tiene la función _showLetter\(\)_.

Pero, sin embargo, si escribimos esto:

```ts
class A {
    show = () => {
        this.showLetter();
    }
    showLetter() {
        alert("A");
    }
}

let a: A = new A();
let show = a.show;
show();
```

Funcionará correctamente. Lo que hace el compilador es referenciar el _this_ en otra variable llamada _\_this_ justo antes de la declaración del método. Cuando el método se ejecuta y hace _this.showLetter\(\)_, ese _this_ es, en realidad, el _this que antes se creó. this sí hace referencia al objeto en sí y no a window por lo que puede ejecutar this.showLetter\(\)_ sin problemas. 

Si vemos el código JS generado se ve más claro:

```js
var A = (function () {
    function A() {
        var _this = this; // Se cachea el this original al instanciarse
        this.show = function () {
            _this.showLetter(); // Este _this hace referencia siempre a la instancia por lo que nunca puede cambiar
        };
    }
    A.prototype.showLetter = function () {
        alert("A");
    };
    return A;
}());
var a = new A();
var show = a.show;
show();
```

Como vemos, _\_this _siempre es la instancia. Da igual que intentemos manipularlo, su contexto nunca va a cambiar. Esto tiene su lado bueno y su lado malo. 

El bueno es que podemos asegurar que su contexto nunca va a cambiar por lo que no habrá errores en tiempo de ejecución al respecto ya que su contexto está definido de una forma clara y concisa.

El malo es que al no ser recontextualizable, no se pueden usar como métodos para ser llamados desde una clase hija con _super_

```ts
class A {
    show = () => {
        this.showLetter();
    }
}

class B extends A {
    show = () => {
        super.show(); // Error. No reconoce super.show como método
    }
}
```

Si revisamos la herencia que existe en JS, realmente, al llamar a métodos del padre, lo que hacer es llamarlo cambiándole el contexto siendo éste la clase hija.  Como una función flecha no se puede recontextualizar, no es posible hacer esto.

#### this polimórfico {#this-polim-rfico}

Ahora  _this_ se refiere a la instancia de alguna clase que herede de la clase contenedora.

```ts
class HTMLElement { 
//...
  public setId( id: string ){ 
    this.id = id;
    return this; 
  } 
//...
}
class Div extends HTMLElement { //…
  public setWidth( width: number ){ 
    this.width = width;
    return this; 
  } 
//...
}
let div = new Div().setId("div").setWidth(5);
```

Al invocar el método _setId,_ el cual es de _HTMLElement_, lo devolvería, con lo cual, al intentar invocar _setWidth,_ y no ser éste parte de esa clase, fallaría. Precisamente ese es el comportamiento que ha cambiado. Ahora sabe que lo que devuelve _setId_ no es _HTMLElement,_ sino cualquier clase que herede de ella y que esté invocando el método en ese instante.

