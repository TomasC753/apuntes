# Resumen de Introducción a los microservicios

## Unidad 1: Teoría e historia

### Tema 1. Historia de los microservicios

Aparecen con la necesidad d crear sistemas que sean fácilmente escalables y que impliquen un nivel menor de complejidad en cuanto a gestión de proyectos.

Hasta su popularización los desarrollos eran grandes **sistemas monolíticos** que ha medida que crecían su complejidad se hacia mucho mas grande y por ende eran costosos y difíciles de mantener. La solución consistió en distribuir el código respecto a las funciones que tenían dichos sistemas en sistemas mas pequeños, lo que permitió distribuir la carga y "know how" de las funcionalidades en grupos especializados.

#### Características de los microservicios
- **Componentes:** Están compuesto por componentes de software independientes, mantenidos individualmente y sustituibles.
- **Servicios:** Los componentes incluyen servicios disponibles para comunicarse bajo demanda, es decir, para recibir o emitir comunicación
- **Independientes:** Los componentes son independientes entre si, por lo que tampoco se afectan entre si y hasta pueden estar desarrollado en un lenguaje diferente al resto de componentes.
- **Seguridad:** La comunicación entre microservicios esta cifrada con una capa de transporte mutuo (**mTLS**) para proteger los datos durante el proceso.
- **Contenedorización (dockerizacion):** Los microservicios suelen implantarse dentro de contenedores para mayor escalabilidad.

#### Tipos de API

**API Interna o API privada:** Solo pueden ser accedidas por desarrolladores o por otros microservicios. Sirven para comunicar procesos internos dentro de un sistema entre si, reducir el trabajo aislado y mejorar la colaboración.

**API externa o API publica:** Proporciona un medio de intercambio de información con fuentes externas al sistema. Cuando se habla de integrar un sistema basado en microservicios, se habla de integrar APIs externas entre si.

#### Ventaja de los microservicios

- **Escalabilidad:** Dada su independencia, los microservicios son fácilmente escalables, ya que un cambio sobre no afectara a los otros.
- **Modularidad:** Los servicios son módulos independientes que pueden acoplarse o quitarse dependiendo de las necesidades del sistema.
- **Eficacia:** Los servicios son mantenidos por equipos especializados en el mismo, debido a su baja complejidad los miembros pueden capacitarse rápidamente para el mantenimiento de este.
- **Independencia Técnica:** Gracias a su independencia y a la comunicación por métodos **HTTP**, los módulos pueden estar desarrollados con un lenguaje diferente uno del otro, y a un asi el sistema seguir funcionando correctamente.
- **Fácilmente integrable:** Al contar con los métodos HTTP para el intercambio de información, tener una API externa vuelve al sistema fácilmente integrable para cualquier externo.

### Tema 2. SOAP y REST

**SOAP** (**Simple Object Access Protocol** o protocolo de acceso a objetos simples) y **REST** (**Representational State Transfer** o transferencia de estado representacional) son los dos enfoques distintos mas usados para transmitir datos de manera online permitiendo integrar diferentes sistemas o componentes de los mismo. Se valen del uso de estándares para convertir una integración en interoperable.

La diferencia entre estos dos esta en que **SOAP** es un protocolo oficial mantenido por el consorcio **World Wide Web** (**W3C**), mientras que **REST** es un conjunto de principios de arquitectura.

#### SOAP
Fue desarrollado por **Dave Wiener** junto con un equipo de desarrollo de Microsoft y de IBM para posibilitar la comunicación entre un cliente y los servicios de un servidor. Para que esto sea posible el cliente deberá enviar una solicitud a la API y el framework de SOAP determinara la forma que debe adoptar dicha solicitud por medio de unas reglas básicas.

En lugar de darle al cliente solicitante acceso total al servidor, con un protocolo SOAP, se puede limitar el acceso a las funciones que necesita. La arquitectura del mismo, al facilitar un marco al que la aplicación puede incorporarse, permite que sistemas muy diferentes puedan integrarse entre si.

