## Interfaces herendando de clases {#interfaces-herendando-de-clases}

En TS podemos hacer que una interfaz herede de una clase. En este caso la interfaz hereda los miembros pero no su implementación porque una interfaz no puede contener implementaciones.

```ts
class A {
    public name: string;
}

interface I extends A { }
```

¿Qué ocurriría si la clase contiene miembros? Como hemos visto en apartados anteriores, aunque los miembros privados no se heredan, realmente sí están presentes en las clases hijas aunque no accesibles. Por ello la interfaz lo contendría pero con una curiosa consecuencia:

```ts
class A {
    private name: string;
}

interface I extends A { }
```

Sólo las clases que hereden de _A_ podrán implementar la interfaz _I_ y no otras pues serán las únicas que contengan el miembro privado original.

```ts
class A {
    private name: string;
}

interface I extends A { }
class B extends A implements I { } // Correcto
class C implements I { } // Error. C No es subclase de A
```

Muestra un error indicando que _C_ no está implementando todos los miembros de la interfaz _I_, concretamente el atributo _nombre_. Aunque declaremos un atributo nombre de tipo **string** y privado en la clase C, no conseguiríamos que compilara. El único que le sirve es el de la clase A y sólo se puede conseguir heredando de ella. El comportamiento con miembros protegidos sería exactamente el mismo.