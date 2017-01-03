## Parámetros {#par-metros-de-una-funci-n}

> Comúnmente a los parámetros se les llama también argumentos, separando los parámetros/argumentos formales y los parámetros/argumentos actuales. Los primeros son propiedades intrínsecas que están definidas en la signatura de la función. Los segundos son los valores que se le pasan a esa función en la invocación de la misma. Para facilitar las cosas, a partir de ahora llamaremos simplemente parámetros para referirnos a los formales y argumentos para referirnos a los actuales.

Los parámetros se definen de la siguien forma:

```ts
function functionName(/*listaParametros*/):void {}

/*listaParametros representa una lista de parámetros separados por coma. 
Los parámetros son valores que la función acepta como entrada. 
Esto resulta muy útil para construir funciones más reutilizables que nos ahorren tiempo y trabajo.*/


funcion foo(x: number, z: number) { }
```

Hemos declarado dos parámetros llamados _x_ y _z_ respectivamente del tipo _number_. Esto quiere decir que para poder utilizar esa función debemos pasarle como argumentos dos números o algún tipo de dato compatible con _number_.

