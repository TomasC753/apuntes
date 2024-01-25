---
sidebar_position: 2
---
# Lenguajes de Programación
Un lenguaje de programación es un lenguaje formal (o artificial, es decir, un lenguaje con reglas gramaticales bien definidas) que proporciona a una persona, en este caso el programador, la capacidad y habilidad de escribir (o programar) una serie de instrucciones o secuencias de órdenes en forma de algoritmos con el fin de controlar el comportamiento físico o lógico de un sistema informático, para que de esa manera se puedan obtener diversas clases de datos o ejecutar determinadas tareas. A todo este conjunto de órdenes escritas mediante un lenguaje de programación se le denomina programa informático.

El lenguaje de programación permite especificar de manera precisa sobre qué datos debe operar un software específico, cómo deben ser almacenados o transmitidos dichos datos, y qué acciones debe tomar el software bajo una variada gama de circunstancias. Todo esto, a través de un lenguaje que intenta estar relativamente próximo al lenguaje humano o natural. Una característica relevante de los lenguajes de programación es precisamente que más de un programador pueda usar un conjunto común de instrucciones que sean comprendidas entre ellos para realizar la construcción de un programa de forma colaborativa.

## Elementos de un Lenguaje de Programación

### Variables y vectores
Las variables son títulos asignados a espacios en memoria para almacenar datos específicos. Son contenedores de datos y por ello se diferencian según el tipo de dato que son capaces de almacenar. En la mayoría de lenguajes de programación se requiere especificar un tipo de variable concreto para guardar un dato específico. Por ejemplo, en Java, si deseamos guardar una cadena de texto debemos especificar que la variable es del tipo String. Por otra parte, en lenguajes como PHP o JavaScript este tipo de especificación de variables no es necesario. Además, existen variables compuestas llamadas vectores. Un vector no es más que un conjunto de bytes consecutivos en memoria y del mismo tipo guardados dentro de una variable contenedor. A continuación, un listado con los tipos de variables y vectores más comunes:

| Tipo de Dato | Descripción |
| ------------ | ----------- |
| Char    | Estas variables contienen un único carácter, es decir, una letra, un signo o un número.|
| Int     | Contienen un número entero. |
| Float   | Contienen un número decimal. |
| String  | Contienen cadenas de texto, o lo que es lo mismo, es un vector con varias variables del tipo Char. |
| Boolean | Solo pueden contener un cero (**false**) o un uno (**true**). |

### Condicionales
Las sentencias condicionales son estructuras de código que indican que, para que cierta parte del programa se ejecute, deben cumplirse ciertas premisas; por ejemplo: que dos valores sean iguales, que un valor exista, que un valor sea mayor que otro… Estos condicionantes por lo general solo se ejecutan una vez a lo largo del programa. Los condicionantes más conocidos y empleados en programación son:

- **if**: Indica una condición para que se ejecute una parte del programa.
- **else if**: Siempre va precedido de un "If" e indica una condición para que se ejecute una parte del programa siempre que no cumpla la condición del if previo y sí se cumpla con la que el "else if" especifique.
- **else**: Siempre precedido de "if" y en ocasiones de "else if". Indica que debe ejecutarse cuando no se cumplan las condiciones previas.

### Bucles
Los bucles son parientes cercanos de los condicionantes, pero ejecutan constantemente un código mientras se cumpla una determinada condición. Los más frecuentes son:

- **for**: Ejecuta un código mientras una variable se encuentre entre 2 determinados parámetros.
- **while**: Ejecuta un código mientras que se cumpla la condición que solicita.

### Funciones
Las funciones se crearon para evitar tener que repetir constantemente fragmentos de código. Una función podría considerarse como una variable que encierra código dentro de si. Por lo tanto, cuando accedemos a dicha variable (la función) en realidad lo que estamos haciendo es ordenar al programa que ejecute un determinado código predefinido anteriormente.

Todos los lenguajes de programación tienen algunos elementos de formación primitivos para la descripción de los datos y de los procesos o transformaciones aplicadas a estos datos (tal como la suma de dos números o la selección de un elemento que forma parte de una colección). Estos elementos primitivos son definidos por reglas sintácticas y semánticas que describen su estructura y significado respectivamente.

### Sintaxis
A la forma visible de un lenguaje de programación se la conoce como sintaxis. La mayoría de los lenguajes de programación son puramente textuales, es decir, utilizan secuencias de texto que incluyen palabras, números y puntuación, de manera similar a los lenguajes naturales escritos. Por otra parte, hay algunos lenguajes de programación que son más gráficos en su naturaleza, utilizando relaciones visuales entre símbolos para especificar un programa.

