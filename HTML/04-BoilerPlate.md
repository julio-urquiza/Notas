# ¿Qué es un código HTML estándar y por qué es importante?

Aprendamos acerca del código HTML.

¿Te preguntas qué es el HTML repetitivo? Es como una plantilla predefinida para tus páginas web. Piensa en él como los cimientos de una casa. Un HTML repetitivo incluye la estructura básica y los elementos esenciales que todo documento HTML necesita. Te ahorra tiempo y te ayuda a garantizar que tus páginas estén configuradas correctamente. Aquí tienes un ejemplo:

Código de ejemplo

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta
       name="viewport"
       content="width=device-width, initial-scale=1.0" />
    <title>freeCodeCamp</title>
    <link rel="stylesheet" href="./styles.css" />
  </head>
  <body>
  </body>
</html>
```

Analicemos las partes clave de este texto estándar. Primero, está la `DOCTYPE`declaración:

Código de ejemplo

```html
<!DOCTYPE html>
```

Indica a los navegadores qué versión de HTML se está usando. A continuación, viene la `html`etiqueta:

Código de ejemplo

```html
<!DOCTYPE html>
<html lang="en">
  <!--All other elements go inside here-->
</html>
```

Esto envuelve todo tu contenido y permite especificar el idioma de tu página. Dentro de la `html`etiqueta, encontrarás dos secciones principales: a `head`y a `body`:

Código de ejemplo

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <!--Important metadata goes here-->
  </head>
  <body>
    <!--Headings, paragraphs, images, etc. go inside here-->
  </body>
</html>
```

La `head`sección contiene información importante detrás de escena:

Código de ejemplo

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Document Title Goes Here</title>
  <link rel="stylesheet" href="./styles.css" />
</head>
```

Los metadatos de tu sitio, incluidos en `meta`los elementos, contienen detalles sobre aspectos como la codificación de caracteres y cómo sitios web como Twitter deberían previsualizar el enlace de tu página. El título de tu sitio, que se encuentra en el `title`elemento, determina el texto que aparece en la pestaña o ventana del navegador. Por último, normalmente enlazarás las hojas de estilo externas de tu página en la `head`sección mediante `link`elementos.

La `body`sección es donde va todo tu contenido:

Código de ejemplo

```html
<body>
  <h1>I am a main title</h1>
  <p>Example paragraph text</p>
</body>
```

Ahora bien, ¿por qué es importante un código repetitivo? Garantiza que tus páginas estén correctamente estructuradas y funcionen correctamente en diferentes navegadores. Usar un código repetitivo te ayuda a evitar errores comunes y a seguir las mejores prácticas. Es un excelente punto de partida para cualquier proyecto web. Recuerda que puedes personalizar tu propio código repetitivo para adaptarlo a tus necesidades. A medida que ganes experiencia, puedes añadir tus propios elementos o `meta`etiquetas preferidos. A medida que vayas mejorando tu código repetitivo, descubrirás que te ahorra tiempo al iniciar nuevos proyectos.

La próxima vez que crees un nuevo archivo HTML, considera usar un código repetitivo. Sin duda, te brindará una base sólida sobre la que construir.