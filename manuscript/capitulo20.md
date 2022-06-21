# Introducción al desarrollo web

Comprender los fundamentos del desarrollo web es crucial para todo desarrollador JavaScript.  Sumerjámonos en este tema.

> Parte del presente capítulo está inspirado en la en la [documentación del framework PHP Symfony](http://symfony.com/doc/current/introduction/http_fundamentals.html).

## TL;DR

* Los intercambios de información en la web obedecen a un paradigma de **solicitud/respuesta**. Un **cliente** lanza una solicitud al **servidor**, el cual la procesa y devuelve su resultado al cliente.

* **HTTP** (HyperText Transfer Protocol; en español, Protocolo de Transferencia Hipertextual) es el protocolo que permite a dos máquinas comunicarse entre sí en la web. Su versión protegida es **HTTPS**.

* HTTP  se basa en comandos de texto. El **método** HTTP define el tipo de solicitud. Los principales métodos HTTP son `GET` para acceder a un recurso y `POST` para insertar alguna información en el servidor.

* Una respuesta HTTP contiene un **código de estado** indicando el resultado de la solicitud: 200 si es exitoso, 404 para un recurso no encontrado, etc.

* Los recursos web son localizados únicamente por su **URL** (Uniform resource locator; en español, localizador uniforme de recursos). Una URL es un texto con forma de `http://www.misitioweb.com/rutademirecurso/mirecurso`.

* En un escenario tradicional de desarrollo web, las acciones del usuario en una página generan una recarga total después de una solicitud sincrónica al servidor. Otro modelo de desarrollo web apodado **AJAX**  (Asynchronous JavaScript and XML; en español, JavaScript  y XML asíncronos) usa JavaScript y solicitudes HTTP asíncronas para obtener información cuando se necesite y actualizar solo los fragmentos deseados de la página. Esto permite la creación de **aplicaciones web** buscando ofrecer la experiencia de usuario de una aplicación nativa.

* Las solicitudes AJAX de dominio múltiple solo son posibles si el servidor ha sido configurado para aceptarlas al activar el **intercambio de recursos de origen múltiple** (CORS, del inglés cross-origin resource sharing).


* **JSON** (JavaScript Object Notation; en español, escritura de objetos JavaScript), una sintaxis textual para describir información estructurada, ha sustituido a XML como el formato de datos de la web. Un documento JSON es un conjunto de pares nombre/valor.

## Cómo funciona la web

Navegar la web es pan comido. Digamos que quieres leer la historieta del día del popular sitio web [xkcd](https://xkcd.com). Tecleas el texto `"xkcd.com"` en la barra de navegación de tu navegador y listo aparece la historieta (suponiendo que no hay ningún problema de red).

Intentemos comprender qué es lo que está sucediendo detrás de cámaras.

### Servidores web

Para estar en línea, un sitio web tiene que ser publicado en un **servidor**. Este es un tipo especial de máquina cuya tarea es escuchar y responder las peticiones de los clientes. Un servidor que publica recursos en la web lógicamente es llamado servidor **web**.

Más específicamente, una máquina servidor web ejecuta cierto programa (también llamado servidor web) capaz de publicar sitios web. Los más populares son [Apache](http://httpd.apache.org/), [Microsoft IIS](http://www.iis.net/) y [nginx](http://nginx.org).

### Clientes web 

El equipo que solicita un recurso al servidor es llamado **cliente web**. De hecho, el cliente real es un programa que se ejecuta en el equipo. Un tipo de cliente web bien conocido es el **navegador**, un programa especializado en mostrar páginas web. Entre los navegadores web famosos se incluyen [Mozilla Firefox](https://www.mozilla.org/firefox), [Chrome](https://www.google.com/chrome/browser/), [Safari](https://www.apple.com/safari/) y [Opera](http://www.opera.com/fr).

Aunque, no todos los clientes web son navegadores. Por ejemplo, los robots de motores de búsqueda y aplicaciones móviles también se comunican con los servidores y solicitan contenido.

### Comunicación entre clientes y servidores

Los intercambios de información en la web siguen un paradigma de **solicitud/respuesta**.

![Un ejemplo de intercambio web](images/chapter20-01.png)

1. El intercambio es iniciado por el cliente, que envía una **solicitud** al servidor para acceder a cierto recurso web. 
1. El servidor prepara un resultado para la solicitud 
1. El servidor devuelve este resultado al cliente.

Para entenderse entre sí, los clientes y servidores web usan un protocolo en común: HTTP.

## HTTP, el protocolo web 

HTTP, significa **Protocolo de Transferencia Hipertextual** del inglés HyperText Transfer Protocol, es la fundación técnica de la World Wide Web. Es un **protocolo**, un lenguaje que le permite a dos maquinas comunicarse entre sí.

> HTTPS es la versión protegida de HTTP.

Técnicamente hablando, HTTP es un protocolo bastante simple basado en **comandos textuales**.

### Anatomía de una solicitud HTTP

Estudiemos la primera parte del intercambio web descrito anteriormente: la solicitud.

![Un ejemplo de solicitud web](images/chapter20-02.png)

Esta solicitud HTTP viene en forma de un texto multilínea similar al siguiente:

```http
GET / HTTP/1.1
Host: xkcd.com
Accept: text/html
User-Agent: Mozilla/5.0 (Macintosh)
...
```

La línea más importante es la primera. Está contiene:

* El **método** HTTP (el tipo de solicitud, también llamado **comando**). Aquí, el método `GET` indica una solicitud de acceso a un recurso.
* El **recurso** solicitado. Aquí, `/` (símbolo de raíz) indica una solicitud del documento predeterminado.
* La **versión** del protocolo HTTP, aquí 1.1.

Las otras líneas de texto son llamadas **campos de encabezado**. Dan más información acerca de la solicitud del cliente: nombre del servidor (`Host`), tipo de contenido aceptado (`Accept`), detalles del programa del cliente (`User-Agent`). Hay muchos otros posibles campos de encabezado.

Los principales métodos HTTP son `GET` para acceder a un recurso y  `POST` para enviar alguna información al servidor. Existen otros, tales cómo `HEAD`, `PUT` o `DELETE`.

### Anatomía de una respuesta HTTP

Cuando recibe una solicitud HTTP, el servidor busca información internamente. Después construye una respuesta apropiada y la devuelve.

![Un ejemplo de respuesta web](images/chapter20-01.png)

La respuesta HTTP enviada por el servidor luce algo así.

```http
HTTP/1.1 200 OK
Date: Fri, 22 Apr 2017 18:05:05 GMT
Server: Apache/2.2
Content-Type: text/html

<html>
<!-- HTML code of the page -->
<!-- ... -->
</html>
```

La primera línea contiene el **estado** de la respuesta: un número de tres dígitos indicando el resultado de la solicitud. Las otras líneas son campos de encabezado (`Date` fecha, `Content-Type` tipo de conenido, etc.) proporcionando información adicional sobre la respuesta.

Una respuesta HTTP también podría incluir información. En este ejemplo, contiene el código HTML de la página web correspondiente al recurso solicitado.

### Códigos de estado HTTP 

Los códigos de estado HTTP corresponden a diferentes familias, dependiendo de su primer dígito.

Familia | Significado | Ejemplos
--------|---------------|---------
**1xx** | Información |
**2xx** | Logro | 200: solicitud atendida exitosamente 
**3xx** | Redirección |
**4xx** | Error del cliente | 404: recurso no encontrado
**5xx** | Error del servidor | 500: error interno del servidor

> Para una presentación más a fondo del protocolo HTTP, dirigirse a la [Red de Desarrolladores de Mozilla](https://developer.mozilla.org/es/docs/Web/HTTP/Overview).

### Dirigirse a un recurso con una URL

Regularmente se accede a los sitios web usando su dirección, un texto en forma de:

<http://www.nombredelsitio.com/ruta/del/recurso>

Esta dirección puede dividirse en varias subpartes:

* `http://`significa acceso a través del protocolo HTTP.
* `www.nombredelsitio.com` es el **nombre del dominio** del sitio web.
* `/ruta/del/recurso` es la ruta al recurso solicitado.

Una dirección cómo está es llamada URL (del inglés Uniform Resource Locator),  o **localizador uniforme de recursos**. Una URL únicamente describe un recurso web y la forma de solicitarlo.

## De los sitios web a las aplicaciones web

### Los modelos de desarrollo web

En un escenario tradicional de desarrollo web, cuando haces clic en un enlace o envías un formulario, tu navegador envía una solicitud al servidor que devuelve una nueva página web completa adaptada a tu solicitud. Este modelo está sujeto a largos tiempos de carga y a una interactividad limitada. 

Otro modelo de desarrollo web pretende evitar la transmisión de una página web completa por cada acción del usuario. Así es cómo funcionan las cosas en ese modelo:

* Las acciones del usuario en la página son interceptadas a través de controladores de eventos JavaScript.
* Las solicitudes HTTP son enviadas al servidor sin interrumpir la navegación en la página.
* Solo los fragmentos necesitados de la página son actualizados con los resultados de las solicitudes.

Aunque más desafiante, este modelo de desarrollo web puede llevar a cargas reducidas de recursos, una interactividad mejorada y a una experiencia de usuario casi a la par de las aplicaciones nativas.

El conjunto de tecnologías que permiten la creación de aplicaciones web es llamado convencionalmente **AJAX** (del inglés Asynchronous JavaScript and XML, *JavaScript  y XML asíncronos*). Una invocación AJAX es una solicitud HTTP asíncrona hecha para obtener o enviar información de/a un servidor.

### Solicitudes síncronas contra asíncronas

En un intercambio **sincrono** el solicitante espera hasta que obtiene la información necesitada. Una llamada telefónica es un ejemplo de un intercambio síncrono.

En cambio, el solicitante en un intercambio **asíncrono** puede hacer cualquier otra cosa mientras espera que se complete su solicitud. El correo electrónico es un ejemplo de un intercambio asíncrono.

El modelo de desarrollo web tradicional usa solicitudes sincronas: el cliente web es bloqueado mientras espera que el servidor complete su solicitud. El modelo AJAX usa solicitudes asíncronas: la información es obtenida cuando se necesita en segundo plano.

### Solicitudes de dominio múltiple

Por razones de seguridad muchos sitios web tienen una política conservadora respecto a las solicitudes AJAX. Está *política del mismo origen* establece que las solicitudes están limitadas a su dominio de origen: `"http://misitio"` no puede enviar una solicitud a `"http://otrositio"`. Esto evita que algunos servidores sean accesibles a través de invocaciones AJAX. 

La habilitación de solicitudes de dominio múltiple es realizada activando el **intercambio de recursos de origen múltiple** (CORS del inglés Cross-Origin Resource Sharing) en la configuración del servidor.

> Para más información sobre este tema revisa este [artículo de la Red de Desarrolladores de Mozilla](https://developer.mozilla.org/es/docs/Web/HTTP/CORS).

## JSON, un formato de datos para la web

La letra `"X"` en AJAX viene de XML, un lenguaje de etiquetado genérico que solía ser la norma para los intercambios de información multiplataforma. Aunque todavía está en usó, XML es bastante extenso y tiende a ser reemplazado por JSON como el formato de datos estándar en la web.

JSON (del inglés JavaScript Object Notation), o **escritura de objetos JavaScript**, es una sintaxis textual para describir información estructurada. Como verás en el siguiente ejemplo, JSON se inspira en gran medida en la sintaxis de objetos JavaScript. 

```json
{
  "carros": [
    {
      "modelo": "Peugeot",
      "color": "azul",
      "registro": 2012,
      "verificaciones": [2015, 2017]
    },
    {
      "modelo": "Citroën",
      "color": "blanco",
      "registro": 1999,
      "verificaciones": [2003, 2005, 2007, 2009, 2011, 2013]
    }
  ]
}
```

Un documento JSON es un conjunto de pares nombre/valor. Los nombres siempre van entre comillas dobles `""`. Los valores pueden ser números, cadenas de caracteres, booleanos, matrices u objetos.

Muchos lenguajes de programación tiene soporte nativo para  el formato JSON… ¡Incluyendo a JavaScript, claro!