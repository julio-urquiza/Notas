La estructura general del `<body>` en **HTML** no es rígida, pero sí sigue convenciones semánticas y estructurales claras. El `<body>` contiene **todo el contenido visible del documento**.

A nivel arquitectónico, suele organizarse en tres grandes zonas:

```html
<body>
  <header>
    <!-- Encabezado: logo, navegación, título -->
  </header>

  <main>
    <!-- Contenido principal de la página -->
  </main>

  <footer>
    <!-- Pie de página: copyright, enlaces legales, contacto -->
  </footer>
</body>
```

---

## 🔹 Estructura semántica recomendada (HTML5)

Desde **HTML5**, se promueve el uso de etiquetas semánticas para estructurar el contenido correctamente:

```html
<body>

  <header>
    <h1>Título del sitio</h1>
    <nav>
      <ul>
        <li><a href="#">Inicio</a></li>
        <li><a href="#">Servicios</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section>
      <h2>Sección 1</h2>
      <p>Contenido de la sección.</p>
    </section>

    <article>
      <h2>Artículo independiente</h2>
      <p>Contenido del artículo.</p>
    </article>

    <aside>
      <p>Contenido complementario</p>
    </aside>
  </main>

  <footer>
    <p>© 2026 Mi Sitio Web</p>
  </footer>

</body>
```

---

## 🔹 Significado de cada bloque

- **`<header>`** → Encabezado de la página o de una sección.
    
- **`<nav>`** → Bloque de navegación.
    
- **`<main>`** → Contenido principal (solo debe haber uno por documento).
    
- **`<section>`** → Agrupación temática de contenido.
    
- **`<article>`** → Contenido independiente (blog post, noticia, etc.).
    
- **`<aside>`** → Contenido secundario (sidebar, publicidad).
    
- **`<footer>`** → Pie de página.
    

---

## 🔹 Alternativa básica (sin semántica)

Si no se usan etiquetas semánticas, se puede estructurar con `<div>`:

```html
<body>
  <div class="header"></div>
  <div class="main"></div>
  <div class="footer"></div>
</body>
```

Pero esto **no es recomendable** en proyectos modernos porque:

- Pierde semántica
    
- Afecta accesibilidad
    
- Empeora SEO
    

---

## 🔹 Regla conceptual importante

El `<body>`:

- Solo puede existir **uno por documento**
    
- No puede contener `<head>`, `<html>` ni `<!DOCTYPE>`
    
- Puede contener scripts (`<script>`) al final para optimizar carga
    

---
