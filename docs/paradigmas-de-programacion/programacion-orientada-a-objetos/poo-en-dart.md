---
sidebar_label: 'Programación orientada a objetos en Dart'
sidebar_position: 2
---

# Programación orientada a objetos en Dart

## Definición de una clase e instanciación de una clase
En dart podemos definir una clase con la palabra clave `class` seguido del nombre que se le quiere dar a la clase. Posteriormente esta el cuerpo de la clase que se encierra entre llaves, aquí se declaran sus propiedades, métodos, getters, setters y constructores. Para poder crear una instancia de la misma clase solo se tiene llamar a un constructor de la clase.

```dart
// Declaración de la clase
class Point {
    final int x;
    final int y;

    // Constructor
    Point(this.x, this.y);

    // Otro constructor de la clase
    Point.fromJson(Map<String, int> json) {
        x = json['x']; // Accede al valor de la clave "x" dentro del mapa y lo asigna a "x" de la instancia
        y = json['y']; // Accede al valor de la clave "y" dentro del mapa y lo asigna a "y" de la instancia
    }
}

void main() {
    var p1 = Point(2, 5); // Instanciación de la clase
}
```

Los nombres de los constructores pueden ser el **mismo nombre de la clase** o el nombre de la clase mas "**.**" y un **identificador**, como si fuera un método. Por ejemplo, el siguiente código crea objetos Point utilizando los constructores Point() y Point.fromJson():

```dart
var p1 = Point(2, 2);
var p2 = Point.fromJson({'x': 1, 'y': 2});
```

El primer constructor `Point()` pide dos números que representan las coordenadas **X** e **Y** para poder crear un punto dentro de un espacio bidimensional. Mientras, el constructor `Point.fromJson()` es capaz de construir un punto a partir de otra estructura "`Map<String, int>`" que contiene, igualmente, coordenadas de un espacio bidimensional.

:::info[Acerca de los Json]
**JSON** es un formato de texto que se utiliza para el almacenamiento, acceso e intercambio de datos. Es un formato de texto sencillo que se deriva de la sintaxis de JavaScript, pero no tiene como objetivo la creación de programas. Dart para procesar este tipo de dato ofrece las funciones `jsonDecode()` y `jsonEncode()` que vienen con el paquete `dart:convert` y transforma el JSON de texto a un `Map<dynamic, dynamic>`.
:::

Algunas clases proporcionan un **constructor constante** que se usan para crear una constante en tiempo de compilación. Estos constructores pueden ser llamados simplemente agregando un `const` antes del constructor de la siguiente manera:

```dart
var p = const ImmutablePoint(2, 2);
```

:::info[Acerca de los datos inmutables]
En el contexto de la programación, la **inmutabilidad** se refiere a la propiedad de un objeto o variable que no se puede modificar después de su creación. La creación de objeto constante al momento de la compilación ayuda al rendimiento del programa resultante.
:::

Dentro de un contexto constante, puede omitir la constante antes de un constructor o literal. Por ejemplo, mira este código, que crea un mapa constante:

```dart
// Muchas constantes para declarar un mapa
const pointAndLine = const {
  'point': const [const ImmutablePoint(0, 0)],
  'line': const [const ImmutablePoint(1, 10), const ImmutablePoint(-2, 11)],
};
```

​Puedes omitir todos los usos excepto el primero de la palabra clave `const`:

```dart
// Puede simplificarse usando un solo const al comienzo de la declaración
const pointAndLine = {
  'point': [ImmutablePoint(0, 0)],
  'line': [ImmutablePoint(1, 10), ImmutablePoint(-2, 11)],
};
```

## Variables de instancia
Las variables de instancia son variables que pertenecen a una clase y se declaran sin la palabra clave `static`. Cada objeto de la clase tiene su propia copia de las variables de instancia. Las variables de instancia se inicializan cuando se crea un objeto de la clase y se pueden acceder a ellas utilizando el objeto.

Asi es como se declaran las variables de instancia:

```dart
class Point {
  double? x; // Declara una variable de tipo double potencialmente nulo llamada "x", iniciada en nulo
  double? y; // Declara "y" inicializada en nulo
  double z = 0; // Declara "z" como un double e inicializa en 0 
}
```

Las variables potencialmente nulas no inicializadas o sin un valor especificado se inicializan en `null`. Una variable que no admite un nulo, obligatoriamente deben ser inicializadas con un valor o mediante los constructores de la clase.

