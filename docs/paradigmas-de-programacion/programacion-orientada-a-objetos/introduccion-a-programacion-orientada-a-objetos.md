---
sidebar_label: 'Introducción a Programación Orientada a Objetos (POO)'
sidebar_position: 1
---
# Introducción a Programación Orientada a Objetos (POO)

La programación Orientada a objetos se define como un paradigma de la programación, una manera de programar específica, donde se organiza el código en unidades denominadas clases, de las cuales se crean objetos que se relacionan entre sí para conseguir los objetivos de las aplicaciones.

Podemos entender la programación Orientada a objetos (POO) como una forma especial de programar, más cercana a como expresaríamos las cosas en la vida real que otros tipos de programación, que permite diseñar mejor las aplicaciones, llegando a mayores cotas de complejidad, sin que el código se vuelva inmanejable.

## Motivación de la programación orientada a objetos
Durante años, los programadores se han dedicado a construir aplicaciones muy parecidas que resolvían una y otra vez los mismos problemas. Para conseguir que los esfuerzos de los programadores puedan ser reutilizados se creó la posibilidad de utilizar módulos. El primer módulo existente fue la función, que somos capaces de escribir una vez e invocar cualquier número de veces.

Sin embargo, la función se centra mucho en aportar una funcionalidad dada, pero no tiene tanto interés con los datos. Es cierto que la función puede recibir datos como parámetros y puede devolverlos, pero los trata de una estructura muy volátil, centrada en las operaciones. Simplemente hace su trabajo, procesando los parámetros recibidos y devuelve una respuesta.

En las aplicaciones en realidad los datos están muy ligados a la funcionalidad. Por ejemplo podemos imaginar un punto que se mueve por la pantalla. El punto tiene unas coordenadas y podemos trasladarlo de una posición a otra, sumando o restando valores a sus coordenadas. Antes de la programación orientada a objetos ocurría que cada coordenada del punto tenía que guardarse en una variable diferente (dos variables para ser exacto: x, y) y las funciones de traslación estaban almacenadas por otra parte. Esta situación no facilitaba la organización del código ni tampoco su reutilización.

Con la Programación Orientada a Objetos se buscaba resolver estas situaciones, creando unas mejores condiciones para poder desarrollar aplicaciones cada vez más complejas, sin que el código se volviera un caos. Además, se pretendía dar una de pautas para realizar las cosas de manera que otras personas puedan utilizarlas y adelantar su trabajo, lo que deriva en mayores facilidades para la reutilización del código.

## Principios Fundamentales

### Clases y objetos:
- Una clase es una plantilla que define la estructura y el comportamiento de un objeto.
- Un objeto es una instancia de una clase, con datos específicos y la capacidad de realizar operaciones definidas por la clase.

Se puede pensar una clase como un plano para construir casas. El plano especifica cómo se deben construir las casas, qué habitaciones tendrán, y cómo estarán conectadas. Cada casa construida según ese plano sería un objeto.

