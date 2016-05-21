## Introducción {#introducci-n}

¿Qué es la asincronía? Es la capacidad de realizar tareas a la vez que se está esperando el resultado de otras. Se puede hacer una llamada a un servicio y realizar otros menesteres mientras se espera la respuesta. Una vez llega, se trata de forma adecuada. JS, por diseño, no es multihilo como sí lo es Java o C#. Esto quiere decir que no podemos dejar un hilo ejecutándose mientras en otro realizamos alguna otra operación. Pero sí es asíncrono, es más, fue diseñado para serlo desde su nacimiento.

La forma más habitual de lidiar con la asincronía es con los llamados “callbacks”, que no son más que funciones que se ejecutan cuando la operación ha terminado, ya sea de forma exitosa o no. Esto ha sido válido durante mucho tiempo y resolvió gran cantidad de problemas pero convertía el código en difícil de leer y mantener por lo que había que tener mucho cuidado a la hora de utilizarlo. Más tarde surgió el concepto de Promise (promesa), que es una clase (objeto) que se utiliza para manejar las respuestas. Estas promesas también usan funciones de “callbacks” pero tienen la particularidad de que se pueden encadenar, dando mayor flexibilidad.

Los seres humanos realizamos tareas voluntarias de forma síncrona, es decir, cuando acabamos una empezamos otra. Nos cuesta pensar de forma asíncrona. Las funciones asíncronas intentan solucionar esto. Con ellas se puede escribir código visualmente síncrono pero que se comporta de forma asíncrona.

PREREQUSITOS PROMISE