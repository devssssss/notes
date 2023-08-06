
No funciona en tiempo de ejecucion, transpila a JS. Hace que no sea tipado debil y dinamico. pero en tiempo de ejecucion no funciona.

```jsx
Asi se asigna un tipo

const hola: string = 'asd'
```

hay que evitar escribir tipos, typescript sabe inferir tipos por defecto (cuando no infiere se suele agregar el any que esta obviamente mal) Ej:

```jsx
const variable1  = 1
const variable2 : number = 1
```

El tipo unknow es no sabe cual es el tipo. any se saltea los type checking.

El tipo never nunca devuelven nada, void simplemente la funcion puede devolver un valor

Las funciones no tienen inferencia.

es viable usar el readonly

Tambien typescript tiene inferencia del tipo que retorna en las funciones.

si queremos podemos agregarle readonly en los tipos para que sea solo de lectura (lo hace inmutable en tiempo de desarrollo, hasta que transpila en js)

Para tipar funciones se hace asi

fn: (arg: string) ⇒ void 

 se intenta evitar poner solo fn: Function por que es lo mismo que any

los tipos propios se ahcen es pascalCase primero mayus

optional chaining:

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled.png)

otro ejeplo es esto 

```jsx
if (a !== null) const abc = carvas.getContext() 
//
const ctx = canvas?.getContext()
```

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%201.png)

eso es intersection types

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%202.png)

eso es type from function return

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%203.png)

arrays 

```jsx
const lenguajes = [] //eso es type never no se le puede agregar nada
const forma1 : string[] = [] // array de strings
const forma2 : (string | number)[] = [] // array de strings o number
const forma3 : Array<string> = [] // array de strings
```

ej de tuplas (array con un numero fijo de elementos) ej useState

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%204.png)

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%205.png)

Enums

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%206.png)

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%207.png)

type assertions

son serciones de tipos, se obvliga a que lo tratemos como queremos.  

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%208.png)

en el primer ejemplo se evitar usar el type assertion. typescript deduce que canbas es un htmlcanvas 

en el segundo ejemplo si no enceuntra canvas crashearia. (se evita errores en tiempon de ejecucion)

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%209.png)

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%2010.png)

un ejemplo de as 

![Untitled](deuda%20tecnica%20f080775229ab4fd5b5f806a5a5c16afc/Untitled%2011.png)

INTERFAz

contratode un objeto, defino comoo es el objeto

En TypeScript, tanto las interfaces como los tipos (type) son herramientas utilizadas para definir la estructura y los contratos de los tipos de datos. Aunque tienen similitudes, también tienen diferencias clave en cuanto a su funcionalidad y uso. Aquí tienes una explicación de las diferencias principales:

1. Sintaxis:
    - Interface: La sintaxis para definir una interfaz es **`interface NombreInterfaz { ... }`**. Por ejemplo, **`interface Persona { ... }`**.
    - Type: La sintaxis para definir un tipo es **`type NombreTipo = ...`**. Por ejemplo, **`type Persona = ...`**.
2. Extensibilidad:
    - Interface: Las interfaces pueden extenderse utilizando la palabra clave **`extends`**. Puedes crear una nueva interfaz que herede las propiedades de otra interfaz. Por ejemplo, **`interface Estudiante extends Persona { ... }`**.
    - Type: Los tipos no pueden extenderse directamente. Sin embargo, puedes utilizar otras técnicas como la intersección (**`&`**) y la unión (**`|`**) para combinar múltiples tipos y lograr comportamientos similares.
3. Reutilización:
    - Interface: Puedes implementar múltiples interfaces en una sola declaración. Es posible que una clase o estructura de datos implemente varias interfaces al mismo tiempo.
    - Type: Los tipos no admiten implementación múltiple directamente. Cada tipo se define de forma independiente y no se pueden combinar de la misma manera que las interfaces.
4. Compatibilidad:
    - Interface: Las interfaces pueden ser fusionadas cuando tienen el mismo nombre, lo que significa que se pueden agregar propiedades a una interfaz existente en diferentes declaraciones.
    - Type: Los tipos no pueden fusionarse. Si intentas definir un tipo con el mismo nombre, se producirá un error.
5. Inferencia de tipo:
    - Interface: Las interfaces no pueden ser inferidas automáticamente por el compilador de TypeScript. Debes especificar explícitamente cuándo una clase o estructura de datos implementa una interfaz.
    - Type: Los tipos pueden ser inferidos automáticamente por el compilador de TypeScript en muchas situaciones. No siempre es necesario especificar el tipo de forma explícita.

En general, las interfaces son adecuadas para definir estructuras de datos y contratos en casos donde la extensibilidad y la implementación múltiple son necesarias. Por otro lado, los tipos son más flexibles y permiten trabajar con uniones, intersecciones y otros conceptos más avanzados.

Ambas interfaces y types tienen sus usos y dependiendo del escenario y las necesidades específicas de tu proyecto, puedes elegir utilizar uno u otro.

type guard (se intenta evitar por que se hace un poco vevoso pero ese es un ejemplo)

```tsx
interface Animal {
  mover(): void;
}

interface Perro extends Animal {
  ladrar(): void;
}

function hacerSonido(animal: Animal) {
  if ("ladrar" in animal) {
    animal.ladrar();
  } else {
    animal.mover();
  }
}

```

En este ejemplo, tenemos las interfaces **`Animal`** y **`Perro`**. La interfaz **`Perro`** extiende la interfaz **`Animal`** y agrega el método **`ladrar`**. La función **`hacerSonido`** toma un parámetro **`animal`** de tipo **`Animal`**.

Dentro del bloque condicional **`if ("ladrar" in animal)`**, utilizamos el operador **`in`** para comprobar si la propiedad **`ladrar`** existe en el objeto **`animal`**. Si la propiedad está presente, inferimos que el objeto es de tipo **`Perro`** y podemos llamar al método **`ladrar`**. Si la propiedad no está presente, inferimos que el objeto es de tipo **`Animal`** y llamamos al método **`mover`**.

Este type guard nos permite realizar acciones específicas o acceder a propiedades/métodos específicos según la presencia de ciertas propiedades en un objeto.



