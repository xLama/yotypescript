## Polimorfismo {#polimorfismo}

Com su nombre indica \(muchas formas\) es la cualidad que tiene un objeto de un tipo de comportarse como de otro tipo en un momento determinado.

Recordando el ejemplo:

Stundent -&gt; Person -&gt; Mammal -&gt; LivingBeing

Podemos hacer esto:

```ts
let be: LivingBeing = new Stundent();
```

¿Por qué? Porque Student es-un LivingBeing

Si en una función aceptamos como parámetro un LivingBeing:

```ts
function example(be: LivingBeing) { }
```

¿Qué pasaría si la invocamos pasándole como argumento un _Student_?

```ts
example(new Stundent());
```

¿Sería correcto? Sí. Pues un _Stundent_ es un _LivingBeing_. No hay riesgo de ningún tipo pues _Stundent_ ha heredado de _LivingBeing_ todos los miembros públicos por lo que estamos seguros que de los métodos se van a ejecutar sin problemas.

