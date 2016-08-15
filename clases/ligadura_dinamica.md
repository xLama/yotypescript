## Ligadura dinámica {#ligadura-din-mica}

¿En qué consiste?

```ts
class A {
    mostrarLetra() {
        alert("A");
    }
}
class B extends A {
    mostrarLetra() {
        alert("B");
    }
}
```

Tenemos dos clases: _A_ y _B_. _B_ hereda de _A_. Ambas tienen definido el método _mostrarLetra\(\)_. En _A_ la ejecución de ese método muestra un alert con la letra A y en _B_ muestra la letra B.

Si hacemos esto:

```ts
let a = new A();  
let b = new B();
a.mostrarLetra();
b.mostrarLetra();
```


Lo que obtendremos primero es A y después B. Algo lógico.

Pero ¿y si hacemos esto?

```ts
let a: A = new B();
a.mostrarLetra();
```

¿Qué mostrará el alert? ¿“A” o “B”? La respuesta es “B”.

El trabajo se realiza en tiempo de ejecución pues no es hasta entonces cuando se conoce qué método ha de ejecutarse: si el del padre o el del hijo.

¿Qué utilidad tiene esto?

La más inmediata es que nos evita hacer el _casting_ de tipos. Se ve mejor con un ejemplo.

Tenemos esta jerarquía de clases:

Alumno Persona Mamifero SerVivo

**function** mostrarNombre\(ser: SerVivo\): **void** { ser.mostrarNombre\(\);}

Ejecutamos el método _mostrarNombre\(\)_ del parámetro. Cada una de las clases de la jerarquía tiene implementado el método _mostrarNombre_\(\) ya sea porque lo ha heredado o porque lo ha sobreescrito. Por lo tanto sea cual sea el tipo que introduzcamos como parámetro en la llamada a la función nos ejecutará el del tipo introducido y no el de _SerVivo_. Esto está estrechamente relacionado con el [polimorfismo](polimorfismo.md).

