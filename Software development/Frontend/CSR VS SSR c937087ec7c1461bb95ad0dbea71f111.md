# CSR VS SSR

## Client Side Rendering (CSR)

[data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNzg1IiBoZWlnaHQ9IjQ2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNzg1IiBoZWlnaHQ9IjQ2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=)

### El funcionamiento es el siguiente:

1°Primero el usuario ingresa a la página lo que hace una petición al servidor web o CDN donde esté alojada nuestra página web.

2°Seguido, el servidor entrega una página web en blanco contenido html

3°En este momento el navegador empieza a cargar el contenido Javascript de la página y a hacer peticiones correspondientes a las APIs para obtener la información para mostrar

4°Con la información obtenida la página puede pintar la data volviendose interactiva con el usuario.

Pros

- Es rápido para el servidor entregar una página en blanco.
- Tiene soporte para SPAs.
- Es súper rápido una vez todo el Javascript ha sido cargado.

Contras

- Entregas una página en blanco al usuario.
- **Al entregar una página en vacía, no hay posibilidad de ser indexado por motores de búsqueda.**
- Peligroso cuando tienes que cargar mucha información, provocando que el usuario solo vea una página blanca por más tiempo.
- Conexiones lentas pueden pueden provocar rebote de los usuarios.

## Server Side Rendering (SSR)

crea la página final en el lado del servidor, llenándola con información previo a entregársela al usuario.

[data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNzg1IiBoZWlnaHQ9IjQ2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNzg1IiBoZWlnaHQ9IjQ2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=)

### El funcionamiento es el siguiente:

1° Primero el usuario ingresa a la página lo que hace una petición al servidor web o CDN donde esté alojada nuestra página web.

2° Luego React corre en el servidor, empezando a ejecutar las llamadas a las APIs para obtener la información que quiere utilizar la página.

3° Las APIs entregan la información requerida por el servidor.

4° Con el HTML montado, el servidor entrega la página completa al cliente.

5° Cuando le llega la página al cliente, React empieza a comparar la página entregada con el javascript en su [fase de hidratación](https://es.reactjs.org/docs/react-dom.html#hydrate) generando el Vdom, si es exitoso ambas partes [se reconcilian](https://es.reactjs.org/docs/reconciliation.html) y estás listo para usar la página.

Pros

- Es bueno para páginas que necesitan tener un buen SEO y que quieren ser indexadas por motores de búsqueda
- El contenido entregado por el servidor es inmediato.
- Funciona perfectamente en conexiones lentas.
- No hay peticiones a APIs en el lado del cliente.

Contras

- Es más pesado para el servidor
- No puede ser cacheado debido a las peticiones que hace, por lo que se asume que esta información necesita ser nueva cada vez que el cliente quiere entrar a la página
- No funciona bien con librerías que necesitan acceder a la propiedad document.
- Genera problemas de hidratación si se accede a variables de localStorage o información que no puede ser obtenida en el lado del servidor.

## 3.- Static Side Generation (SSG)

Con este modelo, movemos el trabajo de renderizado de las páginas desde el lado del cliente y del lado del servidor hacia nuestro proceso de compilación o build generando toda las páginas y entregando páginas cacheadas al usuario.

[data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNzg1IiBoZWlnaHQ9IjQ2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNzg1IiBoZWlnaHQ9IjQ2MCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=)

[https://www.stewartgf.com/_next/image?url=%2F_next%2Fstatic%2Fimage%2Fpublic%2Fimg%2Ftipos-de-renderizado-en-2021-con-next-js%2FSSG.953eb3cd8e46dc4ac9d86efc0ea0e8d5.png&w=1920&q=100](https://www.stewartgf.com/_next/image?url=%2F_next%2Fstatic%2Fimage%2Fpublic%2Fimg%2Ftipos-de-renderizado-en-2021-con-next-js%2FSSG.953eb3cd8e46dc4ac9d86efc0ea0e8d5.png&w=1920&q=100)

### El funcionamiento es el siguiente:

- Previamente- Al querer desplegar la página para producción se tiene que hacer un build, que por lo general es manejado por páginas como [Vercel](http://vercel.com/) ó [Netlify](http://netlify.com/) acá Next.js comienza a generar todas las páginas haciendo llamadas a las APIs para poder obtener la información y generar las páginas estáticas.

1°Primero el usuario ingresa a la página lo que hace una petición al servidor web o CDN donde esté alojada nuestra página web.

2°El CDN entrega la página inmediatamente al ya tener la página generada, cargada en el build.

Pros

- Las páginas son muy rápidas.
- Se genera una vez y luego el CDN la entrega inmediatamente al usuario.
- No tenemos peticiones por el lado del cliente.
- Perfecto para páginas que requieren un buen SEO.
- No tiene estado de carga, ya que nada necesita ser cargado, todo fue previamente cargado en el build.
- No hay necesidad de tener un servidor.

Contras

- Tiene un build time más largo que el resto de los modelos.
- No funciona bien con librerías que necesitan acceder a la propiedad document.
- Genera problemas de hidratación si se accede a variables de localStorage o información que no puede ser obtenida previa a la generación de la página.