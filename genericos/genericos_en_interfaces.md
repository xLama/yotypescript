## Genéricos en interfaces {#gen-ricos-en-interfaces}

También se pueden parametrizar las interfaces de la misma forma que las clases.

Nuestra clase de ejemplo _Concesionario_ va a implementar una interfaz llamada _IConcesionario_ que acepte el mismo parámetro.

```ts
interface Concesionario<T> {
    getCoche(índice: number): T;
}

class Concesionario<T extends Automovil> implements IConcesionario<T> {
    //(...)
}
```

Como hemos dicho, al sustituir el parámetro _T_ por lo que queremos, se hace en todas las ocurrencias de _T_. Con el ejemplo de _Seat_ quedaría así:

```ts
class Concesionario<Seat extends Automovil> implements IConcesionario<Ferrari>{
    //(...)
}
```

Hay que aclarar que estos ejemplos sustituyendo la _T_ de forma manual son simplemente para mostrar lo que hace el lenguaje.

¿Se puede hacer que la restricción de parámetro sea por interfaz y no por herencia? Sí, con la misma palabra _extends_.

Cambiamos la clase _Concesionario_ para que su restricción se base en la interfaz _IAutomovil_

Tan fácil como:

```ts
class Concesionario<T extends IAutomovil> implements IConcesionario<T>{
    //(...)
}
```

Ahora todas las clases que implementen la interfaz _IAutomovil_ son susceptibles de ser introducidas como argumento y si no lo hacen no sería aceptada.

```ts
class Automovil implements IAutomovil { }
class Seat extends Automovil { }
let conceSeat = new Concesionario<Seat>();
```

En este caso sería correcto porque aunque _Seat_ no implementa la interfaz _IAutomovil_ de forma explícita, lo hace a través de su superclase.