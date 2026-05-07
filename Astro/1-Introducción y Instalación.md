### 📘 1. Qué es Astro

**Astro** es un _framework de frontend orientado a contenido estático y rápido_.  
Su lema es **“Less JavaScript, faster websites”**, porque:

- Renderiza la mayor parte del contenido **en el servidor o durante el build**.
- Envía al navegador **solo el JavaScript necesario** para cada componente.
- Permite usar **cualquier framework** (React, Vue, Svelte, Solid, etc.) dentro del mismo proyecto.

👉 Ideal para:

- Blogs, portfolios, landing pages, documentación.
- Sitios que priorizan **velocidad, SEO y rendimiento**.

---

### ⚖️ 2. Comparación rápida

|Framework|Tipo|JS en el cliente|Ideal para|
|---|---|---|---|
|**Astro**|Generador de sitios estáticos híbrido|Solo donde lo pedís|Sitios rápidos, contenido|
|**Next.js**|SSR/SPA|Mucho JS|Apps complejas, dashboards|
|**React**|SPA|Todo JS|Interactividad pura|
|**Vue**|SPA/SSR|Todo JS|Apps interactivas|
|**SvelteKit**|SSR|Menos JS|Apps pequeñas/medianas|

---

### ⚙️ 3. Instalación paso a paso

#### ✅ Requisitos

- Node 18 o superior
- npm o pnpm

#### 📦 Comando de instalación

```bash
# Con npm
npm create astro@latest

# O con pnpm
pnpm create astro@latest
```

Te pedirá:

- Nombre del proyecto → `mi-landing-astro`
- Plantilla → elige **“Minimal”**
- TypeScript → opcional (recomendado)
- Instalar dependencias → **Yes**

Después:

```bash
cd mi-landing-astro
npm run dev
```

Y abrí [http://localhost:4321](http://localhost:4321/) 🚀

---

### 🧱 4. Estructura del proyecto

```
mi-landing-astro/
├── public/                # Archivos estáticos (imágenes, íconos)
├── src/
│   ├── components/        # Componentes .astro, .jsx, .vue, etc.
│   ├── layouts/           # Layouts reutilizables
│   ├── pages/             # Cada archivo = una ruta (ej: index.astro → "/")
│   └── styles/            # CSS global o módulos
├── package.json
├── astro.config.mjs
└── tsconfig.json          # Si usás TypeScript
```

---

### 🌐 5. Primer sitio: “Mi primer landing con Astro”

#### 1️⃣ En `src/pages/index.astro`:

```astro
---
import "../styles/global.css"
---

<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <title>Mi primer landing con Astro 🚀</title>
  </head>
  <body>
    <header>
      <h1>Bienvenido a mi sitio hecho con Astro</h1>
      <p>Ultra rápido, moderno y sin complicaciones.</p>
    </header>

    <main>
      <section>
        <h2>¿Qué es Astro?</h2>
        <p>Un framework que te deja usar HTML, CSS y JS como te gusta, pero optimizado al máximo.</p>
      </section>

      <section>
        <h2>Beneficios</h2>
        <ul>
          <li>⚡ Super veloz</li>
          <li>💡 Simple de usar</li>
          <li>🔧 Compatible con cualquier framework</li>
        </ul>
      </section>
    </main>

    <footer>
      <p>Hecho con ❤️ y Astro</p>
    </footer>
  </body>
</html>
```

#### 2️⃣ Crea `src/styles/global.css`:

```css
body {
  font-family: system-ui, sans-serif;
  margin: 0;
  background: linear-gradient(180deg, #1a1a1a, #2a2a2a);
  color: white;
  padding: 2rem;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

section {
  margin-top: 2rem;
}
```

#### 3️⃣ Ejecutá:

```bash
npm run dev
```

Y abrí el navegador para ver tu **landing básica en Astro** 🪐

---