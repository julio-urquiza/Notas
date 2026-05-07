### 🧩 1. Qué es un componente `.astro`

Un **componente en Astro** es simplemente un archivo con extensión `.astro` que puede:

- Contener **HTML**, **JS** y **CSS**.
- Recibir **props** (propiedades) como en React.
- Renderizar **otros componentes**.

📄 Ejemplo básico (`Card.astro`):

```astro
---
const { title, description } = Astro.props;
---

<div class="card">
  <h2>{title}</h2>
  <p>{description}</p>
</div>

<style>
  .card {
    padding: 1rem;
    border: 1px solid #ccc;
    border-radius: 8px;
  }
</style>
```

Podés usarlo así en otra página o componente:

```astro
---
import Card from '../components/Card.astro';
---

<Card title="Hola Mundo" description="Mi primera card en Astro 🚀" />
```

---

### ⚙️ 2. Pasar Props entre componentes

Las props funcionan igual que en React o Svelte:

- Se **declaran** en la parte superior (`Astro.props`).
- Se **envían** como atributos cuando usás el componente.

📘 Ejemplo:

```astro
---
// Card.astro
const { nombre, edad } = Astro.props;
---

<div>
  <h3>{nombre}</h3>
  <p>Tiene {edad} años.</p>
</div>
```

```astro
---
// index.astro
import Card from '../components/Card.astro';
---

<Card nombre="Julio" edad={28} />
```

🧠 Tip: las props se pueden **validar o dar valor por defecto**:

```astro
const { nombre = "Desconocido", edad = 0 } = Astro.props;
```

---

### 🔁 3. Render condicional y loops

Astro permite usar **JavaScript directamente** dentro del HTML.  
Podés usar `if`, `map`, etc. dentro del bloque HTML:

```astro
---
const { usuarios } = Astro.props;
---

<ul>
  {usuarios.length > 0 ? (
    usuarios.map((u) => <li>{u}</li>)
  ) : (
    <li>No hay usuarios</li>
  )}
</ul>
```

📄 Ejemplo de uso:

```astro
<UsuariosList usuarios={["Ana", "Pedro", "Lucía"]} />
```

---

### ⚛️ 4. Interacción con React, Vue o Svelte

Astro te permite **incrustar componentes de otros frameworks**.  
Solo tenés que instalarlos:

```bash
npm install @astrojs/react
```

Y agregarlo en tu `astro.config.mjs`:

```js
import react from "@astrojs/react";

export default {
  integrations: [react()],
};
```

Luego, podés usar un componente React dentro de Astro:

```astro
---
import Contador from '../components/Contador.jsx';
---

<h1>Componente React dentro de Astro:</h1>
<Contador client:load />
```

🧩 El `client:load` indica que ese componente se monta en el cliente (navegador).  
También existen `client:visible`, `client:idle`, `client:only="react"`, etc.

---

### 🎨 5. Slots y composición de componentes

Los **slots** te permiten pasar contenido **dentro** de un componente.  
Sirven para hacer layouts reutilizables.

📦 Ejemplo (`Layout.astro`):

```astro
<div class="layout">
  <header>Mi sitio</header>
  <main>
    <slot />  <!-- Aquí se inyecta el contenido -->
  </main>
  <footer>© 2025</footer>
</div>
```

📄 Uso:

```astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout>
  <h1>Bienvenido a mi sitio</h1>
  <p>Contenido principal...</p>
</Layout>
```

🧩 También podés tener **named slots**:

```astro
<header><slot name="header" /></header>
<main><slot /></main>
<footer><slot name="footer" /></footer>
```

---
## 🧩 Qué son los “named slots”

En Astro, un `<slot />` es un **espacio reservado** dentro de un componente donde se puede inyectar contenido **desde el componente padre**.

Si no le ponés nombre, es el “**slot principal**” (`<slot />`).

Pero si le ponés un atributo `name`, como:

```astro
<slot name="header" />
```

…entonces ese slot solo mostrará contenido que venga con ese nombre.

---

## 💡 Ejemplo completo

Supongamos que tenemos un layout llamado `Layout.astro`:

```astro
<!-- Layout.astro -->
<div class="layout">
  <header>
    <slot name="header" />  <!-- Aquí se mostrará el header -->
  </header>

  <main>
    <slot /> <!-- Este es el contenido principal -->
  </main>

  <footer>
    <slot name="footer" />  <!-- Aquí se mostrará el footer -->
  </footer>
</div>

<style>
  .layout {
    border: 2px solid #ccc;
    border-radius: 8px;
    padding: 1rem;
  }
  header, footer {
    background: #f4f4f4;
    padding: 0.5rem;
  }
</style>
```

---

### 🧱 Ahora usás ese layout en otra página o componente:

```astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout>
  <!-- Slot principal -->
  <h1>Bienvenido a mi sitio</h1>
  <p>Este es el contenido principal del body.</p>

  <!-- Slot con nombre "header" -->
  <div slot="header">
    <h2>Encabezado personalizado 🌟</h2>
  </div>

  <!-- Slot con nombre "footer" -->
  <div slot="footer">
    <p>Hecho con ❤️ por Julio</p>
  </div>
</Layout>
```

---

## 🧠 Cómo funciona

- Todo lo que pongas **sin `slot="..."`** irá al **slot principal** (`<slot />`).
    
- Lo que tenga `slot="header"` va a `<slot name="header" />`.
    
- Lo que tenga `slot="footer"` va a `<slot name="footer" />`.
    

Si no enviás nada para un slot con nombre, **queda vacío**.

---

## ✅ Resultado visual

```
┌─────────────────────────────┐
│  Encabezado personalizado   │
├─────────────────────────────┤
│ Bienvenido a mi sitio       │
│ Este es el contenido...     │
├─────────────────────────────┤
│ Hecho con ❤️ por Julio       │
└─────────────────────────────┘
```

---
