# Hoisting

Falta hoisting con funciones let y const temporal dead zone etc

En JavaScript, las declaraciones (por ejemplo, de variables o funciones) se mueven al principio de su [scope](https://www.w3schools.com/js/js_scope.asp) o ámbito. Este comportamiento se conoce como [hoisting](https://developer.mozilla.org/es/docs/Glossary/Hoisting) y es muy importante tenerlo en cuenta a la hora de programar para prevenir posibles errores.

Teniendo en cuenta cómo funciona el hoisting, **podemos llamar a una función y definirla más abajo**, porque automáticamente JS la “subirá”. Así, este código funciona correctamente:

```
add();function add() {
   var myNumber = 4;
   console.log(myNumber + myNumber);
}
```

Porque, aproximadamente, JS está haciendo:

```
function add() {
    var myNumber;
    myNumber = 4;
    console.log(myNumber + myNumber);
}add();
```

En el caso de las **variables, es muy importante tener en cuenta que el hoisting solo se aplica a la declaración**, y no a su asignación.

Por lo tanto, **NO** podríamos escribir esto:

```
//Erroradd();function add() {
    console.log(myNumber + myNumber);
}var myNumber = 4;
```

Es esencial quedarnos con dos conceptos:

- Las funciones siempre se mueven arriba del scope. Por lo tanto, podemos elegir donde declararlas y usarlas.
- La declaración de las variables se mueven arriba del scope, pero no la asignación. Antes de usar una variable, habrá que crearla y asignarla.