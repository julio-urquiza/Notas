### 1️⃣ Configuración del build (`astro.config.mjs`)

Astro genera un **sitio estático** por defecto, que se guarda en la carpeta `/dist` cuando corrés:

```bash
npm run build
```

Esto crea todos los archivos HTML, CSS y JS listos para subir a cualquier servidor.

Si abrís el archivo `astro.config.mjs`, vas a ver algo así:

```js
import { defineConfig } from 'astro/config';

export default defineConfig({
  site: 'https://tusitio.com', // importante para SEO y RSS
  output: 'static', // o 'server' si usás SSR
});
```

🧠 **Tips:**

- `site`: define la URL base de tu sitio.
- `output`: si usás adaptadores como `@astrojs/vercel` o `@astrojs/netlify`, cambia a `server`.

---

### 2️⃣ Despliegue en Netlify, Vercel o GitHub Pages

#### 🔹 **Opción 1: Vercel**

1. Subí tu proyecto a GitHub.
2. Entrá en [https://vercel.com](https://vercel.com/) y conectá tu cuenta.
3. Importá tu repo → Vercel detecta Astro automáticamente.
4. ¡Listo! Se publica en una URL del tipo `https://tuapp.vercel.app`.

📦 Instalá el adaptador si querés configurarlo explícitamente:

```bash
npm install @astrojs/vercel
```

Y en `astro.config.mjs`:

```js
import vercel from "@astrojs/vercel/serverless";
export default defineConfig({
  adapter: vercel(),
});
```

---

#### 🔹 **Opción 2: Netlify**

1. Subí tu repo a GitHub.
2. En [https://app.netlify.com](https://app.netlify.com/), conectá tu repo.
3. En “Build command”: `npm run build`
4. En “Publish directory”: `dist`

📦 Instalá el adaptador:

```bash
npm install @astrojs/netlify
```

Y configurá:

```js
import netlify from "@astrojs/netlify/functions";
export default defineConfig({
  adapter: netlify(),
});
```

---

#### 🔹 **Opción 3: GitHub Pages**

1. Instalá el adaptador:

```bash
npm install @astrojs/github-pages
```

2. Configurá:

```js
import github from "@astrojs/github-pages";
export default defineConfig({
  adapter: github(),
  site: "https://tusuario.github.io/tu-repo",
});
```

3. Subí a GitHub y corré:

```bash
npm run deploy
```

---

### 3️⃣ Optimización de imágenes y assets

Astro tiene el **Image Service** integrado.

```astro
---
import { Image } from "astro:assets";
import img from "../assets/foto.jpg";
---

<Image src={img} alt="Mi imagen optimizada" width={600} height={400} />
```

✅ Beneficios:

- Redimensiona automáticamente.
- Optimiza formato (WebP, AVIF, etc).
- Lazy loading por defecto.

También podés usar el plugin:

```bash
npm install @astrojs/image
```

---

### 4️⃣ Buenas prácticas de SEO y rendimiento

#### 🧭 Etiquetas meta

En tu layout base (`src/layouts/BaseLayout.astro`):

```astro
<head>
  <meta charset="UTF-8" />
  <meta name="description" content="Mi sitio con Astro" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>{Astro.props.title || "Mi sitio Astro"}</title>
</head>
```

#### ⚡ Optimización de rendimiento

- Usa componentes **islands** solo cuando sea necesario.
- Importá imágenes y assets locales, no enlaces externos innecesarios.
- Hacé análisis con `npm run preview` para detectar tiempos de carga.

---

### 🧩 Ejercicio Práctico

👉 **Tarea:**

1. Configurá el `astro.config.mjs` con tu URL.
2. Instalá un adaptador (Netlify o Vercel).
3. Desplegá tu sitio de prueba online.
4. Enviá la URL final publicada 🚀


---