## La importancia de Symbol {#la-importancia-de-symbol}

Existe un **symbol** predefinido que accesible de esta forma:

Symbol.iterator;

Éste sirve para nombrar al método iterador de una clase. Es posible gracias a que un **symbol** puede ser una propiedad de un objeto. Para comprobar si una clase lo posee:

**var** nums : **number**[] = [1, 2, 3];**var** iterator : **string** = "iterator";**var** x : **number** = 26;**var** obj : {} = {name : "Carlos", age: 26}nums[Symbol.iterator]; // funtion ArrayValuesiterator[Symbol.iterator]; // funtion [Symbol.iterator]()x [Symbol.iterator]; // undefinedobj [Symbol.iterator]; // undefined

Sólo el array y el **string** tienen iteradores predefinidos. Tanto el **number** como el object, no. Esto es importante porque ni con el object ni con el **number** podremos usar for-of, ya que éste requiere el método [Symbol.iterator](). Lo realmente potente es que nosotros podemos crear nuestros propios iteradores.