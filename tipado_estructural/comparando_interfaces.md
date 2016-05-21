## Comparando interfaces {#comparando-interfaces}

La comparación de interfaces se hace igual que la comparación de clases: miembro a miembro. Aunque resulta más simple por no tener miembros privados ni protegidos.

Esto es correcto:

**interface** A { **** name: **string**;}

**interface** B { **** name: **string**;}

**var** a: A;**var** b: B;a = b;b = a;

De nuevo se aplica la máxima en las comparaciones de objetos: el objeto con más miembros puede ser asignado al objeto con menos, pero no al revés.

**interface** A{ **** nombre: **string**; print();}**interface** B { **** nombre: **string**;}**var** a: A;**var** b: Ba = b; // Errorb = a;