#### REST

REST se caracteriza por su capacidad para transferir representaciones de recursos a través de HTTP, utilizando formatos de datos como **JSON** (**JavaScript Object Notation**), HTML, XML, XLT, Python, PHP o texto sin formato. Se centra en una arquitectura cliente-servidor sin estado, lo que significa que cada solicitud es independiente y no almacena información del cliente entre solicitudes.

Para que una API se considere de **RESTful**, debe cumplir los siguientes criterios:

- Arquitectura cliente-servidor compuesta de clientes, servidores y recursos, con la gestión de solicitudes a través de HTTP.
- Comunicación entre el cliente y el servidor sin estado. Esto implica que no se almacena la información del cliente entre las solicitudes de GET y que cada una de ellas es independiente y está desconectada del resto.
- Datos que pueden almacenarse en caché y optimizan las interacciones entre el cliente y el servidor.
- Una interfaz uniforme entre los elementos, para que la información se transfiera de forma estandarizada. Para ello deben cumplirse las siguientes condiciones:
  - Los recursos solicitados deben ser identificables e independientes de las representaciones enviadas al cliente.
  - El cliente debe poder manipular los recursos a través de la representación que recibe, ya que esta contiene suficiente información para permitirlo.
  - Los mensajes autodescriptivos que se envíen al cliente deben contener la información necesaria para describir cómo debe procesarla.
- Debe contener hipertexto o hipermedios, lo cual significa que, cuando el cliente acceda a algún recurso, debe poder utilizar hipervínculos para buscar las demás acciones que se encuentren disponibles en ese momento.
- Un sistema en capas que organiza en jerarquías invisibles para el cliente cada uno de los servidores (los encargados de la seguridad, del equilibrio de carga, etc.) que participan en la recuperación de la información solicitada.

En comparación con SOAP, REST resulta más fácil de usar y más ligero, ya que no tiene requisitos específicos como la mensajería XML. Su flexibilidad y simplicidad lo hacen más adecuado para entornos donde la velocidad y la eficiencia son prioritarias.

### Tema 3. XML y JSON

#### Estructura de SOAP-XML

Se basa en el metalenguaje **XML** (**eXtensible Markup Language**), el cual se explica como un conjunto de unidades de información necesarias par a la correcta formación del fichero XML.

En la mayoría de los casos, SOAP se integra también en HTTP. El transporte se realiza a través del protocolo y se integra en su estructura.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<!-- Inbound Message -->
<soapenv:Envelope
xmlns:soapenv="http://schemas.xmlsoap.ord/soap/envelope"
xmlns:typ="http://www.mycompany.com/common/ServiceRequestHeader..."
xmlns:typ1="http://www.mycompany.com/salesorder/SalesOrderSearch...">
    <soapenv:Header>
        <typ:ServiceRequestHeader>
            <ApplicationCredential>
                <ID>12345</ID>
                <Credential>password</Credential>
            </ApplicationCredential>
            <ISOLanguageCode>EN</ISOLanguageCode>
            <TransactionModel>
                <UserCredential>
                    <ID />
                </UserCredential>
            </TransactionModel>
        </typ:ServiceRequestHeader>
    </soapenv:Header>
    <soapenv:Body>
        <typ1:ServiceRequest>
            <RequestPreamble>
                <CompanyCode>SG01</CompanyCode>
                <CustomerNumber>593</CustomerNumber>
            </RequestPreamble>
            <OrderSearchRequest>
                <SearchCriteria>
                    <OrderNumber>14912</OrderNumber>
                </SearchCriteria>
            </OrderSearchRequest>
        </typ1:ServiceRequest>
    </soapenv:Body>