Todas las variables de instancia generan un método **getter** implícito. Las variables de instancia no finales y las variables de instancia finales tardías sin inicializadores también generan un método **setter** implícito.

Los **Getters** y **Setters** son métodos de acceso a los campos/atributos de una clase. Los **Getters** nos permiten obtener los datos de las variables y los **Setters** nos permiten asignar o cambiar su valor. Los Getters y Setters se utilizan para acceder y modificar los valores de los atributos de una clase. Los métodos que permiten acceder al valor de un atributo se denominan *"getters"* y los que fijan el valor de un atributo se denominan *"setters"*.

```dart
class Point {
  double? x; // Declara una variable double potencialmente nula llamada X. Se inicializa en null
  double? y; // Declara una variable double potencialmente nula llamada Y. Se inicializa en null

  // La clase no tiene un constructor definido
}

void main() {
  var p1 = Point(); // Se crea una instancia de Point y se guarda en "p1"

  print(p1.x); // Se imprime el valor de X por consola, en este caso null
  p1.x = 4; // Se usa el setter implícito de x para asignarle a este el valor de 4

  print(p1.x); // Se imprime el valor de X por consola, en este caso 4
  print(p1.y == null) // Imprime si el valor Y es igual a nulo, en este caso es True
}
```

Inicializar una variable de instancia no declarada como `late` en el lugar donde se declara establece el valor cuando se crea la instancia, antes de que se ejecute el constructor y su lista de inicializadores. Como resultado, la expresión de inicialización (después del `=`) de una variable de instancia no declarada como 'late' no puede acceder a 'this', es decir, una propiedad no puede acceder al valor de otra antes de que se cree una instancia de la clase, a no ser que se use el modificador `late` antes de la declaración.

```dart
double initialX = 1.5;

class Point {
  // OK, Puede acceder al valor de "initialX" porque es una variable fuera de la clase
  double? x = initialX;

  // ERROR, No puede acceder al valor de x ya que no tiene el modificador late
  double? y = this.x;

  // OK, Puede acceder al valor de x después de la inicialización de la instancia
  late double? z = this.x;

  // Constructor de la clase
  Point(this.x, this.y);
}
```

Las variables de instancia pueden ser finales, en cuyo caso deben establecerse exactamente una vez. Inicialice las variables de instancia finales, no tardías, en la declaración, usando un parámetro de constructor o usando la lista de inicializadores de un constructor:

```dart
class ProfileMark {
  // A esta variable se le asignara un valor a traves del constructor y esta permanecerá constante a lo largo del tiempo
  final String name;
  // Esta variable ya tiene un valor por defecto y es final por lo que no puede ser inicializada en el constructor
  final DateTime start = DateTime.now();

  // Constructor principal
  ProfileMark(this.name);

  // Constructor "unnamed"
  ProfileMark.unnamed() : name = '';
}
```

## Métodos

Los métodos son funciones que proporcionan comportamiento a un objeto.
​
### Métodos de la instancia
Los métodos de instancia en objetos pueden acceder a variables de instancia y a `this`. El método `distanciaTo()` del siguiente ejemplo es un método de instancia:

```dart
import 'dart:math';

class Point {
  final double x;
  final double y;

  Point(this.x, this.y);

  double distanceTo(Point other) {
    var dx = x - other.x; // Guarda el valor de X del otro punto en "dx"
    var dy = y - other.y; // Guarda el valor de Y del otro punto en "dy"
    return sqrt(dx * dx + dy * dy); // Retorna la raíz cuadrada de la suma de dx al cuadrado y dy al cuadrado.
  }
}
```
En la clase `Point` se declara un método `distanceTo` que recibe otro objeto `Point` como parámetro y retorna un decimal que representara la distancia entre un punto y otro.

### Operadores
|  \<  |   +   |  \|  |  >>>  |
| ---- | ----- | ---- | ----- |
|  >   |   /   |  ^   |  []   |
|  \<=  |   ~/  |  &   |  []=  |
|  >=  |   *   |  \<\<  |  ~  |
|  -   |   %   |  >>  |  ==   |

:::info[NOTA]
Puede que hayas notado que algunos operadores, como `!=`, no están en la lista de nombres. Esto se debe a que son simplemente **azúcar sintáctico**, es decir, si no está explícitamente mencionado en la lista, no es porque no exista, sino porque es una forma abreviada o sintáctica de expresar algo más. Por ejemplo `e1 != e2` es equivalente a escribir `!(e1 == e2)`. Esto significa que la comprobación de desigualdad `!=` se traduce internamente en la negación de la comprobación de igualdad `==`.
:::

