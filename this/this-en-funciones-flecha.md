## This en las funciones flecha

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

Como vemos, \_this siempre es la instancia. Da igual que intentemos manipularlo, su contexto nunca va a cambiar. Esto tiene su lado bueno y su lado malo.

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

