## Parámetros de una función {#par-metros-de-una-funci-n}


> Comúnmente a los parámetros se les llama también argumentos, separando los parámetros/argumentos formales y los parámetros/argumentos actuales. Los primeros son propiedades intrínsecas que están definidas en la signatura de la función. Los segundos son los valores que se le pasan a esa función en la invocación de la misma. Para facilitar las cosas, a partir de ahora llamaremos simplemente parámetros para referirnos a los formales y argumentos para referirnos a los actuales.



Los parámetros se definen de la siguien forma:

```ts
function nombreDeLaFuncion(*/listaParametros*/):void```

_listaParametros_ representa una lista de parámetros separados por coma. Los parámetros son valores que la función acepta como entrada. Esto resulta muy útil para construir funciones más reutilizables que nos ahorren tiempo y trabajo.

```ts
funcion (x: number, z: number) { }
```

Hemos declarado dos parámetros llamados _x_ y _z_ respectivamente del tipo **number**. Esto quiere decir que para poder utilizar esa función debemos pasarle como argumentos dos números o algún tipo de dato compatible con **number**.

### Parámetros opcionales y por defecto {#par-metros-opcionales-y-por-defecto}

En TS podemos hacer que un parámetro de una función sea opcional, e incluso asignarle un valor por defecto. Para hacer que sea opcional escribimos el símbolo _?_ justo después del nombre del parámetro.

```ts
function sum(x: number, z?: number) {
  return x * y;
}
```

Si llamamos a la función sólo con un argumento:

```ts
sumar(10);
```

E inspeccionamos el valor de _z_, nos daría _undefined_, pues no lo hemos especificado.

Pero si llamamos a la función pasándole dos argumentos:

```ts
sumar(10,20);
```

El valor de _x_ sería 10 y el de _z_ sería 20.

También podemos asignar un valor por defecto.

```ts
function sum(x: number, z? = 20):  {
  return x * z;
}
```

De esta forma, aunque llamemos a la función con sólo un argumento, la _z_ valdrá 20 y no _undefined_.

Los parámetros opciones e inicializados no pueden colocarse delante de uno no opcional ni inicializado.

```ts
function sum(x?: number, z: number) { } // Error
function sum(x = 20, z: number): { } // Error
```

### Más parámetros {#m-s-par-metros}

Existe una forma de aceptar una lista infinita de argumentos por parámetro. En TS se llama “el resto de parámetros”.

Es bastante sencillo:
```ts
function more(x: number, ...moreParams) {
    return x;
}
```

Como puedes observar, basta con definir un parámetro más anteponiendo… (tres puntos suspensivos) a su nombre. Será del tipo _Array_ de A_ny_. Podemos tiparlo para que sea un _Array_ de otra cosa pero siempre un _Array_.

```ts
function more(...moreP: number[]) { }
```

Este parámetro especial no puede ser opcional ni puede estar inicializado.

```ts
function more(...moreP?: number[]): void { }; // Error
function more(...moreP: number[] = []): void { }; // Error
```


Para usarlo lo hacemos como si de un _array_ cualquiera se tratara.

```ts
function adder(...moreP: number[]) {
    let total = 0;
    for (let num of moreP) {
        total += num;
    }
    return total;
}
let sum = adder(3, 56, 89, 12, 56); // 216
```

La función suma todos los números del array introducido como argumento y devuelve el resultado.

### Parámetros por valor o por referencia {#par-metros-por-valor-o-por-referencia}

A la hora de pasar argumentos a una función, se puede hacer de dos formas: por valor o por referencia. Esto no lo decidimos nosotros (no en TS. Existen otros lenguajes donde sí podemos elegir).

#### Por valor {#por-valor}

El paso por valor es el más sencillo. Cuando invocamos una función e introducimos un valor como argumento, se realiza una copia del valor hacia el parámetro de la función. Que sea una copia quiere decir que el valor pasado y el parámetro ya no tienen relación en la memoria en el momento de la ejecución.

```ts
let x = 5;
function value(y: number): void {
    y++; // 6
}
x; // 5
```

Hemos creado una variable de tipo **number** con un valor inicializado de 5\. Hemos invocado la función pasando esta variable como argumento. En ese momento se ha creado una copia de la variable _x_ de fuera de la función hacia la variable _y_ de dentro de la función. Si modificamos la variable _y_ (en este caso hemos sumado uno) vemos como la _x_ se mantiene intacta.

#### Por referencia {#por-referencia}

En contraposición al paso por valor existe el paso por referencia. En éste no se hace una copia del valor de la variable hacia el parámetro de la función, sino que lo que se le pasa es la referencia de la dirección de memoria.

Cuando se crea una variable se reserva un espacio de memoria donde almacenarla. Ese espacio de memoria tiene una dirección que maneja internamente la máquina virtual. Al hacer un paso por referencia lo que se le proporciona es esta dirección de memoria a otra variable. Dos variables, a priori distintas, que posean la misma dirección están apuntando al mismo lugar de la memoria por lo que en realidad son la misma variable.

```ts
let x = [0, 0];
x[0]; // 0
function reference(y: number[]): void {
    y[0] = 1; // 1
}
reference(x);
x[0]; // 1
```

Tenemos un _Array_ de **number** con dos posiciones, ambas con valor 0.Le pasamos el array a la función y la posición 0 que vale 0, la cambiamos a 1.Al acabar la ejecución de la función y mostrar el contenido de la posición 0 del array, vemos que lo cambiado en la función persiste, al contrario de lo que pasaba con el ejemplo del paso por valor.

Como hemos dicho lo que ha ocurrido es que a la función se le ha pasado la dirección de memoria del array. Gracias a esto, al usar la variable lo que estamos haciendo es trabajar directamente sobre el array original.