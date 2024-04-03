---
sidebar_position: 2
---
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
- Un objeto en **JSON** se encuentra definido por las llaves "\{ \}" y contiene campos que definen los **atributos** de ese **objeto**.
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

## Unidad 2. Protocolos HTTP

### Tema 1. 404 Titulo no encontrado

En el protocolo **HTTP** intervienen dos partes, el servidor y el cliente quien es el que inicia la comunicación con el servidor y el mismo responde un texto con un encabezado (**header**) y un cuerpo (**body**) que determinan ciertos factores, como la información a enviarse y recibirse (en el **body**) y hacia dónde estamos enviándola, asi como nuestras credenciales, que nos identifican y dan acceso a ese servidor, también llamadas metadatos (en el **header**).

#### URL
Las **URL** (**Uniform Resource Locator**) sirven para identificar/localizar un recurso con el cual queremos operar. Tanto en API como en la web, las URL contienen el mismo formato.

Las **URL**s tienen un formato común que consiste en un protocolo seguido por un dominio y una ruta que identifica el recurso específico. Por ejemplo, "http://www.servidor.com/clientes" indica que se está accediendo a la sección de clientes en el servidor.

Dependiendo del tipo de API (**REST** o **SOAP**), la información devuelta puede estar en diferentes formatos. En el caso de las APIs **REST**, la información se devuelve comúnmente en formato **JSON**, mientras que en las APIs **SOAP** se devuelve en formato **XML**.

Para consultar o manipular la información en una API REST, se utilizan los **métodos HTTP** disponibles, también conocidos como **request**. Estos métodos permiten realizar operaciones como obtener datos (**GET**), crear nuevos recursos (**POST**), actualizar recursos existentes (**PUT/PATCH**), o eliminar recursos (**DELETE**).

### Tema 2. Peticiones HTTP via API

Existe una gran cantidad de verbos o request, los mas usados son los siguiente:

- **GET:** Se utiliza para obtener información desde el recurso API y solo es una solicitud de lectura.
- **POST:** Se utiliza para crear un nuevo recurso dentro de una API. El cuerpo del mensaje (body) de solicitud proporciona los detalles del nuevo recurso basándose en la estructura que se haya definido en la arquitectura de la API para ese tipo de elementos en particular.
- **PUT:** Crea o sustituye un recurso, aunque normalmente se lo utiliza para actualizar algún registro en particular. Se debe enviar toda la estructura del body que está definida por la API y enviar allí también el valor nuevo que queremos actualizar.
- **PATCH:** Realiza una actualización parcial de un recurso. El body de la solicitud especifica el conjunto de cambios que se aplican al recurso.
- **DELETE:** Se borra el registro solicitado, normalmente se  detalla en la URL del request.

Las principales diferencias entre POST y PUT son:
1. El método PUT es **idempotente** en HTTP, lo que significa que producirá el mismo resultado si se ejecuta varias veces.
2. El método POST no es **idempotente**, ya que si se ejecuta varias veces se estarían creando varios elementos.
3. El método POST se utiliza para crear una nueva entidad.
4. El método PUT se utiliza para actualizar (reemplazar) una entidad existente. Se debe tener presente que, si en la trama se envía solo una parte de los valores a actualizar, los demás campos se setearán a null o vacío.

#### ¿Cuando utilizar los métodos PUT y POST en REST?

| POST | PUT |
| --- | ---- |
| Para crear nuevos recursos | Para actualizar los recursos existentes |
| Cuando se necesita que el servidor controle la generación de URL de los recursos | Cuando se conozca el "Id" del Objeto |

### Tema 3. Códigos de respuesta

- 1xx Respuestas informativas: Esta respuesta significa que el servidor ha recibido los encabezados de la petición.
  - **101 Switching Protocols:** El servidor acepta el cambio de protocolo propuesto por el navegador
  - **102 Processing:** El servidor aun esta procesando la petición del navegador.
- 2xx Peticiones correctas: Indica que la petición fue recibida correctamente, entendida y aceptada.
  - **200 OK:** Respuesta estándar para peticiones correctas.
  - **201 Created:** La petición ha sido completada y ha resultado en la creación de un nuevo recurso.
  - **202 Accepted:** La petición ha sido aceptada para procesamiento, pero este no ha sido completado.
  - **204 No Content:** La petición ha sido completado con éxito, pero su respuesta no tiene contenido.
- 3xx Redirecciones: El cliente tiene que tomar una acción adicional para completar la petición.
  - **301 Moved Permanently:** Esta y todas las peticiones futuras deberán ser dirigidas a la URL dada.
  - **302 Found:** Este es el código de redirección mas popular.
  - **307 Temporary Redirect:** Se trata de una redirección que debería haber sido hecha con otra URI, pero aun puede ser procesado por la URI proporcionada.
  - **308 Permanent Redirect:** El recurso solicitado por el navegador se encuentra en otro lugar y este cambio es permanente.
