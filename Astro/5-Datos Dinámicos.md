---

## 📦 MÓDULO 5 – Datos Dinámicos

---
### 🧠 1. Usar Markdown (`.md`) como fuente de contenido

Astro puede leer archivos Markdown (por ejemplo, para un blog).  
Cada archivo `.md` puede tener un _frontmatter_ con metadatos y luego el contenido.

📄 Ejemplo (`src/content/posts/primer-post.md`):

```markdown
---
title: "Mi primer post en Astro"
date: "2025-10-10"
author: "Julio"
---

Bienvenido a mi primer artículo en **Astro** 🚀.
```

Y podés mostrarlo en una página:

```astro
---
import { marked } from "marked";
import fs from "fs";

const post = fs.readFileSync("./src/content/posts/primer-post.md", "utf-8");
const html = marked.parse(post);
---

<article class="prose" set:html={html}></article>
```

> 🧩 Si tenés Tailwind, podés usar la clase `prose` (de `@tailwindcss/typography`) para aplicar estilo automáticamente al contenido Markdown.

---

### 📂 2. Importar y renderizar datos desde JSON

Podés crear un archivo JSON y usarlo directamente en Astro.

📁 `src/data/usuarios.json`

```json
[
  { "nombre": "Julio", "edad": 28 },
  { "nombre": "María", "edad": 31 }
]
```

Y en tu página:

```astro
---
import usuarios from "../data/usuarios.json";
---

<ul>
  {usuarios.map((u) => (
    <li>{u.nombre} — {u.edad} años</li>
  ))}
</ul>
```

✅ Esto es **server-side**, así que no expone los datos directamente al cliente (a menos que los renderices).

---

### 🌐 3. Fetch de APIs externas

Astro puede hacer **peticiones HTTP** desde el servidor o el cliente.

#### 🔹 Server-side (recomendado)

El fetch ocurre en el servidor **antes de renderizar la página**:

```astro
---
const res = await fetch("https://api.github.com/users/octocat");
const data = await res.json();
---

<h2>{data.name}</h2>
<img src={data.avatar_url} width="100" />
<p>{data.bio}</p>
```

✅ Ideal para datos que cambian poco (como perfiles, listados, etc.)

---

#### 🔹 Client-side

Cuando querés hacer la llamada desde el navegador (por ejemplo, para búsquedas o datos que cambian constantemente):

```astro
---
import { useEffect, useState } from "react";
---

<script client:load>
  import { useState, useEffect } from "react";

  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch("https://api.github.com/users/octocat")
      .then((res) => res.json())
      .then(setUser);
  }, []);
</script>

{user ? <div>{user.login}</div> : <p>Cargando...</p>}
```

> 💡 Para usar esto, el archivo debe tener **integración React o Vue** configurada (como vimos en el módulo 4).

---

### 📘 4. Usar `Astro.glob()` para leer contenido dinámico

`Astro.glob()` te permite **importar múltiples archivos** al mismo tiempo (Markdown, JSON, etc).

Ejemplo: cargar todos los posts `.md` de una carpeta:

```astro
---
const posts = await Astro.glob("../content/posts/*.md");
---

<ul>
  {posts.map((post) => (
    <li><a href={post.url}>{post.frontmatter.title}</a></li>
  ))}
</ul>
```

✅ Astro genera automáticamente las rutas y metadatos.

---

### 🔗 5. Integrar datos externos (Google Drive, Firebase, CMS, etc.)

Para conectarte con fuentes externas:

- **Google Drive** → usás su API con `fetch` y claves de acceso (desde el backend o un endpoint de Astro).
    
- **Firebase** → podés inicializar el SDK en un componente de servidor o cliente.
    
- **Headless CMS** (ej. Contentful, Sanity, Strapi) → hacés un fetch desde sus endpoints REST o GraphQL.
    

Ejemplo de fetch desde Google Drive:

```astro
---
const folderId = "1aB2C3D4E5F"; // ID de carpeta pública
const res = await fetch(
  `https://www.googleapis.com/drive/v3/files?q='${folderId}'+in+parents&key=TU_API_KEY`
);
const { files } = await res.json();
---

<ul>
  {files.map((file) => (
    <li>{file.name}</li>
  ))}
</ul>
```

> 🧠 Recomendación: hacé estos fetch **en el servidor**, no en el navegador, para evitar exponer tu API key.

---
