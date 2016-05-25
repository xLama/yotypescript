# Anexo III. JSON {#anexo-iii-json}

JSON, acrónimo de JavaScript Object Notation, es un formato ligero para el intercambio de datos. JSON es un subconjunto de la notación literal de objetos de JavaScript que no requiere el uso de XML.

JSON es realmente un _Object_ de Javascript, lo que podemos representar por {}. Un ejemplo de JSON sería el siguiente.

```json
{"productos": 
  { 
    "camaras": [ {"modeloA": {"precio":"100"} }, {"modeloB": {"precio":"200"} } ], 
    "relojes": [ {"relojA": {"precio":"100"} }, {"relojB": {"precio":"200"} } ] 
  }
}
```

JSON se compone de, básicamente, seis tipos de datos: _{}_, _Array_, _String, Number, Null y Boolean_. Lo normal es que todo el archivo se agrupe en un {} de modo que tenga toda la información accesibles a través de índices de cadenas de caracteres. Si quedemos agrupar _{}_ relacionados usamos los Arrays mediante literales [].

En el ejemplo tenemos un objeto con un índice llamado “productos”. Éste, a su vez, es un _{}_ con otros dos índices: _camaras_ y _relojes_. Estos son arrays que contienen cada uno {} que representan los distintos productos ya detallados, en este caso con el precio de cada uno.

Los índices pueden ser _strings_ o _booleanos_ aunque no es necesario encerrarlo entre comillas.