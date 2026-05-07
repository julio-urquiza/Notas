### 🎨 1. Formas de usar CSS en Astro

Astro te permite aplicar estilos de tres maneras principales:

|Tipo|Dónde se define|Alcance|
|---|---|---|
|**Inline CSS**|Dentro de la etiqueta `<style>` en el mismo archivo `.astro`|Solo afecta a ese componente (scoped)|
|**Global CSS**|En un archivo `.css` importado en el layout o en `src/styles`|Afecta a todo el sitio|
|**CSS Externo**|Cargado desde `/public/` o CDN|Afecta globalmente (como en HTML clásico)|

---

#### 🧩 Ejemplo 1: **Scoped CSS**

```astro
---
---
<div class="card">
  <h2>Mi card</h2>
  <p>Contenido estilizado solo aquí.</p>
</div>

<style>
  .card {
    background: #222;
    padding: 1rem;
    border-radius: 1rem;
    color: white;
    transition: transform 0.2s;
  }
  .card:hover {
    transform: scale(1.05);
  }
</style>
```

➡️ Este estilo **solo afecta este componente `.astro`**, aunque exista otra clase `.card` en otro archivo.

---

#### 🧩 Ejemplo 2: **Global CSS**

En `src/styles/global.css`:

```css
body {
  margin: 0;
  background: #1a1a1a;
  color: #f1f1f1;
  font-family: system-ui, sans-serif;
}
a {
  color: #00d8ff;
  text-decoration: none;
}
```

Y lo importás una vez en tu layout:

```astro
---
import "../styles/global.css";
---
```

---

### ⚡ 2. Integrar Tailwind CSS en Astro

### Add Tailwind 4

In Astro `>=5.2.0`, use the `astro add tailwind` command for your package manager to install the official Vite Tailwind plugin. To add Tailwind 4 support to earlier versions of Astro, follow the [instructions in the Tailwind docs](https://tailwindcss.com/docs/installation/framework-guides/astro) to add the `@tailwindcss/vite` Vite plugin manually.

- [npm](https://docs.astro.build/en/guides/styling/#tab-panel-2001)
- [pnpm](https://docs.astro.build/en/guides/styling/#tab-panel-2002)
- [Yarn](https://docs.astro.build/en/guides/styling/#tab-panel-2003)

Terminal window

``` terminal
pnpm astro add tailwind
```

Then, import `tailwindcss` into `src/styles/global.css` (or another CSS file of your choosing) to make Tailwind classes available to your Astro project. This file including the import will be created by default if you used the `astro add tailwind` command to install the Vite plugin.

src/styles/global.css

``` css
@import "tailwindcss";
```

Import this file in the pages where you want Tailwind to apply. This is often done in a layout component so that Tailwind styles can be used on all pages sharing that layout:

src/layouts/Layout.astro

``` astro
---import "../styles/global.css";---
```

---

#### 🧠 Configuración básica

El archivo `tailwind.config.mjs` ya debería contener:

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./src/**/*.{astro,html,js,jsx,ts,tsx,vue,svelte}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

Y en `src/styles/global.css`:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

#### 🚀 Uso en tu Layout o Componentes

Ejemplo (`BaseLayout.astro`):

```astro
---
import "../styles/global.css";
---

<html lang="es">
  <body class="bg-gray-900 text-white font-sans">
    <header class="bg-gray-800 p-4 flex justify-center gap-6">
      <a href="/" class="hover:text-cyan-400">Inicio</a>
      <a href="/about" class="hover:text-cyan-400">Sobre mí</a>
      <a href="/contact" class="hover:text-cyan-400">Contacto</a>
    </header>

    <main class="p-6">
      <slot />
    </main>

    <footer class="text-center p-4 bg-gray-800 mt-10">
      © {new Date().getFullYear()} - Mi sitio Astro
    </footer>
  </body>
</html>
```

💡 **Consejo:** con Tailwind no necesitás escribir `<style>` — todo se hace con clases utilitarias.

---

### 🧱 3. Estilos “Scoped” con Tailwind y CSS híbrido

Podés mezclar estilos locales y Tailwind sin problema:

```astro
<div class="card bg-gray-800 p-4 rounded-lg text-center">
  <h2 class="text-xl font-semibold text-cyan-400">Título</h2>
  <p>Texto dentro de una card estilizada</p>
</div>

<style>
  .card:hover {
    transform: scale(1.05);
    transition: transform 0.2s;
  }
</style>
```

Astro compila ambos estilos sin conflictos.

---

### 📱 4. Diseño responsivo con Tailwind

Tailwind usa **prefixes por breakpoint** para diseño responsive:

|Breakpoint|Prefijo|Tamaño|
|---|---|---|
|`sm:`|Small|≥640px|
|`md:`|Medium|≥768px|
|`lg:`|Large|≥1024px|
|`xl:`|Extra Large|≥1280px|

Ejemplo:

```html
<div class="p-4 bg-gray-800 md:p-8 lg:flex lg:justify-between">
  <div class="mb-4 lg:mb-0">
    <h2 class="text-xl">Responsive design</h2>
  </div>
  <button class="bg-cyan-500 px-4 py-2 rounded hover:bg-cyan-600">
    Accionar
  </button>
</div>
```

💡 En móvil se muestra en columna, en escritorio (`lg:`) se alinea en fila.

---

### 🧠 MINI-PROYECTO DEL MÓDULO 3

**Objetivo:** aplicar todo lo aprendido para crear un _hero section_ moderno con Tailwind.

#### 🪄 Estructura

`src/pages/index.astro`:

```astro
---
import BaseLayout from "../layouts/BaseLayout.astro";
---

<BaseLayout title="Inicio">
  <section class="flex flex-col items-center justify-center text-center min-h-[80vh] bg-gradient-to-b from-gray-900 to-gray-800">
    <h1 class="text-4xl md:text-6xl font-bold text-cyan-400 mb-4">
      Hola, soy Julio 👋
    </h1>
    <p class="text-gray-300 text-lg max-w-xl">
      Desarrollador web que crea experiencias rápidas y modernas con Astro ⚡
    </p>
    <a href="/contact" class="mt-6 px-6 py-3 bg-cyan-500 text-white font-semibold rounded-lg hover:bg-cyan-600 transition">
      Contáctame
    </a>
  </section>
</BaseLayout>
```

💥 Resultado: una página totalmente responsive, moderna y sin escribir CSS manual.
