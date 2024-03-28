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
