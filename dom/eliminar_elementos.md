## Eliminar elementos {#eliminar-elementos}

Para eliminar un elemento se debe borrar como elemento hijo del padre que tenga. Como no sabemos, a priori, quién es su padre, lo más cómodo es usar el atributo _parentNode_ y, posteriormente, removeChild

```ts
let capa = document.createElement("div");
capa.parentNode.removeChild(capa);
```