## Polimorfismo {#polimorfismo}

Com su nombre indica (muchas formas) es la cualidad que tiene un objeto de un tipo de comportarse como de otro tipo en un momento determinado.

Recordando el ejemplo:

Stundent Person Mammal LivingBeing

Podemos hacer esto:

```ts
let ser: SerVivo = new Stundent();
```

¿Por qué? Porque Student es-un LivingBeing

Si en una función aceptamos como parámetro un LivingBeing:

```ts
function example(ser: LivingBeing): void { }
```

¿Qué pasaría si la invocamos pasándole como argumento un _Alumno_?

```ts
ejemplo(new Stundent());
```

¿Sería correcto? Sí. Pues un *Stundent* es un *LivingBeing*. No hay riesgo de ningún tipo pues *Stundent* ha heredado de *LivingBeing* todos los miembros públicos por lo que estamos seguros que de los métodos se van a ejecutar sin problemas.