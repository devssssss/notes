# Cliente

[https://github.com/midudev/preguntas-entrevista-react#qué-es-react](https://github.com/midudev/preguntas-entrevista-react#qu%C3%A9-es-react)

temporal dead zone, callback, , callstack,y talvez cosas como webpack, babel, frameworks, ssr, csr patrones de disenio, arquitectura, npm, css(teorico),  accesibilidad? principios, typescript, virtual dom

dom docuymento con todos los elementos para mostrar una pagina web, es un nodo de lementos que representa. Esta dentro de las librerias. 2 procesos importantes reconciliazion y renderizacion

recionciliacion: proceso que utiliza readt para tomar componentes analizar y comparar con lo que esta en la web(dom). Si no existe una diferencia .lso23 estan sincronizados

renderizacion: tomar esas diferencias y se asegura que se aplica en el dom 

react libreria para renderizar elementos de una pagina web con una arquitectura ce componentes.

Virtual DOM: parte eencial apra el proceso de reconciliacion. representacion de la pagina a rederizar. funciona principalmente para optimizar

react-dom renderiza

[CSR VS SSR](CSR%20VS%20SSR%20c937087ec7c1461bb95ad0dbea71f111.md)

[https://ecdisis.com/que-es-la-indexacion-en-los-motores-de-busqueda/](https://ecdisis.com/que-es-la-indexacion-en-los-motores-de-busqueda/)


# Next

next utiliza por debajo express

un fetch en el cliente si no se carga en js no se muestran los datos. Por lo tanto no sirve. La solucion es hacer el fetching en cada request de datos en el servidor con getServerSideProps (da performance) y devluelve el html con la data  . para datos muy live o tiene muchos datos dinamicos. hace el fetch en runtime cuando hay una request de un usuario

getStaticProps (ssg)haceel fetching 1 sola vez en build time o para referescar la pagina en el html. 

componente image optimiza. y hace que no haya saltos en e

el coimponente image no hace cambiio de layout