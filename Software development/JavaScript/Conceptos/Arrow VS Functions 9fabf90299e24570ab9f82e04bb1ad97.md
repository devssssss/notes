# Arrow VS Functions

```
function iniciar() {
  // Código
}
```

Si quisieras invocar una de estas funciones, como la de nuestro ejemplo, tendrías que llamarla así:

```
iniciar();
```

Además también es posible asignar cualquier función a una variable, tal y como hacemos en este ejemplo:

```
const iniciar = function iniciar() {
  // Código
}

iniciar();
Si así lo prefieres, también puedes declarar estas funciones como anónimas, de modo que carezcan de nombre. La única diferencia entre una función anónima y una con nombre, es que en caso de que ocurra un error, no verás el nombre de la función en la traza que se muestre. Aquí un ejemplo de una función anónima:

const iniciar = function () {
  // Código
}

iniciar();
También podemos pasar parámetros a la función independientemente de cómo la declaremos:

function iniciar(param1, param2) {
  // Código
}

iniciar('Soy', 'Edu!');
```

Las **[funciones flecha de JavaScript](https://www.neoguias.com/funciones-flecha-es6/)** fueron introducidas en la versión ES6 de JavaScript, que apareció en el año 2015. Son algo así como una versión adicional con respecto a las funciones normales. Al igual que las funciones anónimas, carecen de nombre. Podrás asignarlas a una variable, pero el nombre de la variable será eso mismo, el nombre de la variable, no el de la función.

Para declarar estas funciones se declara primero una variable y luego, tras los posibles parámetros, se escribe el conjunto de símbolos **`=>`**, que son la representación de una flecha. El nombre de las funciones flecha viene precisamente de este símbolo. Tras la flecha, se coloca el cuerpo de la función entre llaves. He aquí un ejemplo:

```
const iniciar = () => {
  // Código
}

iniciar();
```

En caso de que tengamos un solo parámetro, podemos obviar los paréntesis:

```
const iniciar = param => {
  // Código
}

iniciar();
```

En caso contrario, como cuando tenemos dos o más parámetros o cuando no tenemos ninguno, los paréntesis son obligatorios.

Por otro lado, en caso de que la función solamente incluya una sentencia, es posible obviar las llaves de la función. En este caso, se sobreentiende que hay una sentencia **`return`**, por lo que el resultado de la sentencia es devuelto por la función:

```
const iniciar = param => 'Soy ' + param;
iniciar('Edu');
```

Si quieres más información, puedes consultar con más detalle **[cómo se utilizan las funciones flecha](https://www.neoguias.com/funciones-flecha-es6/)**.

## **Las diferencias**

Tal y como hemos visto, las diferencias en lo que concierne a la sintaxis son bastante grandes. Sin embargo, por ahora no son muy diferentes en cuanto a su funcionalidad. Además, tanto las funciones normales como las funciones flecha pueden ser usadas como métodos de cualquier clase usando la misma sintaxis.

Sin embargo existe una diferencia bastante grande entre los dos tipos de función. Hablamos del trato que cada tipo de función hace del elemento **`this`** en el cuerpo de la función. Vamos a proponer el siguiente ejemplo:

```
const coche = {
  marca: 'Ford',
  modelo: 'Mustang',
  arrancar: function() {
    console.log(`Arrancando el coche ${this.marca} ${this.modelo}`);
  },
  parar: () => {
    console.log(`Parando el coche ${this.marca} ${this.modelo}`);
  }
}
```

La función **`arrancar()`** es una función normal o estándar, mientras que la función **`parar()`** es una función flecha. Vamos a ver el trato que se le da **`this`** en cada caso:

- En la función `arrancar()`, la palabra reservada `this` hace referencia al objeto `coche`, ya que `this` hace referencia al propio ámbito en el que se define la función.
- Sin embargo, en la función `frenar()`, la palabra `this` no hace referencia al objeto `coche`, sino que hace referencia al ámbito en el que está definida la constante `coche`. Es decir, al contexto padre que está por encima del objeto.

En las funciones flecha, **`this`** no hace referencia a la instancia del objeto en el que se define, sino que hace referencia al ámbito al que **`this`** hace referencia externamente. Esto significa que las funciones flecha no son la mejor opción a la hora definir un método de un objeto, ya que habitualmente siempre querrás tener acceso al objeto dentro de al función. En cualquier otro caso, el uso de las funciones flecha es lo que se recomienda.

[https://www.neoguias.com/funciones-flecha-es6/#Que_son_las_Funciones_Flecha](https://www.neoguias.com/funciones-flecha-es6/#Que_son_las_Funciones_Flecha)