En Dart, los operadores no son simplemente palabras clave, sino que se definen mediante funciones con el nombre `operator` seguido del símbolo del operador. Aquí hay un ejemplo para ilustrar esto:

```dart
class Vector {
  final int x, y;

  Vector(this.x, this.y);

  // Se sobrescribe la funcionalidad del operador "+" para la clase Vector
  Vector operator +(Vector v) => Vector(x + v.x, y + v.y);
  // Se sobrescribe la funcionalidad del operador "-" para la clase Vector
  Vector operator -(Vector v) => Vector(x - v.x, y - v.y);

  @override
  bool operator ==(Object other) => // Esto es una función de flecha
      other is Vector && x == other.x && y == other.y;

  @override
  int get hashCode => Object.hash(x, y);
}

// Uso de la clase Vector
void main() {
  var vector1 = Vector(1, 2);
  var vector2 = Vector(2, 3);

  // Uso del operador "+"
  var suma = vector1 + vector2; // Se obtiene un tercer vector de X=3 y Y=5 ([3, 5])
}
```
En este ejemplo se sobrescribe la funcionalidad de los operadores **"+"**, **"-"** y **"=="**. Tomando como ejemplo la función de suma, esta se modifica para sumar de una forma "especial" los datos que sean vectores. Lo que hace es tomar otro vector como parámetro.

En este ejemplo se parte de una clase `Vector` que representa un vector de dos dimensiones en la vida real. En matemática, se sabe que dos vectores pueden sumarse entre si, sin embargo, en Dart, al tratarse de una estructura "desconocida" creada por nosotros, no se sabe como es la suma entre dos vectores, por lo que nosotros tenemos que especificarle a la clase como hacerlo sobrescribiendo la funcionalidad del operador "`+`" u otras operaciones que se tengan en mente. Siguiendo con el ejemplo de la suma, en la clase `Vector` se especifica que esta funcionalidad toma como parámetro a otro vector para formar un nuevo vector cuyo valor "X" sera igual a la suma (normal) de x1 y x2, y cuya "Y" es igual a la suma de y1 e y2. Ej: 
$$
\Large \begin{bmatrix}
1 & 2
\end{bmatrix} + \begin{bmatrix}
2 & 3
\end{bmatrix} = \begin{bmatrix}
3 & 5
\end{bmatrix}
$$
### Getters y Setters
Los getters y setters son métodos especiales que brindan acceso de lectura y escritura a las propiedades de un objeto. Recuerda que cada variable de instancia tiene un getter implícito, además de un setter si corresponde. Puede crear propiedades adicionales implementando getters y setters, utilizando las palabras clave `get` y `set`:

```dart
class Cuadrado {
  double lado;

  Cuadrado(this.lado);

  // Propiedad calculada: área
  double get area => lado * lado;

  // Propiedad calculada: perímetro
  double get perimetro => 4 * lado;
}

void main() {
  // Crear una instancia de Cuadrado con un lado de longitud 5
  var cuadrado = Cuadrado(5);

  // Obtener y mostrar el área
  print('Área del cuadrado: ${cuadrado.area}'); // Imprime 25

  // Obtener y mostrar el perímetro
  print('Perímetro del cuadrado: ${cuadrado.perimetro}'); // Imprime 20
}
```
En este ejemplo:

1. La clase `Cuadrado` tiene una propiedad `lado`, que se inicializa mediante el constructor.
2. Se define una propiedad calculada `area`, que devuelve el área del cuadrado multiplicando el lado por sí mismo.
3. Se define otra propiedad calculada `perimetro`, que devuelve el perímetro del cuadrado calculado como 4 veces el lado.
4. En la función `main()`, se crea una instancia de Cuadrado con un lado de longitud 5.
5. Se obtiene y muestra el área del cuadrado usando la propiedad calculada `area`.
6. Se obtiene y muestra el perímetro del cuadrado usando la propiedad calculada `perimetro`.

