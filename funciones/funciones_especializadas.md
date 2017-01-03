## Funciones especializadas {#funciones-especializadas}

Son aquéllas que poseen un parámetro con valor por defecto y ese valor es un _string_.

```ts
function especializada(name: "espe"): string;
function especializada(name: string): number
function especializada(name: string): any {
    return 0;
}
```

Tras los dos puntos no se ha especificado el tipo del parámetro, sino directamente el valor como cadena de caracteres.

De esta forma si invocamos la función e introducimos como argumento el valor especificado “espe”, se usaría exclusivamente esa definición de función.

Hay que tener en cuenta que si usamos este tipo de definiciones especializadas, siempre tiene que haber una que no lo sea y que englobe a las demás.

Esto no es válido

```ts
function especializada(name: "espe"): string;
function especializada(name: number): any;
function especializada(name: string): number {
    return 0
}
```

Y no lo es porque la segunda definición tiene como parámetro un _number_ el cual no es compatible con _string._ A su vez es necesaria una tercera definición que es la que contendrá el cuerpo de la función con la implementación de la misma.

