### Tipos Intersección \(Intersection Types\) {#tipos-intersecci-n-intersection-types}

Si antes hemos visto la unión de tipos, ahora vamos a ver la intersección. El nombre puede confundir ya que podríamos entender unión de tipos como la combinación de los tipos. Realmente tiene ese nombre porque puede albergar cualquier dato de los tipos de la unión. En la intersección la mecánica es distinta. Cuando tipamos con una intersección de tipos, estamos haciendo que de forma obligatoria el valor debe ser de todos los tipos especificados:

```ts
type A = { x: string } & { z: number }
let foo: A;
```

Para inicilizar la variable _foo_ del ejemplo se necesita un objeto que contenga tanto la propiedad _x_ como _z_:

```ts
type A = { x: string } & { z: number }
let foo: A = { x : "foo" , z : 5};
```

Si los nombres de las propiedades coinciden, el resultado sería la intersección de sus tipos.

```ts
type A = { x: string } & { x: number }
```

Un momento, _string_ y _number_ son primitivos por lo que el valor que le asigne a _x_ debe ser uno del tipo compatible con los dos nombrados. ¿Cuál existe que cumpla esa condición? La respuesta es: solo _null_ y _undefined_. No podemos asignar un valor que sea de dos o más tipos primitivos porque no existe, más allá de los ya expuestos. Por eso hay que tener mucho cuidado a la hora de intersecar tipos porque no podría dar un comportamiento no deseado.

Podemos intesectar clases, interfaces, etc, teniendo en cuenta que sus miembros con igual nombre también se van a intersecar, y esto ocurre en todos los niveles:

```ts
class C { x: string; }
class D { x: number; }
class A { member: C; }
class B { member: D; }
let intersect: A & B;
intersect.member.x = "2"; // Error. Es del tipo number & string.
```

Hemos intersecado A & B . Como ambos tienen un miembro llamado _member_, estos también se intersecan. Los miembros son del tipo _C_ y _D_. Al intersecar estos tipos, los cuales también tienen un miembro del mismo nombre, _x_, también se intersecan. Resulta que esos miembros son primitivos por lo que al final nos da como resultado _number & string_.

