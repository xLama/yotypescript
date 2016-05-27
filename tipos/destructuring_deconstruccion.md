## Destructuring (deconstrucción) {#destructuring-deconstrucci-n}

Permite manipular _arrays_ y objetos de una forma fácil y amena.

### Arrays {#arrays}

```ts
let [x,y,z] = [1, 2, 3];
```

De esta forma tenemos 3 variables, llamadas *x, y, z,* con el valor 1,2,3, respectivamente

Podemos asignar arrays directamente:

```ts
let array = [1, 2, 3];
let [x,y,z] = array;
```

Si hay un exceso de valores en el _array,_ estos son ignorados. Si faltan valores, los no inicializados serán _undefined_.

Es muy útil para intercambiar valores, evitando el uso de una variable intermedia.

```ts
let [x,z] = [1, 2]; 
[x,z] = [z,x]; // Ahora z vale 1 y x vale 2.
```

También es posible usarlos como valores devueltos por una función:

```ts
function numbers() {
    return [1, 2, 3]
}
let [x, y, z] = numbers();
```

Además podemos ignorar valores no deseados:

```ts
function numbers() {
    return [1, 2, 3]
}
let [x, , z] = numbers();// Sólo obtenemos x, z.
```

### Objetos {#objetos}

Pero no sólo sirve para _arrays_. También es posible con objetos.

```ts
let person = { name: "José Carlos", surname: "Lama" };
let {name, surname } = person;
```

Se han creado dos variables _name_ y _surname_,inicializados con los valores correpondientes a los atributos del mismo nombre. El compilador mostraría un error si cambiaráramos algún nombre:

```ts
let person = { name: "José Carlos", surname: "Lama" };
let {name, surname} = person; // Error.
```

Tenemos la opción de redefinir los nombres:

```ts
let person = { nombre: "José Carlos", surname: "Lama" };
let {name: nombre, surname: apellido} = person;
```

### En los parámetros de una función {#en-los-par-metros-de-una-funci-n}

Desde un punto de vista práctico la deconstrucción tiene mucho sentido cuando se trabaja con funciones. A la hora de definir sus parámetros resulta muy útil usarla ya que nos proporciona un control exhaustivo sobre ellos. La forma de hacerlo es la siguiente.

```js
function car({color = "red", fuel = "gasoline", extras = { air: true } }) {
    console.log(color, fuel, extras)
}
car({ color: "green", fuel: "gasoil" })
```

De esta forma no lo tratamos como si fuera un único parámetro tipo objeto, sino que desde el punto de vista del consumidor son todos parámetros independientes.

Para ver la ventaja que supone con respecto a versiones anteriores se muestra el código referente al estándar ECMAScript 5:

```js
function car(carProperties) {
    carProperties = carProperties === undefined ? {} : carProperties;
    let color = carProperties.color === undefined ? "red" : carProperties.color;
    let fuel = carProperties.fuel === undefined ? " gasoline " : carProperties.fuel;
    let extras = carProperties.extras === undefined ? { air: true } : carProperties.extras;
    console.log(color, fuel, extras)
}

car({ color: "green", fuel: "gasoil" })
```

Como vemos el código es bastante más largo y engorroso.