## Fusionando interfaces {#fusionando-interfaces}

Puede declarar dos interfaces con el mismo nombre sin ningún problema. Éstas se fusionarán en una sola donde sus miembros será la combinación de todos.

Se puede tener atributos con nombre repetidos ya que en ese caso el atributo sería el tipo unión de ambos. Los métodos también pueden repetirse por lo que se aplicarían las reglas de [sobrecarga de funciones](../funciones/sobrecarga.md).

Es muy útil para crear tipos aumentados, como por ejemplo los ya predefinidos por el lenguaje como _Number_ o _String_.