</soapenv:Envelope>
```
En ese ejemplo podemos observar un modelo de solicitud XML diferenciando tres estructuras básicas:
- **Envelope:** raíz de la estructura XML, identifica al mensaje SOAP como tal y por ende es obligatoria
- **Header:** aquí se incorpora información referida a cómo debe ser procesado el mensaje. También pueden ir incluidas validaciones de seguridad.
- **Body:** se incluye toda información necesaria para la llamada o respuesta del mensaje. En caso de faltar un campo obligatorio o incluir información no permitida dentro del mismo, se devolverá un error, pero sin detalles del mismo, por lo cual se debe hacer un **troubleshooting manual**, campo a campo para descubrir donde está.

#### Troubleshooting
El proceso de solución de problemas (Troubleshooting) en el contexto de envío de llamadas en formato XML implica identificar y corregir los errores que puedan surgir durante la transmisión. Cuando se recibe un error en respuesta a una llamada XML, el código de error no proporciona detalles específicos sobre la naturaleza del problema. Por lo tanto, es necesario revisar minuciosamente cada campo para asegurarse de que la información enviada sea correcta.

Para verificar la precisión de la información enviada, es fundamental consultar la documentación correspondiente para comprender las opciones disponibles en los campos habilitados del XML. Por ejemplo, un error puede ocurrir si se excede el límite de caracteres permitidos para un campo específico, como en el caso de direcciones que exceden el límite establecido.

Además, pueden surgir errores debido a caracteres inválidos o no admitidos por el XML, como caracteres especiales. Otro escenario común es el error de autenticación, que puede ocurrir si las credenciales proporcionadas son incorrectas.

Es importante destacar que pueden existir diversos tipos de errores, incluso varios dentro del mismo XML. La resolución de problemas requiere habilidad para identificar estos errores basándose en la documentación y el contenido del XML con errores. Una vez identificados, los problemas deben ser corregidos manualmente antes de volver a enviar la llamada XML para su procesamiento correcto.

#### SOAPUI
**SOAPUI** es una herramienta de prueba de servicios web ampliamente utilizada para probar, desarrollar y simular servicios web SOAP y RESTful.
1. Interfaz Gráfica de Usuario (GUI) Amigable: SOAPUI proporciona una interfaz gráfica de usuario intuitiva que facilita la creación, edición y ejecución de pruebas de servicios web.
2. **Soporte para Protocolos:** Soporta tanto el protocolo SOAP (Simple Object Access Protocol) como REST (Representational State Transfer), lo que permite probar una variedad de servicios web.
3. **Creación de Pruebas Funcionales:** Permite a los usuarios crear pruebas funcionales mediante la creación de solicitudes HTTP o SOAP específicas y la definición de las aserciones para verificar las respuestas.
4. **Pruebas de Carga y Rendimiento:** SOAPUI permite la creación de pruebas de carga y rendimiento para evaluar el rendimiento de los servicios web bajo diferentes cargas y condiciones.
5. **Automatización de Pruebas:** Ofrece capacidades de automatización de pruebas, lo que permite ejecutar pruebas de forma automatizada como parte de un proceso de integración continua o de entrega continua (CI/CD).
6. **Soporte para Scripting:** Permite la escritura de scripts en Groovy para personalizar y extender las pruebas según sea necesario.
7. **Entorno de Pruebas Completo:** SOAPUI proporciona un entorno completo para el desarrollo y la ejecución de pruebas de servicios web, incluyendo la capacidad de gestionar entornos de prueba y datos de prueba.
8. **Soporte para Diversas Autenticaciones y Seguridad:** Ofrece soporte para varios mecanismos de autenticación y seguridad, como Basic Auth, WS-Security, OAuth, etc.

#### JSON

Un **JSON** es una cadena cuyo formato recuerda al de los **objetos literales JavaScript**, popularizado por **Douglas Crockford** a mediados de los años 2000. Es posible incluir los mismos tipos de datos básicos dentro de un JSON que en un objeto estándar de Javascript (cadenas, números, arreglos, booleanos, y otros literales de objeto).

```json
[
    {
        "name": "Molecule Man",
        "age": 29,
        "secretIdentify": "Dan Jukes",
        "Powers": [
            "Radiation resistance",
            "Turning tiny",
            "Radiation blast"
        ]
    },
    {
        "name": "Madame Uppercut",
        "age": 39,
        "secretIdentify": "Jane Wilson",
        "Powers": [
            "Million tonne punch",
            "Damage resistance",
            "Superhuman reflexes"
        ]
    }
]
```
- Un objeto en **JSON** se encuentra definido por las llaves "{ }" y contiene campos que definen los **atributos** de ese **objeto**.
- Un **array** se encuentra definido por los corchetes "[ ]" y pueden contener 0, 1 o más **objetos** dentro. Cada uno de estos **objetos** será identificable empezando a contar desde el número 0 (cero)

### Tema 4. Estructura de JSON

JSON es un formato de intercambio de datos ligero diseñado para ser fácilmente leído y escrito por humanos, así como fácilmente interpretado y generado por máquinas. Se basa en un subconjunto del lenguaje de programación **JavaScript Standard ECMA-262** para definir las propiedades y atributos de los objetos.

JSON es un formato de texto independiente del lenguaje, lo que significa que puede ser utilizado con cualquier lenguaje de programación. Sin embargo, sigue convenciones ampliamente conocidas por los programadores de lenguajes de la familia C (C, C++, C#, Java, Javascript, Perl, Python, etc).

JSON está compuesto por dos estructuras básicas:
- Una colección de pares de **clave/valor**, conocida en varios lenguajes como objeto, registro, estructura o lista de claves.
- Una lista ordenada de valores, que se implementa comúnmente como arreglos, vectores, listas o secuencias en la mayoría de los lenguajes de programación.

Las estructuras básicas de JSON son compatibles con prácticamente todos los lenguajes de programación, lo que lo convierte en un formato ideal para el intercambio de datos entre diferentes sistemas y plataformas.

#### Tipos de valores

##### Array
Un array es una colección ordenada de valores. Está rodeado de corchetes y cada valor está separado por una coma.

##### Objetos
Un objeto contiene una clave y un valor. Hay Dos puntos después de cada clave y una coma después de cada valor. El objeto como valor debe seguir la misma regla que un objeto común.

```json title="ejemplo"
{
    "amigos": {
        "nombre": "Pablo",
        "apellido": "Fernandez"
    }
}
```

**String:** Es una secuencia establecida de cero o mas caracteres. Está encerrado entre dos comillas dobles.

**Numero:** El numero en JSON debe ser un entero o un punto flotante como `{"Edad": 30}`.

**Booleano:** Puedes usar verdadero o falso como valor. Ejemplo `{"Casado": true}`.

**Nulo:** Es para mostrar que no hay información. Ejemplo `{"Factor Sanguíneo": null}`.

**Datos JSON almacenados:** Hay dos formas para almacenar datos JSON: Objeto y vector...

```json title="Objeto"
{
    "nombre": "Pablo",
    "apellido": "Fernandez",
    "género": "masculino"
}
```

```json title="Usando vectores" {5-7}
{
    "nombre": "Pablo",
    "apellido": "Fernandez",
    "género": "masculino",
    "hobby": [
        "Música", "Futbol", "Karate"
    ]
}
```

Lo que diferencia esto del método anterior es el cuarto par clave/valor. Hobby es la clave y hay varios valores [Musica, Futbol y Karate] entre corchetes, que representan un vector.

Este proceso funciona utilizando lo que se denomina devoluciones de llamada (**callbacks**), que solicitarán un elemento específico del vector sin obtener un error “del mismo origen” (**same-origin**).

Y, afortunadamente, un array también admite bucles, lo que te permite ejecutar comandos repetidos para buscar múltiples datos, haciendo que el proceso sea más rápido y efectivo.