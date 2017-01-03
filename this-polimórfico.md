## This polimórfico

Ahora  _this_ se refiere a la instancia de alguna clase que herede de la clase contenedora.

```ts
class HTMLElement { 
//...
  public setId( id: string ){ 
    this.id = id;
    return this; 
  } 
//...
}
class Div extends HTMLElement { //…
  public setWidth( width: number ){ 
    this.width = width;
    return this; 
  } 
//...
}
let div = new Div().setId("div").setWidth(5);
```

Al invocar el método _setId,_ el cual es de _HTMLElement_, lo devolvería, con lo cual, al intentar invocar _setWidth,_ y no ser éste parte de esa clase, fallaría. Precisamente ese es el comportamiento que ha cambiado. Ahora sabe que lo que devuelve _setId_ no es _HTMLElement,_ sino cualquier clase que herede de ella y que esté invocando el método en ese instante.