```dart
class Persona {
  String _nombre; // La convención _ indica que es una variable privada
  int _edad;

  Persona(this._nombre, this._edad);

  // Getter para obtener el nombre
  String get nombre => _nombre;

  // Setter para actualizar el nombre
  set nombre(String nuevoNombre) {
    if (nuevoNombre.isNotEmpty) {
      _nombre = nuevoNombre;
    }
  }

  // Getter para obtener la edad
  int get edad => _edad;

  // Setter para actualizar la edad
  set edad(int nuevaEdad) {
    if (nuevaEdad >= 0) {
      _edad = nuevaEdad;
    }
  }
}

void main() {
  // Crear una instancia de Persona
  var persona = Persona("Juan", 25);

  // Obtener y mostrar el nombre y la edad
  print('Nombre: ${persona.nombre}, Edad: ${persona.edad}');

  // Intentar actualizar el nombre con un valor vacío (no debería cambiar)
  persona.nombre = '';
  print('Nombre después de intentar actualizar con valor vacío: ${persona.nombre}');

  // Actualizar la edad
  persona.edad = 30;

  // Mostrar la nueva edad
  print('Edad después de actualizar: ${persona.edad}');
}
```
En este ejemplo:

1. La clase `Persona` tiene propiedades `_nombre` y `_edad`, que están marcadas como privadas utilizando la convención _.
2. Se definen getters (`nombre` y `edad`) para obtener los valores de las propiedades privadas.
3. Se definen setters (`nombre` y `edad`) que permiten actualizar las propiedades privadas, pero con lógica adicional. En este caso, se verifica que el nuevo nombre no esté vacío y que la nueva edad sea un valor no negativo.
4. En la función `main()`, se crea una instancia de `Persona` y se muestra el nombre y la edad iniciales.
5. Se intenta actualizar el nombre con un valor vacío, pero debido a la lógica en el setter, el nombre no cambia.
6. Se actualiza la edad y se muestra la nueva edad.

### Métodos en clases abstractas
Los métodos de instancia, getters y setters pueden ser abstractos y definir una interfaz pero dejar su implementación en manos de otras clases. Los métodos abstractos sólo pueden existir en clases abstractas o mixins.

Para hacer que un método sea abstracto, use un punto y coma (;) en lugar del cuerpo del método:

```dart
// Clase Abstracta
abstract class Doer {
  // Aquí se definen los getters, setters y métodos abstractos

  void doSomething(); // Definición de un método abstracto
}

class EffectiveDoer extends Doer {
  @override
  void doSomething() {
    // Se especifica la función del método
  }
}
```

## Métodos y propiedades estáticos
En Dart, los métodos y propiedades estáticas pertenecen a la clase en sí misma, en lugar de a una instancia específica de la clase. Se pueden acceder directamente a través del nombre de la clase, sin necesidad de crear una instancia de esa clase.

### Métodos estáticos
Un método estático se define usando la palabra clave static y no tiene acceso a las instancias de la clase. Puedes invocar un método estático directamente en la clase, sin necesidad de crear un objeto de esa clase. Aquí hay un ejemplo:

```dart
class MiClase {
  static void metodoEstatico() {
    print("Este es un método estático.");
  }
}

void main() {
  // Invocar el método estático sin crear una instancia de la clase
  MiClase.metodoEstatico(); // Imprime "Este es un método estático."
}
```
En este ejemplo, `metodoEstatico` es un método estático de `MiClase`. Se puede llamar directamente en la clase sin necesidad de crear un objeto `MiClase`.

### Propiedad Estatica
Una propiedad estática es similar a un método estático, pero representa un valor que pertenece a la clase en lugar de a una instancia específica. Se define utilizando la palabra clave static. Aquí hay un ejemplo:

```dart
class MiClase {
  static int propiedadEstatica = 42;
}

void main() {
  // Acceder a la propiedad estática directamente en la clase
  print(MiClase.propiedadEstatica); // Imprime 42
}
```
En este ejemplo, `propiedadEstatica` es una propiedad estática de `MiClase`. Puedes acceder directamente a la propiedad utilizando el nombre de la clase.

### Uso de Métodos y Propiedades Estáticas:
1. Los métodos y propiedades estáticas son útiles cuando se desea tener funcionalidades asociadas a la clase en sí misma, y no a instancias específicas de esa clase.
2. Se accede a los métodos y propiedades estáticas directamente a través del nombre de la clase, sin necesidad de crear instancias.
3. Son útiles para situaciones en las que la funcionalidad no depende del estado de una instancia particular, sino que es independiente de las instancias.
5. No pueden acceder a las variables de instancia ni usar la palabra clave `this`, ya que no están asociados a instancias particulares.
6. Los métodos y propiedades estáticas son declarados utilizando la palabra clave `static` antes de su declaración.

<!-- ## Ejemplo Practico -->