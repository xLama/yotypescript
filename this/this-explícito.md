## This explícito

Es lógico que TS no pueda deducir el valor de _this teniendo en cuenta lo manipulable que puede llegar a ser. Una forma de controlarlo es especificando de forma explícita el tipo de this_. Es tan fácil como declarar una función con un parámetro llamado _this_ del tipo que creamos conveniente.

```ts
function otherThis(this:number){
    this; // Es un number
}
```

Esto no quiere decir que por arte de magia su contexto sea el que especifiquemos, es evidente. Esto sirve para que podamos verlo fácilmente a la vez que podamos exprimir las herramientas de autocompletado del editor.

¿Y para qué podemos usar esto realmente? Tiene su lógica si activamos noImplicitThis en el tsconfig.json. Con esto el compilador \_nos avisa de los this que no tienen un valor específico, sino que suelen ser Any.

```ts
class A {
    foo() {
        this;
        return function () {
            this; // Error. this es any
        }
    }
}
```

¿Por qué es _Any_? El primer _this es la propia clase y eso lo tiene controlado. El problema viene con el segundo this. Como recordamos de temas anteriores, el contexto de una función que está dentro de otra función es window o undefined. Por ello nos avisa. Para arreglar esto necesitamos especificar el tipo del this._

```ts
class A {
    foo() {
        this;
        return function (this : A) {
            this; // Ok. this es del tipo A
        }
    }
}
```

Ahora no produce error. Una cosa a tener en cuenta es que si en algún momento el contexto de esa función no es el tipo _A_, la ejecución fallará si referenciamos una propiedad de _this \_que no tenga_ A.\_

```ts
class A {
    bar = "bar"
    foo() {
        this;
        return function (this: A) {
            console.log(this.bar);
        }
    }
}

class B {
    name;
}

let a = new A();
let foo = a.foo().bind(new B());
foo(); // es undefined pues lo hemos recontexualizado a una instancia de B
```

Esto no ocurre si usamos de forma adecuada las funciones flecha.

```ts
class A {
    bar = "bar"
    foo() {
        this;
        return () => {
            this.bar; // Ok
        }
    }
}
```

Y es así porque una función flecha conserva el contexto donde se ha declarado. En este caso su contexto es la instancia y eso no cambiará nunca por lo que TS infiere que _this \_es del tipo_ A.\_

