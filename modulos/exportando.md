### Exportando {#exportando}

Lo primero que hay que hacer es declarar algún miembro como exportado para que pueda ser importando posteriormente. Lo habitual es tener un módulo por archivo, aunque no es obligatorio.

Persona.ts:

```ts
export class Person { }
```

También podemos exportarlos de esta forma.

Person.ts

```ts
class Person { }
export { Person };
```

Si tenemos más de un miembro con el mismo nombre, se exportarán ambos.

Person.ts:

```ts
class Person { }
interface Person { }
export { Person }
```

Además podemos renombrar un miembro al ser exportado.

Person.ts:

```ts
class Person { }
export { Person as Persona }
```

Una forma más fácil de exportar uno miembro es con la plabara reservada _default_. Sólo puede haber un miembro _default_ por módulo ya que con él se marca el único o más relevante del mismo.

Person.ts

```ts
class Person { }
export { Person as default }
```

Sería equivalente a.

Person.ts:

```ts
export default class Person { }
```



