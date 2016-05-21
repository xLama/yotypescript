## Destructuring (deconstrucción) {#destructuring-deconstrucci-n}

Permite manipular _arrays_ y objetos de una forma fácil y amena.

### Arrays {#arrays}

**var** [x,y,z] = [1, 2, 3];

De esta forma tenemos 3 variables, llamadas _x, y, z,_ con el valor 1,2,3, respectivamente

Podemos asignar arrays directamente:

**var** array = [1, 2, 3]; **var** [x,y,z] = array;

Si hay un exceso de valores en el _array,_ estos son ignorados. Si faltan valores, los no inicializados serán _undefined_.

Es muy útil para intercambiar valores, evitando el uso de una variable intermedia.

**var** [x,z] = [1, 2]; [x,z] = [z,x]; // Ahora z vale 1 y x vale 2.

También es posible usarlos como valores devueltos por una función:

**function** numeros(){ **return** [1, 2, 3]}**var** [x,y,z] = numeros();

Además podemos ignorar valores no deseados:

**function** numeros(){ **return** [1, 2, 3]}**var** [x, ,z] = numeros();// Sólo obtenemos x, z.

### Objetos {#objetos}

Pero no sólo sirve para _arrays_. También es posible con objetos.

**var** person = {name: "José Carlos", surname: "Lama"};**var** {name, surname } = person;

Se han creado dos variables _name_ y _surname_,inicializados con los valores correpondientes a los atributos del mismo nombre. El compilador mostraría un error si cambiaráramos algún nombre:

**var** person = { name: "José Carlos", surname: "Lama"};**var** {name, surname} = person; // Error.

Tenemos la opción de redefinir los nombres:

**var** person = {nombre: "José Carlos", surname: "Lama"};**var** {name : nombre , surname: apellido} = person;

### En los parámetros de una función {#en-los-par-metros-de-una-funci-n}

Desde un punto de vista práctico la deconstrucción tiene mucho sentido cuando se trabaja con funciones. A la hora de definir sus parámetros resulta muy útil usarla ya que nos proporciona un control exhaustivo sobre ellos. La forma de hacerlo es la siguiente.

**function** car ( {color = "red", fuel = "gasoline", extras = {air : **true** } } ){ console.log(color, fuel, extras)}car ( {color: "green", fuel: "gasoil" } )

De esta forma no lo tratamos como si fuera un único parámetro tipo objeto, sino que desde el punto de vista del consumidor son todos parámetros independientes.

Para ver la ventaja que supone con respecto a versiones anteriores se muestra el código referente al estándar ECMAScript 5:

**function** car ( carProperties ){ carProperties = carProperties === undefined ? {} : carProperties; **var** color = carProperties.color === undefined ? "red" : carProperties.color; **var** fuel = carProperties.fuel === undefined ? " gasoline " : carProperties. fuel; **var** extras = carProperties.extras === undefined ? {air : **true** } : carProperties. extras;

console.log(color, fuel, extras)}car ( {color: "green", fuel: "gasoil" } )

Como vemos el código es bastante más largo y engorroso.