![](https://miro.medium.com/v2/resize:fit:828/format:webp/1*d2crhvTjaWQzEyeF7GEElA.png)
- Cuando construimos una casa el arquitecto diseña los planos (blueprints) que definen cómo debe ser construida la casa. A esta plantilla, en programación se la conocemos como clase.
- A una casa construida a partir de la plantilla se la conoce como instancia de la clase.
```dart
class Auto {
    // Propiedades
    String marca;
    String modelo;
    double velocidad;

    // Constructor
    Auto({
        required this.marca,
        required this.modelo,
        this.velocidad = 0 
    });

    void acelerar(int incremento) {
        velocidad += incremento;
    }

    void frenar(int decremento) {
        velocidad -= decremento;
    }
}

// Creación de objetos (instancias) de la clase Auto
void main() {
    Auto auto1 = Auto(marca: "Toyota", modelo: "Corolla");
    Auto auto2 = Auto(marca: "volkswagen", modelo: "Suran My2019")
}
```

En este ejemplo, `Auto` es la clase que define la estructura y comportamiento de los autos. `auto1` y `auto2` son objetos (instancias) de esa clase, cada uno con sus propios datos (marca, modelo, velocidad) y capaces de realizar las operaciones definidas en la clase (acelerar y frenar).

### Conceptos Clave:

#### Atributos:
- Son variables que almacenan datos asociados con un objeto.
- Representan las propiedades de un objeto.

#### Métodos:
- Son funciones que definen el comportamiento de un objeto.
- Realizan operaciones sobre los datos de la clase.

#### Constructores:
- Métodos especiales llamados al crear un objeto.
- Inicializan los atributos del objeto.

### Abstracción
La abstracción en la programación orientada a objetos (POO) es un concepto fundamental que nos permite simplificar y organizar nuestro código de manera eficiente. En términos simples, la abstracción se enfoca en la visión externa de un objeto, separando el comportamiento específico de un objeto.  Esto se logra mediante la creación de una interfaz que define los métodos que serán implementados por una clase sin necesidad de definir qué harán estos métodos. La interfaz abarca las responsabilidades de un objeto y establece todas las suposiciones que pueda hacer un objeto cliente acerca del comportamiento de un objeto servidor.

En resumen, la abstracción es una técnica que nos permite definir características específicas de un objeto, aquellas que lo distinguen de los demás tipos de objetos y que logran definir límites conceptuales respecto a quien está haciendo dicha abstracción del objeto.

### Encapsulación:
- La encapsulación es el principio de ocultar los detalles internos de un objeto y exponer solo lo necesario para su uso.
- Se logra mediante el uso de modificadores de acceso como público, privado y protegido.

### Herencia:
- La herencia es un mecanismo que permite crear una nueva clase basada en una clase existente, heredando sus atributos y métodos.
- La clase que se hereda se llama clase base o superclase, y la nueva clase se llama clase derivada o subclase.
- La subclase puede extender o modificar la funcionalidad de la superclase.
- Favorece la reutilización del código y la creación de jerarquías de clases.

Piensa en una jerarquía de vehículos. Tienes una clase base llamada `Vehiculo` que tiene propiedades y comportamientos comunes a todos los vehículos. Luego, puedes tener subclases como `Auto` y `Camion` que heredan de la clase base y agregan características específicas.

```dart
// SuperClase
class Vehiculo {
    // Propiedades
    String marca;
    String modelo;
    int velocidad;
    
    // Constructor
    Vehiculo({
        required this.marca,
        required this.modelo,
        this.velocidad = 0
    })
}

// SubClase
class Auto extends Vehiculo {
    // Constructor
    Auto({
        required super.marca,
        required super.modelo
    });
}

// SubClase
class Camion extends Vehiculo {
    // Propiedades exclusivas de un camion
    String tipoDeCarga;
    List<dynamic> carga;

    // Constructor
    Camion({
        required this.tipoDeCarga,
        required super.marca,
        required super.modelo
    });

    // Método exclusivo del camion
    void cargar(List<dynamic> cargamento) {
        carga.addAll(cargamento);
    }
}
```

En este ejemplo, `Auto` y `Camion` extienden de la clase padre `Vehiculo`, el cual hereda las propiedades `marca` y `modelo` a sus hijos y estos últimos tienen la posibilidad de desarrollar métodos y propiedades nuevas como es el caso de la subclase `Camion` que presenta una propiedad `carga` y un método `cargar`.

### Polimorfismo:
- El polimorfismo permite que un objeto se comporte de diferentes maneras según el contexto.
- Puede manifestarse de dos formas: polimorfismo de sobrecarga y polimorfismo de anulación (override).
  - La sobrecarga implica tener múltiples métodos con el mismo nombre pero con diferentes parámetros.
  - La anulación ocurre cuando una subclase redefine un método de la superclase.

Imagina una interfaz de música. Puedes reproducir música desde un teléfono, una computadora o un altavoz, pero el comportamiento de reproducción es diferente en cada dispositivo. Eso es polimorfismo: la capacidad de realizar la misma acción (reproducción) de diferentes maneras según el dispositivo.

```dart title="Ejemplo de polimorfismo de anulación"
abstract class Animal {
    void hacerSonido();
}

class Perro extends Animal {
    @override
    void hacerSonido() {
        print('¡guau guau!');
    }
}

class Gato extends Animal {
    @override
    void hacerSonido() {
        print('Dame comida humano!!');
    }
}

void main() {
    Perro perro1 = Perro();
    Gato gato1 = Gato();

    perro1.hacerSonido(); // Imprime "¡guau guau!"
    gato1.hacerSonido(); // Imprime "Dame comida humano!!"
}
```

En este ejemplo se esta diciendo que `Perro` y `Gato` son animales (extienden de la clase `Animal`) y que todos los animales pueden emitir un sonido a traves del método `hacerSonido`, sin embargo, un perro y un gato emiten sonidos diferentes por lo que cada uno su respectiva subclase anula el método original heredado por la clase padre y lo adapta a su contexto.