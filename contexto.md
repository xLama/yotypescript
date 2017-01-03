## Contexto

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

