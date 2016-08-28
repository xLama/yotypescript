## Confirmaciones de tipo ( Type Assertions ) {#confirmaciones-de-tipo-type-assertions}

Siguiendo con el ejemplo anterior, podemos hacer que la letiable _ser_ se convierta en un _Alumno_ para poder ejecutar todo lo que *Stundet* implementa y *LivingBeing* no, porque en la invocación de la función introdujimos como argumento un _Alumno_. Ocurre que sintácticamente no tenemos disponible los métodos de *Stundet* porque el parámetro de la función es del tipo *LivingBeing*, por lo que hay que forzarlo.

```ts
function ejemplo(ser: LivingBeing): void {
    let student = ser as Student;
}
```

A esto se le llama _type assertion_ (es conceptualmente parecido a los _castings_ o conversiones de tipo disponibles en otros lenguajes) y consiste en convertir un tipo en otro siempre y cuando estén relacionados.

```ts
interface A { }
interface B extends A { }
class C implements B { }
function conversion(casting: A): void {
    let c = casting as A;
}
conversion(new C());
```

Los _type assertions_ se hacen encerrando el tipo al que queremos convertir entre &lt;&gt; seguido de la variable que queremos convertir o con la sentencia *as*

En el caso en el que queramos usar un método del tipo de la variable a la que queremos convertir directamente sin asignarlo a otra variable tenemos que usar los paréntesis.

```ts
class C {
    toDo(): void { }
}
function conversion(casting: A): void {
    (casting as C).toDo();
}

conversion(new C());
```

Como TS se basa en el [tipado estructural](../genericos/comparando_genericos.md#757309351116418-_Tipado_estructural), es posible hacer conversiones de tipos que no tengan relación pero sean estructuralmente análogos.

```ts
class A {
    public showA(): void {
        alert("A");
    }
}

class B {
    public showA(): void {
        alert("A");
    }

    public showB(): void {
        alert("B");
    }
}

function showLetter(letter: A) {
    (letter as B).showB();
}


mostrarLetra(new B());
```

El código perfectamente válido y se ejecuta sin problemas. El parámetro del tipo _A_ de la función *showLetter* acepta como parámetro un objeto del tipo _B_ porque _B_ tiene todo lo de _A_. A partir de ahí B puede implementar todos los métodos que quiera.