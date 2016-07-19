## Precedencia de los decoradores {#precedencia-de-los-decoradores}

Los decoradores también tienen un nivel de precedencia por el cual la ejecución de los mismos es inversa a su declaración. Para establecer un orden específico.

1.  Decorador de parámetro
2.  Decorador de método
3.  Decorador de atributo
4.  Decorador de clase

Todos estos elementos se pueden decorar con más de un decorador, teniendo encuenta que el más interno es el primero en ejecutarse:

```ts
@decorator
@anotherDecorator
class Person { }

function decorator(target: Function) { }
function anotherDecorator(target: Function) { }
```




Primero se decoraría con @anotherDecorator y después con @decorator.