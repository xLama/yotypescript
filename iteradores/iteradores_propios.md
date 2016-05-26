## Iteradores propios {#iteradores-propios}

Para crearnos uno lo primero que debemos tener en cuenta es que se debe llamar Symbol.iterator, de otra forma no funcionaría.

Si queremos hacer iterable un número (primero hay que pensar si es lógico y cómo se dede interar pues lo vamos a implementar nosotros), debemos añadir el método anterior al prototype de Number:

```ts
Number.prototype[Symbol.iterator] = function(){}
```

Para este iterador vamos a hacer que recorra el número (sólo la parte entera) de derecha a izquierda, devolviendo cada uno de los dígitos por separado. Para ello lo que hay que hacer es que el método devuelva un objeto que contenga una función llamada _next()_ y ésta a su vez debe devolver un objeto literal con la siguiente estructura:

type iteratorReturn = 

```ts
{value: any, done : boolean }
```

Las propiedades _value_ y _done_ hacen referencia al valor que queremos iterar y a la terminación de la iteración, respectivamente:

```ts
interface Number {
    [Symbol.iterator]();
}

Number.prototype[Symbol.iterator] = function () {
    let num = parseInt(this.valueOf()).toString();
    var index = num.length;
    return {
        next: function () {
            if (index >= 0) {
                index -= 1;
                return { value: num.charAt(index), done: false };
            }
            return { value: undefined, done: true };
        }
    }
}

var num = 2387;

for (var n of num) {
    console.log(n); // {7, 8, 3, 2} 
}
```

De esta forma podemos recorrer los números con for-of ya que hemos creado nuestro propio método _Symbol.iterator_. Explicación del ejemplo paso por paso:

```ts
/* Ampliamos la interfaz Number con el nuevo método.
*/
interface Number {
    [Symbol.iterator]();
}

/* Implementamos el método */
Number.prototype[Symbol.iterator] = function () {
    /* Guardamos el número parseado a entero y pasado a string para un manejo más fácil */
    let num = parseInt(this.valueOf()).toString();
    /* Guardamos el principio de la iteracción. En este caso empezamos desde el final del string que representa al número */
    let index = num.length;
    /* Empezamos a devolver. Es un objeto con una función next dentro */
    return {
        next: function () {
            /* Sólo iteramos cuando el índice sea mayor o igual que 0 porque un string no tiene índices negativos */
            if (index >= 0) {
                /* Restamos uno al índice. Recordemos que los índices empiezan en 0 y que si usáramos la longitud del string como índide estaríamos accediendo a una posición vacía */
                index -= 1;
                /* Devolvermos un objeto con una propiedad _value_ que no es más que el carácter al que accedemos usando el _index_, y otra propiedad _done_ para determinar si hemos llegado al final de la iteracción. Como no es así, es false. */
                return { value: num.charAt(index), done: false };
            }
        /* En el caso de que _index_ fuera menor que 0, devolvemos undefined en _value_ y true en _done_, por lo que de esta forma finalizará la iteracción */ return { value: undefined, done: true };
        }
    }
}

let num = 2387;
for (let n of num) {
    console.log(n); // 7, 8, 3, 2
}
```

Hay que tener que cuenta que esta función _next()_ es una closure (clausura) por lo que cuando se invocó el método Symbol.iterator, su contexto, en este caso _index_ y _num_, fueron referenciados desde _next(),_ de forma que se han podido manipular desde ahí.

Existe otra forma de crear iteradores mucho más clara y elegante con el uso de los Generadores.