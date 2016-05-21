## Evitar que una clase pueda ser superclase {#evitar-que-una-clase-pueda-ser-superclase}

Podemos hacer que una clase no pueda ser usada para herencia descomponiéndola en dos interfaces.

**interface** Persona_Estatica { **new**(edad: **string**): Persona_Instancia;}

**interface** Persona_Instancia { nombre: **string**;}**declare var** Persona: Persona_Estatica;

Recordamos que una clase tiene dos partes: la de instancia y la estática. Se declaran dos interfaces, una por cada parte de la clase. El constructor, que recordemos es de la parte estática, devuelve un objeto del tipo de la parte de instancia. Si te fijas, la variable tiene el nombre que debería tener la clase, _Persona_, y es del tipo de la parte estática de la clase, por lo que contendrá el constructor y todos los demás miembros estáticos. Con ello podemos hacer

**var** carlos = **new** Persona("Carlos");

Como new Persona(); devuelve el tipo Persona_Instancia, tenemos disponibles sus miembros no estáticos.

Así evitamos que se puedan crear clases heredadas de nuestra clase _Persona_ original pues una clase no puede tener como superclase una interfaz.

Cabe recordar que esto es sólo posible cuando estamos escribiendo archivos de definición pues la implementación del código ya está escrita en el .js que hemos cargado mediante el tag script de html.