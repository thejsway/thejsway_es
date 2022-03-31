# ¿Qué es una página web?

Este capítulo breve resumen lo que necesitas saber acerca de la web y las páginas web.

## TL;DR

* La [World Wide Web](https://es.wikipedia.org/wiki/World_Wide_Web) (o **Web**) es un espacio de información construido sobre  [Internet](https://es.wikipedia.org/wiki/Internet). Los recursos web son accesibles a través de su [URL](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme), y pueden contener [hiperenlaces](https://en.wikipedia.org/wiki/Hyperlink) a otros recursos.

* Una página web es un documento apropiado para la web. Crear páginas web generalmente involucra tres tecnologías: [HTML](https://es.wikipedia.org/wiki/HTML)para estructurar el contenido,  [CSS](https://es.wikipedia.org/wiki/CSS) para definir su presentación y JavaScript para añadir interactividad. 

* Un documento HTML está hecho de texto y elementos estructurales llamados **etiquetas** que describen el contenido de la página, tales como: párrafos, encabezados, hiperenlaces, imágenes, etc.

* CSS usa selectores para declarar a qué elementos HTML se les aplica un estilo. Los elementos pueden ser seleccionados por el nombre de la etiqueta (`h1`), clase (`.terminado`) o un identificador (`#grosero`).

* Un documento HTML puede incluir una hoja de estilos CSS con la etiqueta `<link>` y un archivo JavaScript con la etiqueta `<script>`.

```html
<!doctype html>
<html>

<head>
    <!-- Información de la página: título, conjunto de caracteres, etc -->

    <!-- Enlace a una hoja de estilo CSS -->
    <link href="ruta/al/archivo.css" rel="stylesheet" type="text/css">
</head>

<body>
    <!-- Contenido de la página -->

    <!-- Enlace a un archivo JavaScript -->
    <script src="ruta/al/archivo.js"></script>
</body>

</html>
```

* Un **navegador** es un programa que usas para visitar páginas web y usar aplicaciones web. Los modernos incluyen un conjunto de **herramientas para desarrolladores** para facilitar el trabajo de desarrollar para la web.

## Internet y la Web

Como problablemente sabes, la [World Wide Web](https://es.wikipedia.org/wiki/World_Wide_Web) (o **Web** para abreviar) es un espacio de información en continúa expansión construido sobre  [Internet](https://es.wikipedia.org/wiki/Internet). Los recursos web son accesibles a través de su dirección, denominada  [URL](https://es.wikipedia.org/wiki/Localizador_de_recursos_uniforme), y pueden contener [hiperenlaces](https://en.wikipedia.org/wiki/Hyperlink) a otros recursos. Juntos, todos estos recursos interconectados forman un enorme entramado semejante a una telaraña.

Los documentos apropiados para la web son llamados **páginas web**. Son agrupados en **sitios web** y visitados a través de un tipo especial de programa llamado [navegador](https://es.wikipedia.org/wiki/Navegador_web).

## Los lenguajes de la Web

Hay tres tecnologías principales para crear páginas web: HTML, CSS y JavaScript.

### HTML

HTML, siglas en inglés de [HyperText Markup Language](https://es.wikipedia.org/wiki/HTML), 
es el formato de las páginas web. Un documento HTML está hecho de texto y elementos estructurales llamados **etiquetas**. Las etiquetas se usan para describir el contenido de la página, tales como: párrafos, encabezados, hiperenlaces, imágenes, etc.

Aquí hay un ejemplo de una página web sencilla, geralmente almacenada como un archivo `.html`.


```html
<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <title>Mi página web</title>
</head>

<body>
    <h1>Mi página web</h1>
    <p>¡Hola! mi nombre es Baptiste.</p>
    <p>Vivo en la gran ciudad de <a href="https://es.wikipedia.org/wiki/Burdeos">Bordeos</a>.</p>
</body>

</html>
```

![Resultado de visualización](images/chapter13-01.png)

Aquí hay algunas referencias para aprender más sobre HTML:

* [Interneting is Hard - A friendly web development tutorial for complete beginners](https://internetingishard.com/html-and-css/)
* [Khan Academy - Introducción a HTML](https://es.khanacademy.org/computing/computer-programming/html-css#intro-to-html)
* [Red de desarrolladores de Mozilla - Referencia HTML](https://developer.mozilla.org/es/docs/Web/HTML/Reference)

### CSS

CSS, o [hoja de estilo en cascada](https://es.wikipedia.org/wiki/CSS), es un lenguaje usado para modificar la presentación de páginas web

CSS usa selectores para declarar a qué elementos se aplica un estilo. Muchas estrategias de selección son posibles, especialmente:

* Todos los elemento de determinado nombre de etiqueta.
* Elementos correspondientes a determinada **clase** (sintaxis del selector: `.miClase`).
* El elemento correspondiente a un determinado **identificador** único (sintaxis del selector: `#MiId`).

Este es un ejemplo sencillo de una hoja de estilo CSS, generalmente almacenada como un archivo `.css`.

```css
/* Todos los elementos h1 están en rosa */
h1 {
   color: pink;
}

/* Todos los elementos con la clase "terminado" están tachados */
.terminado {
  text-decoration: line-through;
}

/* El elemento que tiene el id "grosero" es mostrado en mayúsculas con un tipo de fuente especial */
#grosero {
  font-family: monospace;
  text-transform: uppercase;
}
```

Una hoja de estilo es asociada con un documento HTML usando una etiqueta `link` en la sección `head` de la página.

```html
<!-- Enlace a una hoja de estilo CSS -->
<link href="ruta/al/archivo.css" rel="stylesheet" type="text/css">
```
Para aprender más sobre CSS, visita los siguientes enlaces:

* [Khan Academy - Introducción a CSS](https://es.khanacademy.org/computing/computer-programming/html-css#intro-to-css)
* [Red de desarrolladores de Mozilla - Referencia CSS](https://developer.mozilla.org/es/docs/Web/CSS/Reference)

### JavaScript

JavaScript puede interactuar con un documento HTML para proporcionar interactividad dinámica: respuestas a las acciones del usuario en la página, estilizado dinámico, animaciones, etc. Es el único lenguaje de programación entendido por todos los navegadores de internet.

Un archivo JavaScript, generalmente almacenado en un archivo `.js`, es cargado por una página web con la etiqueta `<script>`. 

```html
<!-- Carga un archivo JavaScript -->
<script src="ruta/al/archivo.js"></script>
```

## Desarrollo de páginas web

Para crear páginas web interactivas, necesitas escribir código HTML, CSS y JavaScript. Si apenas estás comenzando, la forma más fácil de hacerlo es usando un entorno virtual de JavaScript. Sin embargo, en algún punto probablemente quieras desarrollar de una manera más profesional, o necesites trabajar fuera de línea.

Consulta el apéndice para más detalles sobre cómo configurar tu entorno.

## ¡Hora de programar!

Puedes saltarte este ejercicio si tienes experiencia previa con HTML y CSS.

### Tu primera página web

Sigue los pasos al inicio del tutorial [Primeros pasos en la Web](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web) de la Red de desarrolladores de Mozilla para crear una página web sencilla usando HTML y CSS. Los pasos necesarios son:

1. [¿Cuál será la apariencia de tu sitio web?](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/What_will_your_website_look_like)
1. [Manejo de archivos](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/Dealing_with_files)
1. [Conceptos básicos de HTML](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/HTML_basics)
1. [Conceptos básicos de CSS](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/CSS_basics)

![Resultado esperado](images/chapter12-02.png)