### 📁 1. Sistema de rutas automáticas

En Astro, **cada archivo dentro de `src/pages` se convierte automáticamente en una página**.  
No necesitás configurar routers ni imports complicados.

#### 🧩 Ejemplo:

```
src/pages/
├── index.astro        → /
├── about.astro        → /about
└── contact.astro      → /contact
```

Cada archivo `.astro` exporta HTML directamente al navegador.

#### ✨ Código de ejemplo (`about.astro`)

```astro
---
---
<html lang="es">
  <head>
    <title>Sobre mí</title>
  </head>
  <body>
    <h1>Acerca de mí</h1>
    <p>Esta es la página “Sobre mí” creada con Astro.</p>
  </body>
</html>
```

💡 **Consejo:** los nombres de archivo definen las rutas:

- `index.astro` → raíz `/`
- `about.astro` → `/about`
- `blog/post.astro` → `/blog/post`

---

### 🧱 2. Layouts globales (`BaseLayout.astro`)

Un **layout** es un archivo que define la estructura base que comparten varias páginas.  
Ejemplo: encabezado, footer y metadatos comunes.

#### 📂 Estructura recomendada:

```
src/
├── layouts/
│   └── BaseLayout.astro
└── pages/
    ├── index.astro
    ├── about.astro
    └── contact.astro
```

#### ✨ `src/layouts/BaseLayout.astro`

```astro
---
const { title = "Mi sitio con Astro", description = "Sitio rápido y moderno con Astro" } = Astro.props;
---

<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{title}</title>
    <meta name="description" content={description} />
    <link rel="icon" href="/favicon.svg" />
  </head>
  <body>
    <header>
      <nav>
        <a href="/">Inicio</a>
        <a href="/about">Sobre mí</a>
        <a href="/contact">Contacto</a>
      </nav>
    </header>

    <main>
      <slot /> <!-- Aquí se inyecta el contenido de cada página -->
    </main>

    <footer>
      <p>© {new Date().getFullYear()} - Mi sitio con Astro</p>
    </footer>
  </body>
</html>

<style>
  body {
    margin: 0;
    font-family: system-ui, sans-serif;
    background: #1a1a1a;
    color: white;
  }

  nav {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    background: #111;
    padding: 1rem;
  }

  a {
    color: #00d8ff;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }

  footer {
    text-align: center;
    padding: 1rem;
    background: #111;
    margin-top: 2rem;
  }

  main {
    padding: 2rem;
  }
</style>
```

---

### 🧩 3. Uso de Slots

El `<slot />` dentro del layout es **el espacio donde se “inyecta” el contenido de cada página**.  
Esto permite mantener una sola estructura y que las páginas cambien solo su contenido.

#### ✨ Ejemplo: `index.astro`

```astro
---
import BaseLayout from "../layouts/BaseLayout.astro";
---

<BaseLayout title="Inicio - Mi sitio" description="Página principal del sitio con Astro">
  <h1>Bienvenido a mi sitio 🚀</h1>
  <p>Esta es la página de inicio.</p>
</BaseLayout>
```

#### ✨ Ejemplo: `about.astro`

```astro
---
import BaseLayout from "../layouts/BaseLayout.astro";
---

<BaseLayout title="Sobre mí" description="Conocé más sobre mí">
  <h1>Sobre mí</h1>
  <p>Soy un desarrollador apasionado por la web moderna.</p>
</BaseLayout>
```

---

### 🌐 4. Variables de entorno (para datos comunes)

Podés crear un archivo `.env` con tus datos globales:

#### `.env`

```
SITE_NAME=Mi sitio en Astro
AUTHOR=Julio Urquiza
```

Y accederlos en cualquier archivo `.astro`:

```astro
---
import { SITE_NAME, AUTHOR } from 'astro:env';
---
<p>{SITE_NAME} creado por {AUTHOR}</p>
```

---

### 🔍 5. Metadata y SEO básico

- **`<title>`** y **`<meta name="description">`** deben ser dinámicos por página.
    
- Podés agregar:
    
    ```html
    <meta property="og:title" content="Título para redes" />
    <meta property="og:description" content="Descripción para compartir" />
    <meta property="og:image" content="/preview.png" />
    <meta name="twitter:card" content="summary_large_image" />
    ```
    
- También podés tener un archivo `src/components/Head.astro` reutilizable solo para meta tags.
    

---

### ✍️ 6. Integrar fuentes y favicon

Colocá tu favicon en `/public/favicon.svg` o `/public/favicon.ico`.

Para fuentes, podés usar Google Fonts:

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
```

O importarlas directamente en el layout global.

---
