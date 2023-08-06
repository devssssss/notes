# Motor de JavaScript

Los motores son esas programas que se encargan de convertir código de alto nivel (JavaScript, Python, C) a código de bajo nivel (Machine Code, Bytecode). Cada navegador tiene su propio motor para compilar e interpretar JavaScript:

- **V8 Engine (Google Chrome)**, el cual también es motor de Node.js (En este nos basaremos para la explicación).
- **Spider Monkey (Mozilla Firefox).**
- **Chakra (Microsoft Edge).**
- **JavaScriptCore (Apple Safari).**

**La llegada de V8 y su importancia**

El día 2 de septiembre de 2008 se lanzó la primera versión del motor V8, sin saber del todo que iban a ser el gran cambio en la interpretación de JavaScript en el navegador, este dejaría de ser tan lento como lo era.

**¿Cómo lo hicieron?**

Entre todas las razones, la principal está en los conceptos **compilador** e **intérprete**.

**El compilador es el programa encargado de convertir código escrito en un lenguaje de programación a otro lenguaje de programación de bajo nivel**. Por ejemplo, el compilador del V8 es el encargado de transformar JavaScript a Bytecode(ensamblador) y luego a Machine Code.

Por otra parte, **el intérprete es el encargado de revisar el código línea por línea y ejecutarlo directamente en la máquina de destino**. Cabe resaltar que los intérpretes también realizan algún trabajo de traducción al igual que los compiladores.

> 💡 JavaScript es en realidad un lenguaje interpretado por el navegador. Pero técnicamente también está compilado por el motor del navegador. Increíble, lo sé.
> 

**Entendiendo como funciona V8**

![Untitled](Software%20development/JavaScript/Conceptos/Motor%20de%20JavaScript%20a834c7feef3343dc85236b0320f94d12/Untitled.png)

Cuando llega un script al navegador el motor V8 inicia un proceso el cual consta de:

1. Recibir el código fuente como un flujo de bytes UTF-16 y pasarlo a un decodificador de flujo de bytes que hace parte del motor.
2. Parsear el código y construir el Abstract Syntax Tree (AST).2.1. El parser toma el código fuente y lo descompone en tokens (let, new, símbolos de operaciones, functions, promises). Existen 2 tipos de parseo en V8 que verás más abajo.2.2. Gracias al parseo se genera una estructura de datos en forma de árbol, la cual es la misma que la AST.
3. El intérprete recorre el AST y va generando el bytecode.
4. El **optimizing compiler** optimiza el código bytecode a machine code y se reemplaza el código base.

El **optimizing compiler** encuentra los puntos donde el código se puede optimizar. Normalmente optimiza el código que se repite varias veces. En caso de que la operación cambie por alguna razón, el código vuelve a la versión anterior (la des-optimizada). Esto se hace para consumir menos recursos y por lo tanto ejecutar el código más rápido.

Por ejemplo, este código puede ser optimizado:

```
function add(a, b) {
return a + b;
}

for (let i = 0; i < 1000; i++) {
	add(i, i);
}

```

Cuando ese código se ejecute unas 50 veces, estará listo para ser optimizado porque el profiling data sabe que no cambiará.

Si se cambia el código por alguna razón:

```
functionadd(a,b){
	return a +b;
}

for (let i = 0; i < 1000; i++) {add(i,i);
}

add(1,"uno")

```

Volverá a su versión anterior.

**Tipos de parseo**

**Eager Parsing:**

- Encuentra errores de sintaxis
- Crea el AST
- Construye scopes

**Lazy Parsing:**

- Doble de rápido que el eager
- No crea el AST
- Construye scopes parcialmente

El proceso de parsing hace parte del 15% — 20% del proceso de ejecución así que hay que tenerlo muy en cuenta.

…

¡Y eso es todo! Así funciona el motor V8 de JavaScript desarrollador por Chrome.

Los motores de los demás navegadores tienen casi el mismo proceso de ejecución del V8 Engine ya que fueron creados a partir de este. Cuentan solo con algunas pequeñas diferencias. Como por ejemplo en las capas de optimización:

- V8 Engine (Chrome): 1 Sola capa de optimización
- Spider Monkey (Firefox): Tiene 2 capas de optimización
- Chakra (Edge): Tiene 2 capas de optimización
- JavaScriptCore (Safari): Tiene 3 capas de optimización

Los de 2–3 capas se ejecutan un poco más lento pero se optimizan más rápido.

sacado  de : [https://dev.to/johncardenasp/como-funciona-el-motor-de-javascript-jfb](https://dev.to/johncardenasp/como-funciona-el-motor-de-javascript-jfb)

revisar [https://www.campusmvp.es/recursos/post/fundamentos-de-javascript-por-que-deberias-saber-como-funciona-el-motor.aspx](https://www.campusmvp.es/recursos/post/fundamentos-de-javascript-por-que-deberias-saber-como-funciona-el-motor.aspx)