# Document Object Model (DOM)

![Untitled](Software%20development/JavaScript/Conceptos/Document%20Object%20Model%20(DOM)%20648d1442822548d8901c57995d12ed6a/Untitled.png)

El DOM nos Proporciona otras formas de presentar, guardar y manipular este mismo documento. 
Es una representación completamente orientada al objeto de la página web

Una página HTML está formada por múltiples etiquetas HTML, anidadas una dentro de otra, formando un árbol de etiquetas relacionadas entre sí, que se denomina **árbol DOM.**

DOM virtual: copia del dom a base de objetos de javascript, que estan en memoria. El sentido de esto es mantener los cambios en el DOM virtual y una vez se terminan los eventos se aislan los cambios minimos para efectuarlos en el DOM real. svelte no usa dom virtual por su proceso de compilación cambia la complejidad en la compilacion para no hacerla en el runtime

parent node, query etc