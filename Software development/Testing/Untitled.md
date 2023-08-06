react testinbg library con jext

tipos de test:
TEST UNITARIOS probar una accion concreta

Test de integracion

MOCKS

END TO END 

**

## 7 principios del testing

  

1. La prueba muestra la presencia de defectos, no su ausencia.
    

1. No se puede probar que no hay defectos. Las pruebas reducen la probabilidad de que queden defectos no descubiertos en el software, pero, incluso si no se encuentran, el proceso de prueba no es una demostración de corrección.
    

3. La prueba exhaustiva es imposible.
    

1. No es posible probar absolutamente todo, excepto en casos triviales. En lugar de intentar realizar pruebas exhaustivas se deberían utilizar el análisis de riesgos, las técnicas de prueba y las prioridades para centrar los esfuerzos de prueba.
    

5. La prueba temprana ahorra tiempo y dinero.
    

1. Mientras antes probemos, mejor.
    

7. Los defectos se agrupan.
    

1. El 80% de los defectos está en el 20% de las causas de estos.
    

9. Cuidado con la paradoja del pesticida.
    

1. Si aplicas las mismas pruebas todo el tiempo deja de ser efectivo. Va a llegar un punto en el que deja de conseguir defectos.
    

11. La prueba se realiza de manera diferente según el contexto.
    
12. La ausencia de errores es una falacia.
    

1.  Creer que un aplicativo no tiene errores, fallas o defectos es una falacia, una ingenuidad profesional. Es no conocer la parte teórica del todo.
    



**

**## Casos de uso

  

Antes de realizar el diseño de los casos de prueba, lo que se debe llevar a cabo es el análisis de los documentos que van a ser la base para la generación de esos casos de prueba. Estos documentos van a asegurar los requisitos del cliente. Generalmente, estos requisitos se encuentran escritos como casos de uso. Un tester debe comprender qué es un caso de uso y cómo diseñar los casos de prueba a partir de estos.

  

Un caso de uso cuenta la historia de cómo un usuario interactúa con un sistema de software para lograr o abandonar un objetivo. Cada caso de uso puede contener múltiples rutas que el usuario sigue, estos caminos son denominados escenario de caso de uso.

  

Un caso de prueba cubre el software más en profundidad y con mayor detalle que un caso de uso. Estos incluyen todas las funciones que el programa es capaz de realizar y deben tener en cuenta el uso de todo tipo de datos de entrada/salida, cada comportamiento esperado y todos los elementos de diseño.**

**## Testing positivo y Testing negativo

  

### Testing positivo (+) 

  

Son aquellos casos de prueba que validan el flujo normal de un sistema bajo prueba. Es decir, flujos que están relacionados a los requisitos funcionales del sistema bajo prueba. 

  

### Testing negativo (-) 

  

Son aquellos casos de prueba que validan flujos no contemplados dentro de los requisitos de un sistema bajo prueba. 

  
  

### Happy Path

  

¿Qué es el happy path testing?

  

Es el único camino con el que se prueba una aplicación a través de escenarios de prueba cuidadosamente diseñados, que deberían recorrer el mismo flujo que realiza un usuario final cuando usa la aplicación de manera regular. Generalmente es la primera forma de prueba que se realiza en una aplicación y se incluye en la categoría de prueba positiva. Su propósito no es encontrar defectos, sino ver que un producto o procedimiento funcione como ha sido diseñado.

Ventajas

  

- Se utiliza para conocer los estándares básicos de la aplicación. Es la primera prueba que se realiza.
    
- Se utiliza para determinar la estabilidad de la aplicación antes de comenzar con otros niveles de prueba.
    
- Ayuda a identificar cualquier problema en una etapa temprana y a ahorrar esfuerzos posteriores. 
    

  

Limitaciones

  

- No garantiza la calidad del producto porque el proceso solo utiliza escenarios de prueba positivos. 
    
- Encontrar este camino único requiere un gran conocimiento del uso de la aplicación y necesidades del cliente.**
**

### ¿Qué debe contener un caso de prueba?

#### Identificador

Puede ser numérico o alfanumérico. La mayoría de herramientas lo generan automáticamente. 

#### Nombre del caso de prueba(conciso)

  

Se debe utilizar una nomenclatura que esté definida, pero, si no existe, lo recomendable es incluir el nombre del módulo al que corresponde el caso de prueba. 

  
  
  

#### Descripción

  

Debe decir qué se va a probar, el ambiente de pruebas y los datos necesarios para ejecutarlo. 

  

#### Precondición 

  

Asunción que debe cumplirse antes de ejecutar el caso de prueba. 

  

#### Pasos

  

Son las acciones que se deben realizar para obtener los resultados. 

  

#### Resultados esperados 

  

Es lo que le indica al probador cuál debería ser la experiencia luego de ejecutar los pasos y determinar si el test falló o no.

  
  
  
**

principios solid etc