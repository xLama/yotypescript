### Parámetros por valor o por referencia {#par-metros-opcionales-y-por-defecto}

A la hora de pasar argumentos a una función, se puede hacer de dos formas: por valor o por referencia. Esto no lo decidimos nosotros \(no en TS. Existen otros lenguajes donde sí podemos elegir\).

#### Por valor {#por-valor}

El paso por valor es el más sencillo. Cuando invocamos una función e introducimos un valor como argumento, se realiza una copia del valor hacia el parámetro de la función. Que sea una copia quiere decir que el valor pasado y el parámetro ya no tienen relación en la memoria en el momento de la ejecución.

```ts
let x = 5;
function value(y: number): void {
    y++; // 6
}
x; // 5
```

Hemos creado una variable de tipo _number_ con un valor inicializado de 5. Hemos invocado la función pasando esta variable como argumento. En ese momento se ha creado una copia de la variable _x_ de fuera de la función hacia la variable _y_ de dentro de la función. Si modificamos la variable _y_ \(en este caso hemos sumado uno\) vemos como la _x_ se mantiene intacta.

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

Tenemos un _Array_ de _number_ con dos posiciones, ambas con valor 0.Le pasamos el array a la función y la posición 0 que vale 0, la cambiamos a 1.Al acabar la ejecución de la función y mostrar el contenido de la posición 0 del array, vemos que lo cambiado en la función persiste, al contrario de lo que pasaba con el ejemplo del paso por valor.

Como hemos dicho lo que ha ocurrido es que a la función se le ha pasado la dirección de memoria del array. Gracias a esto, al usar la variable lo que estamos haciendo es trabajar directamente sobre el array original.

