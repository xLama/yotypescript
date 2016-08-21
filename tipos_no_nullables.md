# Tipos no nullables


Para activar esta caracterñuistiuca se debe hacer desde el archivo tsconfig.json stricnullshceck true...

¿Quñe es lo que hace? Hemos estudiado que hay una compatibilidad de tipos predefinida en el lenguaje, es decir, any es ocmpatible con todos los tipos, object (vacio) tambien,
string, umber y boolean solo con los suyos y así sigue. Lo que quizás no te has percatado es que puedes asignar el valor null o undefined a cualquier tipo. Y cuando
digo cualquiera es cualquiera, incluso Function.

Esto lo qu hace es separarlos y no permitir que  que null y undefined sean asignables a todos los tipos, sólo a los que lo especifiqne de forma explícita.
IMAGEN DE EJEMPLO

Ahora no podremos hacer Esto

let name :string = null;

Pero podemos, gracias a los tipos union, aceptarlos de esta forma:

let name: stirng | null = null;

¿Quñe ventajas supone? Una de las grandes ventajas es que , gracias al control del fujo, podemos evitar busg que de otra forma solo serian detectables 
en tiempo de ejecución.

Un ejemplo sencillo para ir entrando en materia.

function getLast(name: string){
    return name....  // Error. Object es posiblemente undefined


}

¿Por qué ese error? Como hemos dicho, ni null ni undefined son asignables a string
