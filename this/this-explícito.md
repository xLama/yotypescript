## This explícito

Es lógico que TS no pueda deducir el valor de this teniendo en cuenta lo manipulable que puede llegar a ser. Una forma de controlarlo es especificando de forma explícita el tipo de this. Es tan fácil como declarar una función con un parámetro llamado this del tipo que creamos conveniente.

```ts
function otherThis(this:number){
    this; // Es un number
}
```

Esto no quiere decir que por arte de magia su contexto sea el que especifiquemos, es evidente. Esto sirve para que podamos verlo fácilmente a la vez que podamos exprimir las _herramientas _de autocompletado del editor.

¿Y para qué podemos usar esto realmente? Tiene su lógica si activamos \_noImplicitThis \_en el tsconfig.json. Con esto el compilador nos avisa de los this que no tienen un valor específico, sino que suelen ser Any.

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

¿Por qué es Any? El primer this es la propia clase y eso lo tiene controlado. El problema viene con el segundo this. \_Como recordamos de temas anteriores, el contexto de una función que está dentro de otra función es \_window \_o \_undefined. Por ello nos avisa. Para arreglar esto necesitamos especificar el tipo del this.

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

Ahora no produce error. Una cosa a tener en cuenta es que si en algún momento el contexto de esa función no es el tipo A, la ejecución fallará si referenciamos una propiedad de \_this \_que no tenga A.

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

Y es así porque una función flecha conserva el contexto donde se ha declarado. En este caso su contexto es la instancia y eso no cambiará nunca por lo que TS infiere que this es del tipo A.

