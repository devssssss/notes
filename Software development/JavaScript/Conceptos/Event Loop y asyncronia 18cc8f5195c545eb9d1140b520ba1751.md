# Event Loop y asyncronia

Promesas vs callbacks

 callbacks funcion que se pasa como argumento, funcion que se le puede pasar a otra como argumento y que se ejecuta despues que alla completado algo(que puede ser asyncrono o no) 

.Existe  la asyncronia con callbacks se usa mas que nada se usa nodejs o con librerias que lo requieran.

### ¿Qué entendemos por programación dirigida por eventos?

La programación basada en eventos es un enfoque que hace un gran uso de eventos para activar varias funciones. Un evento puede ser cualquier cosa como un clic del mouse, presionar una tecla, etc. Cuando ocurre un evento, se ejecuta una función de devolución de llamada (callback) que ya está registrada con el elemento. Este enfoque sigue principalmente el patrón de publicación-suscripción. Debido a la programación basada en eventos, Node.js es más rápido en comparación con otras tecnologías.

Como ya se mencionó, las aplicaciones de Node.js son de un solo subproceso y están basadas en eventos. Node.js admite la simultaneidad, ya que se basa en eventos y, por lo tanto, utiliza conceptos como eventos y callbacks. Las llamadas a la función asíncrona ayudan a Node.js a mantener la concurrencia en toda la aplicación.

Básicamente, en una aplicación Node.js, hay un ciclo principal que espera y escucha eventos, y una vez que se completa un evento, inicia inmediatamente una función callback.

El siguiente diagrama representa cómo se controlan los eventos en Node.js.

[https://lh6.googleusercontent.com/mxI-Y-NtmldPIF878-SGbHrzBwNk_spOEhZI43trHwgU2vOUg8MW_1bwJk_mAn7y3tNgo9ujxVYB9xmSdU8t5S6wa-veO6aG8xTHKWWC2PSvkHxj87WBZl2Yj95aZyzIbd7tlMID-89D-W6FvoEWFVSF13khkupALqnAFLGOQtKqXQtxXZ_wA7gTVw](https://lh6.googleusercontent.com/mxI-Y-NtmldPIF878-SGbHrzBwNk_spOEhZI43trHwgU2vOUg8MW_1bwJk_mAn7y3tNgo9ujxVYB9xmSdU8t5S6wa-veO6aG8xTHKWWC2PSvkHxj87WBZl2Yj95aZyzIbd7tlMID-89D-W6FvoEWFVSF13khkupALqnAFLGOQtKqXQtxXZ_wA7gTVw)

### ¿Qué es el **Event Loop** y cómo funciona?

El Event Loop hace que Javascript parezca ser multihilo a pesar de que corre en un solo proceso. Javascript se organiza usando las siguientes estructuras de datos:

- **Stack**. Va apilando de forma organizada las diferentes instrucciones que se llaman. Lleva así un rastro de dónde está el programa, en que punto de ejecución nos encontramos.
- **Memory Heap**. De forma desorganizada se guarda información de las variables y del scope.
- **Schedule Tasks**. Aquí se agregan a la cola, las tareas programadas para su ejecución.
- **Task Queue**. Aquí se agregan las tareas que ya están listas para pasar al stack y ser ejecutadas. El stack debe estar vacío para que esto suceda.
- **MicroTask Queue**. Aquí se agregan las promesas. Esta Queue es la que tiene mayor prioridad. El Event Loop es un loop que está ejecutando todo el tiempo y pasa periódicamente revisando las queues y el stack moviendo tareas entre estas dos estructuras.

[https://www.youtube.com/watch?v=C_eFawNnmC4](https://www.youtube.com/watch?v=C_eFawNnmC4)