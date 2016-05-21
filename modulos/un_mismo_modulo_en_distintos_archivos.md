## Un mismo módulo en distintos archivos {#un-mismo-m-dulo-en-distintos-archivos}

Una característica importante de los módulos es la posibilidad de declarar el mismo en archivos distintos.

moduloA1.ts

**namespace** A{ **export** **class** Persona { }****}

moduloA2.ts

**namespace** A{ **export** **class** Alumno **extends** Persona { }****}

Tenemos dos archivos distintos: moduloA1.ts y moduloA2.ts. En ambos se declara del módulo _A_. En moduloA1 tenemos una clase de nombre _Persona_ y en moduloA2.ts tenemos una clase de nombre _Alumno_ que hereda de Persona. Al estar en el mismo módulo, no hay problemas. Pero al estar en archivos separados moduloA2.ts no sabe dónde buscar la clase _Persona_. Para ello hay que hacer referencia a ese archivo de forma explícita

moduloA2.ts

/// &lt;reference path="moduloA1.ts" /&gt;**module** A { **export** **class** Alumno **implements** Persona { }****}

Se ha hecho referencia al archivo _moduloA1.ts_ a través de su ruta relativa. De esta forma ya tiene acceso a _Persona_.

Es posible que el editor que estemos usando, como ocurre en el caso de VSCode, esta búsqueda se haga de forma automática y no haga falta referenciarlos explícitamente.