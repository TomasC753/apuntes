---
sidebar_position: 3
---

# Resumen de Postman y estructura general de pruebas

## Unidad 1. Herramientas y nociones básicas

### Tema 1. Instalando Postman

La versión oficial y gratuita puede encontrarse en su página oficial: [Download Postman | Get Started for Free](https://www.postman.com/downloads/)

#### ¿Como está ordenado Postman?

Primero se be crear un ***"Workspace"***, el espacio donde se tendrán todas las **colecciones** con sus **request**.

#### Menu Lateral

- **Collections:** Cada colección es una carpeta que contiene todas las solicitudes que se han creado en ella.
- **API:** Aquí se pueden incorporar las API creadas por medio de algún repositorio en el que se tenga subido el código y las solicitudes de dicha API.
- **Environments:** Aquí se configuraran los ambientes y las variable que queramos en cada uno de ellos.
- **Mock Servers:** Aquí se pueden simular **endpoints** inexistentes y nos evita crear un **back-end** para hacer pruebas que no requieren de una API en la vida real.
- **Monitors:** En los monitores se le puede pedir a Postman que corra una colección de solicitudes de manera automática en una fecha y hora especifica. Mayormente se utiliza para comprobar la *performance* y el test de regresiones constantes o en múltiples entornos.
- **Flows:** Nos permite crear un **flow de trabajo** con distintas *request*, asi como extraer sus resultados por medio de la *consola de Postman* o unir su respuesta en un único cuerpo de resultado.
- **History:** Es un historial de las últimas solicitudes de API ejecutadas junto con su código de estado al momento de la ejecución de su respuesta.

#### Estructura de una solicitud

En la sección para la construcción de una solicitud se pueden identificar 7 secciones:

- **Params:** en esta pestaña, se puede incluir cualquier query que se quiera hacer sobre la solicitud.

:::note
Las **queries** dentro de una URL se identifican con el símbolo de interrogación de cierre **"?"** al comienzo de la key y del value de la solicitud.

Para concatenar dos queries en la misma request, se utiliza el símbolo **"&"**
:::

- **Authorization:** En esta pestaña se puede controlar el tipo de autorización que debemos presentar en nuestra request. Lo mas normal es trabajar con una **APIKey**, que es un código alfanumérico y cifrado, dada por el dueño de la API, que define una serie de permisos que el usuario va a tener para acceder a la API.

:::note
Otras formas de autenticación son:
- **BasicAuth:** Esta compuesto por un usuario y una contraseña que se envían por el encabezado de la URL. Es la opción menos segura.
- **APIToken:** Es un token cifrado temporal generado por la API una vez que el usuario se autentica con unas credenciales.
- **OAuth 2.0:** Permite validad la identidad del usuario por medio de otros sistemas como Google, Facebook, etc.
:::

- **Header:** Los encabezados son campos que brindan información adicional entre una comunicación HTTP de cliente y servidor. Tienen un formato de par clave-valor y se pueden adjuntar tanto a una solicitud como a una respuesta. La autorización, el tipo de contenido y las cookies son ejemplos de metadatos que se pueden proporcionar en los encabezados HTTP.
- **Body:** Es util es las solicitudes PUT/PATCH/POST, dado que permite indicarle al servidor qué es lo que se debe agregar al endpoint al cual se apunta.
- **Pre-request script:** Permite ejecutar **javaScript** antes de que se ejecute una solicitud. Estos scrips sirven cuando se están corriendo varias solicitudes distintas en un misma colección, cuando se quiere que estas se alimenten de los valores de la solicitud inmediatamente anterior a la ejecutada.
- **Test:** Mediante distintos de scrips de **javaScript** se puede pedir a Postman que ejecute diferentes test sobre dicha solicitud y no devuelva su respuesta.
- **Settings:** Aquí se puede configurar el comportamiento de Postman respecto de las solicitudes. Mayormente sobre cuestiones de seguridad y conexión con la API.

#### Consola de Postman

Por medio de esta herramienta se pueden obtener mucho mas detalles del resultado de las solicitudes. Para acceder a ella se debe dirigir al navbar superior izquierdo **view->show postman console**, o con la combinación de teclas `Alt + Ctrl + C`.

:::note
Cuando ejecutamos scripts con **javaScript**, se puede llamar a la instrucción `console.log()` para imprimir datos o mensajes por la consola. 
:::

### Tema 2. Enviando nuestras primeras solicitudes

Para esta experiencia, se consumirá la API de **Trello** para hacer las solicitudes. A continuación se describen los pasos a realizar...

1. Crear una cuenta en [Trello](https://trello.com/).
2. Crear manualmente un espacio de trabajo y un tablero.
3. Ingresar al siguiente enlace: https://trello.com/app-key. Crear un nuevo "Power-Up" y posteriormente generar una nueva clave API.
4. Generar un token.
5. Una vez obtenida la APIKey, se debe crear una nueva colección en Postman con el nombre que queramos.
6. Crear un nuevo *environment* y guardar la APIKey y el token como variables de entorno.
7. Crear una nueva tarjeta en el tablero creado en Trello y obtener su ID.
   1. Se debe abrir las herramientas de desarrollador e ir a la pestaña de red.
   2. Se tiene que crear la tarjeta en el tablero
   3. Una vez creada, en las herramientas de desarrollador, buscar el ultimo registro con el nombre *"cards"*.
   4. Entrar a la pestaña "respuesta" del registro y encontrar la propiedad ID en el JSON.
8. Crear una nueva **request** cuya URL sera: https://www.trello.com/1/cards/{aqui-la-id-de-tarjeta}
9. En *Params* introducir dos query params (**token** y **key**). En el apartado value se tiene que llamar a la variable de entorno, ej: `{{key}}`. Tendría que verse algo asi:

| Key | Value |
| --- | ----- |
| key | `{{key}}` |
| token | `{{token}}` |

10. Ejecutar la request y esperar un **código 200** con la información de la tarjeta en formato JSON como respuesta.

### Tema 3. Llevando la información a la práctica

Siguiendo con la experiencia anterior, la respuesta de la API tendría que mostrar un código **JSON** similar al siguiente en la pestaña *body*:

```json
{
      // highlight-next-line
    "id": "660b7b470417fb243edd6d4e",
    "badges": {
        "attachmentsByType": {
            "trello": {
                "board": 0,
                "card": 0
            }
        },
        "location": false,
        "votes": 0,
        "viewingMemberVoted": false,
        "subscribed": false,
        "fogbugz": "",
        "checkItems": 0,
        "checkItemsChecked": 0,
        "checkItemsEarliestDue": null,
        "comments": 0,
        "attachments": 0,
        "description": false,
        "due": null,
        "dueComplete": false,
        "start": null
    },
    "checkItemStates": [],
    "closed": false,
    "dueComplete": false,
    "dateLastActivity": "2024-04-02T03:28:07.280Z",
    "desc": "",
    "descData": {
        "emoji": {}
    },
    "due": null,
    "dueReminder": null,
    "email": null,
    // highlight-next-line
    "idBoard": "660b769f5b241c7d65870e24",
    "idChecklists": [],
    "idList": "660b769fa9a33f558b99b159",
    "idMembers": [],
    "idMembersVoted": [],
    "idShort": 3,
    "idAttachmentCover": null,
    "labels": [],
    "idLabels": [],
    "manualCoverAttachment": false,
    // highlight-next-line
    "name": "test",
    "pos": 65537,
    "shortLink": "syNGdXqr",
    "shortUrl": "https://trello.com/c/syNGdXqr",
    "start": null,
    "subscribed": false,
    "url": "https://trello.com/c/syNGdXqr/3-test",
    "cover": {
        "idAttachment": null,
        "color": null,
        "idUploadedBackground": null,
        "size": "normal",
        "brightness": "dark",
        "idPlugin": null
    },
    "isTemplate": false,
    "cardRole": null
}
```

En la respuesta del *request* que se lanzo a **Trello** se pueden observar distintos datos referentes a la tarjeta a la que se apunto. A continuación se citaran algunos ejemplos de datos dentro de la estructura del **JSON**...

- **idBoard:** contiene un valor alfanumérico de 24 caracteres que corresponde al **ID** del *board* (tablero) donde esta la tarjeta.

:::info
Dado que los tableros son entidades separadas de las tarjetas ($$n$$ tarjetas están contenidas en 1 tablero, relación **$$n$$ a 1**). Trello tiene su propio *endpoint* para preguntarle por los tableros diferenciados por **ID**.

Sabiendo que el *endpoint* para acceder a los boards es *"https://trello.com/1/boards"* se puede deducir que para obtener la información del board de la tarjeta se puede usar el *endpoint* *"https://trello.com/1/boards/{id_del_board}"*, donde al ID se lo conoce gracias a la información de la tarjeta en el campo ***idBoard***.
:::

- **name:** contiene un *string* con el nombre asignado a la tarjeta en Trello.

Para la siguiente experiencia se pretende cambiar el nombre de esta tarjeta a traves de un método ***PUT***.

La documentación de Trello especifica que, para hacer un update a una tarjeta de un board, se debe enviar un método PUT y en el body se debe incluir exclusivamente los campos a modificar.

:::warning Contradicción
Según el apunte anterior la actualización parcial de los datos debería de hacerse con el método ***PATCH*** envés de ***PUT***, sin embargo, en la practica depende de como este diseñada y construida la **API** que se esta consumiendo. Es por esto que es importante leer la documentación que las **API**s muchas veces ofrecen.
:::

A continuación, para llevar a cabo la experiencia, se listan los pasos a seguir:

1. Cambiar el tipo de solicitud de ***GET*** a ***PUT*** manteniendo el mismo *endpoint* (https://trello.com/1/cards/{{cardID}}).
2. Dirigirse a la pestaña *body* y seleccionar la opción ***raw*** para escribir un código **JSON**.
3. Como se pretende modificar el campo ***name***, en el JSON solamente se debe incluir dicho campo. El código queda algo asi:

```json
{
   "name": "Cambio de nombre"
}
```
5. Enviar la petición.

El resultado es un **código 200** con el mismo JSON recibido en la primera experiencia, pero con el campo ***name*** actualizado. Si se abre la pagina de Trello también se puede ver reflejado el cambio.

### Tema 4. Configurando variables de entorno y globales
Las variables sirven para evitar repetir información reiteradamente cada vez que creamos una.

Una **variable de entorno** es aquella que se guarda en el entorno de trabajo (***environment***) y solo afecta al mismo junto a todas sus solicitudes y colecciones. Estas variables se pueden crear de manera estática; de manera dinámica; e incluso es posible hacer uso de otras variables de entorno.

La diferencia con un **variable global**, es que esta ultima es accesible desde cualquier entorno en el que se este trabajando.

## Unidad 2. Postman

### Tema 1. Trabajando con aserciones
Uno de los test más simples es el test de aserción, es decir, se espera que un valor $$x$$ me devuelva $$y$$, Postman se encargara de verificar si la condición se cumplió o no. 

Normalmente, se utiliza en peticiones del tipo ***GET***, pero no exclusivamente, por lo que puede utilizarse en todos los tipos de peticiones.

Para el resultado esperado, prime se debe declarar una variable que encapsule el cuerpo de respuesta del JSON, para ello se puede utilizar el siguiente código: 

```javascript
/**
 * Crea una variable que contiene el contenido de la respuesta en formato JSON
*/
var JSONData = pm.response.JSON();

/**
 * Esta es una función que recibe como parámetro un texto que se mostrara en caso de éxito
 * y otra función que contendrá las pruebas.
*/
pm.test("Aquí el texto de respuesta si es válido el resultado", function() {

   /**
    * En esta parte se especifica lo que se está esperando y de donde.
    * En este caso se accede a la propiedad `name` que se espera que el JSON de la respuesta contenga
    * y la función `.to.eql()` lo va a comparar con el valor que le pasemos por parámetro a `eql()`
   */
   pm.expect(JSONData.name).to.eql("valorEsperado");
});
```
Postman ejecuta los *test* apenas se recibe una respuesta de las APIs.

En caso de fallar uno de los *test*, Postman devuelve un "***Fail***" de color rojo junto con una leyenda `AssertionError: expected "valor_actual" to deeply equal "valor_esperado"`, que quiere decir que se esperaba un valor, pero que se recibió otro diferente.

Postman tiene la capacidad de navegar por dentro del Json de respuesta tratándolo como a un objeto. Esto abre las puertas a no solo hacer test de asertividad sino también a obtener los datos contenidos en el JSON y manipularlos a nuestro interés.

Otra utilidad que trae adjunta Postman para este tipo de test son los llamados ***Snippets*** que básicamente son **hints**/**tips**/**pistas** de algunos tipos de test posibles. Por ejemplo, al recibir un **código 200** nos indica si una solicitud se ejecuto correctamente.

### Tema 2. Collection runner
Los ***Collection Runner*** ejecutan automáticamente una serie de solicitudes que hay dentro de una solicitud. Se pueden ejecutar 2 o mas solicitudes de distinto tipo de forma seguida o se puede ejecutar una sola solicitud para distintos elementos.

Por ejemplo, se le puede pedir al "Collection Runner" que repita una solicitud $$X$$ tantas veces como sea necesario de acuerdo con la $$n$$ cantidad de objetos dentro de esa variable, es decir, iterar.
