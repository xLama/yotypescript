### Funciones flecha \(Expresiones lambda\) {#expresiones-lambda-funciones-flecha}

TS nos proporciona otra sintaxis a la hora de declarar una función que resulta bastante interesante, llamada funciones flecha.

Siguiendo con el ejemplo anterior, otra forma de declarar _sumar_ sería:

```ts
let example = (x: number) => {
    return 0;
};
```

Entre paréntesis se especifica la lista de parámetros seguido de : \(dos puntos\) para especificar el tipo devuelto por la función. Por último el =&gt; para definir el cuerpo de la función. Realmente no es necesario encerrarlo entre llaves {} pero si se hace debe aparecer la palabra clave _return_

Son equivalentes:

```ts
let example = (x: number): number => {
    return 0;
};
let example = (x: number) => 0;
```

Incluso podemos usar los parámetros en el cuerpo sin llaves:

```ts
let square = (x: number) => x * x;
```

En el caso de las funciones flecha la única posibilidad es la de asignarla a una variable pues su sintaxis no permite darle un nombre en la propia declaración

```ts
let funcion = (): void => { }
```

### Contexto {#contexto}

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

Pero, sin embargo, escribimos esto:

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

Funcionará correctamente. Lo que hace el compilador es referenciar el _this_ en otra variable llamada _\_this_ justo antes de la declaración del método. Cuando el método se ejecuta y hace _this.showLetter\(\)_, ese _this_ es, en realidad, el _this que antes se creó. this sí hace referencia al objeto en sí y no a window por lo que puede ejecutar this.showLetter\(\)_ sin problemas. Para entenderlo mejor es recomendable leer [este apartado.](../clases/estado_y_comportamiento.md#operador-this)

