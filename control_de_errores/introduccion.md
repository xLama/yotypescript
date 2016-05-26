## Introducción {#introducci-n}

Existe una forma de capturar los errores que se produzcan en nuestra aplicación y darle respuesta a los mismos de una forma controlada. En otros lenguajes se les llama excepciones pero en TS se llaman errores.

Para capturar uno se utiliza la estructura _try-catch_, encerrando en el _try_ el código susceptible a fallar.

```ts
try {
    // código
} catch (e) {
    // tratar el error
}
```

Si algo de lo que se ejecuta falla y lanza una excepción, se ejecutará el código encerrado en el bloque _catch_. El parámetro de _catch_ es del tipo _Error_ pero no se tipa de forma explícita. Si se hiciera fallaría al compilar.