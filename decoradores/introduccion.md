## Introducción {#introducci-n}

Es una nueva característica añadida a partir de la versión 1.5 y se basa en una propuesta para ECMAScript 7.

Si tienes conocimientos sobre patrones de diseño seguramente lo hayas asociado al patrón Decorator. Si bien no es sintácticamente igual, sí lo es conceptualmente, pues se basa en decorar distintos elementos. En concreto: clases, métodos, parámetros y atributos.

Un decorador se define como:

*   Una expresión
*   Que evalúa una función
*   Que toma el objetivo, nombre y descriptor de propiedades como argumentos.
*   Y devuelve de forma ocasional un descriptor de propiedad para ser instalado en el objetivo.

Un decorador siempre es una función. Ejemplo de decorador de métodos:

```ts
function decorator(target, propertyKey, descriptor: TypedPropertyDescriptor< () => >){ }
```

Para asignar el decorador se hace de una forma declarativa, escibiendo @nombreDecorador justo en la línea anterior a la declaración del objetivo a decorar:

```ts
class Person{ 
  @decorator caminar(){}
}
```

Se vuelven muy útiles a la hora de inyectar dependencias, trabajar con metadatos y configurar clases o miembros.