- 4xx Errores del cliente:  Para casos en los que el cliente parece haber errado un petición.
  - **400 Bad Request:** el servidor no procesará la solicitud, porque no puede o no debe, debido a algo que es percibido como un error del cliente (por ejemplo, solicitud malformada, sintaxis errónea, etc.). La solicitud contiene sintaxis errónea y no debería repetirse.
  - **401 Authorization Required:** similar al 403 Forbidden, pero específicamente para su uso cuando la autenticación es posible, pero ha fallado o aún no ha sido provista. Vea autenticación HTTP básica y digest access authentication.
  - **403 Forbidden:** la solicitud fue legal, pero el servidor se rehúsa a responderla, dado que el cliente no tiene los privilegios para realizarla. En contraste con una respuesta 401 No autorizado, autenticarse previamente no va a cambiar la respuesta.
  - **404 Not Found:** recurso no encontrado. Se utiliza cuando el servidor web no encuentra la página o recurso solicitado.
  - **405 Method Not Allowed:** una petición fue hecha a una URI utilizando un método de solicitud no soportado por dicha URI. Por ejemplo, cuando se utiliza GET en un formulario que requiere que los datos sean presentados vía POST; o cuando se utiliza PUT en un recurso de solo lectura.
  - **408 Request Timeout:** el cliente falló al continuar la petición, excepto durante la ejecución de videos Adobe Flash cuando solo significa que el usuario cerró la ventana de video o se movió a otro.
  - **409 Conflict:** indica que la solicitud no pudo ser procesada debido a un conflicto con el estado actual del recurso que esta identifica.
  - **410 Gone:** indica que el recurso solicitado ya no está disponible y no lo estará de nuevo. Debería ser utilizado cuando un recurso ha sido quitado de forma permanente.
  - **414 URI Too Long:** la URI de la petición del navegador es demasiado grande y por ese motivo el servidor no la procesa.
  - **428 Precondition Required:** el servidor requiere que la petición del navegador sea condicional (este tipo de peticiones evitan los problemas producidos al modificar con PUT un recurso que ha sido modificado por otra parte).
  - **429 Too Many Requests:** hay muchas conexiones desde esta dirección de internet.
  - **431 Request Header Fields Too Large:** el servidor no puede procesar la petición, porque una de las cabeceras de la petición es demasiado grande. Este error también se produce cuando la suma del tamaño de todas las peticiones es demasiado grande.
- 5xx Errores del servidor: Indica casos en los cuales el servidor tiene registrado, aún antes de servir la solicitud, que esta errado o es incapaz de ejecutar la petición
  - **500 Internal Server Error:** es un código comúnmente emitido por aplicaciones empotradas en servidores web, las cuales que generan contenido dinámicamente, por ejemplo, aplicaciones montadas en IIS o Tomcat, cuando se encuentran con situaciones de error ajenas a la naturaleza del servidor web.
  - **502 Bad Gateway:** el servidor está actuando de proxy o gateway, y ha recibido una respuesta inválida del otro servidor, por lo que no puede responder adecuadamente a la petición del navegador.
  - **503 Service Temporarily Unavailable:** el servidor no puede responder a la petición del navegador porque está congestionado o está realizando tareas de mantenimiento.
  - **504 Gateway Timeout:** el servidor está actuando de proxy o gateway, y no ha recibido a tiempo una respuesta del otro servidor, por lo que no puede responder adecuadamente a la petición del navegador.

Estos códigos de estado ayudan a hacer el troubleshooting necesario para detectar si todo va de acuerdo con lo esperado o si existe algún inconveniente y de donde proviene.

### Tema 4. Troubleshooting básico
El **Troubleshooting** Se refiere al proceso de identificar, diagnosticar y resolver problemas en un sistema o proceso, en el caso de las APIs, esto implica detectar y solucionar errores en las solicitudes o respuestas.

Para hacer un troubleshooting básico se pueden tener en cuenta las siguientes cuestiones:
1. ¿Es nuestro código de autorización válido y esta correctamente escrito?
2. ¿La URL esta bien escrita?
3. Si la URL cuenta con variables, ¿estas no fueron modificadas?
4. ¿Estamos usando el método correcto para la API a la que intentamos conectarnos?
5. ¿Tenemos problemas de conectividad?
6. ¿El protocolo de la URL está bien escrito?
7. Si estamos enviando una query en nuestra URL (identificable por el signo ‘=?’ en la URL), ¿está bien escrita?
8. Si estamos enviando una query con una búsqueda por fecha, ¿el formato de la fecha está bien escrito?. El formato en JSON es de **AAAA-MM-DDTHH:MM:SS.ZZHH**, donde ZZHH corresponde a zona horaria y se escribe con 3 números y una letra
9. Si estamos utilizando una solicitud para enviar información (PUT, POST, PATCH), ¿la estructura del JSON en el cuerpo del mensaje se encuentra correctamente escrita? ¿Es la estructura que el servidor está esperando?
10. Si estamos enviando información en el body y dicho tipo de dato es un string, ¿estamos enviando algún carácter especial que puede no ser válido?