La sintaxis de un lenguaje de programación describe las combinaciones posibles de los símbolos que forman un programa sintácticamente correcto. El significado que se le da a una combinación de símbolos es manejado por su semántica (ya sea formal o como parte del código duro de la referencia de implementación). La mayoría de los lenguajes son textuales.

### Semántica estática
La semántica estática define las restricciones sobre la estructura de los textos válidos que resulta imposible o muy difícil expresar mediante formalismos sintácticos estándar. Para los lenguajes compilados, la semántica estática básicamente incluye las reglas semánticas que se pueden verificar en el momento de compilar. Por ejemplo el chequeo de que cada identificador sea declarado antes de ser usado (en lenguajes que requieren tales declaraciones) o que las etiquetas en cada brazo de una estructura case sean distintas. Muchas restricciones importantes de este tipo, como la validación de que los identificadores sean usados en los contextos apropiados (por ejemplo no sumar un entero al nombre de una función), o que las llamadas a subrutinas tengan el número y tipo de parámetros adecuado, pueden ser implementadas definiéndolas como reglas en una lógica conocida como sistema de tipos. Otras formas de análisis estáticos, como los análisis de flujo de datos, también pueden ser parte de la semántica estática. Otros lenguajes de programación como **Java** y **C#** tienen un análisis definido de asignaciones, una forma de análisis de flujo de datos, como parte de su semántica estática.

### Sistema de tipos
Se refiere a las reglas que gobiernan el uso de tipos de datos en un lenguaje. Define cómo se pueden combinar y manipular diferentes tipos de datos. Hay varios tipos de sistemas de tipos, y su implementación puede variar según el lenguaje de programación. Aquí hay algunas categorías comunes de sistemas de tipos:

1. **Tipado Estático**: En un sistema de tipado estático, los tipos de variables son verificados en tiempo de compilación. Esto significa que el tipo de cada variable debe ser declarado explícitamente, y el compilador verifica la corrección de los tipos antes de que el programa se ejecute. Ejemplos de lenguajes con tipado estático incluyen Java, C++ y Rust.
2. **Tipado Dinámico**: En un sistema de tipado dinámico, los tipos de variables se verifican en tiempo de ejecución. No es necesario declarar el tipo de variable explícitamente, ya que el tipo se puede determinar durante la ejecución del programa. Python, JavaScript y Ruby son ejemplos de lenguajes con tipado dinámico.
3. **Tipos Fuertes vs. Tipos Débiles**: En un sistema de tipos fuertes, la conversión entre tipos de datos está limitada y se realiza de manera explícita. En un sistema de tipos débiles, la conversión entre tipos puede ocurrir de manera más implícita. Los lenguajes con tipos fuertes tienden a ser más estrictos en cuanto a la compatibilidad de tipos. Por ejemplo, en **Python** (**tipado dinámico**), una operación entre tipos incompatibles generará un error en tiempo de ejecución.
4. **Tipos Simples vs. Tipos Compuestos**: Los tipos simples representan datos individuales (enteros, decimales, caracteres), mientras que los tipos compuestos combinan varios elementos en una sola entidad. Los tipos compuestos pueden ser arrays, estructuras, listas, entre otros. C y Java son ejemplos de lenguajes que admiten ambos tipos de sistemas.
5. **Inferencia de Tipos**: Algunos lenguajes permiten la inferencia de tipos, donde el compilador o el intérprete deduce automáticamente el tipo de una variable según su contexto. Esto reduce la necesidad de declarar explícitamente el tipo de cada variable. Lenguajes como Swift, Kotlin y TypeScript utilizan la inferencia de tipos.
6. **Polimorfismo**: El polimorfismo permite que un mismo código trabaje con diferentes tipos de datos de manera transparente. Puede ser estático (sobrecarga de operadores en tiempo de compilación) o dinámico (sobrescritura de métodos en tiempo de ejecución). Los lenguajes orientados a objetos, como Java y C#, suelen hacer uso de polimorfismo.

### Implementación
La implementación de un lenguaje es la que provee una manera de que se ejecute un programa para una determinada combinación de software y hardware. Existen básicamente dos maneras de implementar un lenguaje: **compilación** e **interpretación**.

- **Compilación:** es el proceso que traduce un programa escrito en un lenguaje de programación a otro lenguaje de programación, generando un programa equivalente que la máquina será capaz de interpretar. Los programas traductores que pueden realizar esta operación se llaman compiladores. Estos, como los programas ensambladores avanzados, pueden generar muchas líneas de código de máquina por cada proposición del programa fuente.
- **Interpretación:** es una asignación de significados a las fórmulas bien formadas de un lenguaje formal. Como los lenguajes formales pueden definirse en términos puramente sintácticos, sus fórmulas bien formadas pueden no ser más que cadenas de símbolos sin ningún significado. Una interpretación otorga significado a esas fórmulas.

