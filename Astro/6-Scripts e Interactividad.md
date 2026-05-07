### 🧠 1. Cómo funciona la interactividad en Astro

Astro, por diseño, **no envía JavaScript al navegador** a menos que vos lo pidas explícitamente.

Eso lo hace súper rápido ⚡, pero si querés tener interacción (clicks, animaciones, fetch dinámico, etc.), tenés que decirle a Astro **cuándo y cómo montar tu componente en el cliente**.

Eso se logra con los **client directives** 👇

---

### ⚙️ 2. Client Directives

Son atributos que se agregan al componente cuando lo usás.

```astro
<MiComponente client:load />
```

Hay varias formas de cargarlos según el momento:

|Directiva|Cuándo se carga el componente|
|---|---|
|`client:load`|Apenas carga la página|
|`client:idle`|Cuando el navegador está inactivo|
|`client:visible`|Cuando el elemento aparece en el viewport|
|`client:only="react"`|Solo si la página usa React (o Vue/Svelte)|
|`client:media="(min-width: 600px)"`|Según condición CSS media query|

---

### 💡 Ejemplo rápido

```astro
---
import Contador from "../components/Contador.jsx";
---

<Contador client:load />
```

📁 `Contador.jsx`

```jsx
import { useState } from "react";

export default function Contador() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(count + 1)}>
      Contador: {count}
    </button>
  );
}
```

✅ El componente React se renderiza del lado del cliente y reacciona al click.

---

### 🔌 3. Conectar JavaScript en el frontend (sin React)

No necesitás React para agregar scripts simples.  
Podés insertar **scripts dentro de tu componente Astro** usando el tag `<script>`.

📄 Ejemplo:

```astro
<div id="box" class="p-4 bg-blue-500 text-white">
  Click para cambiar color
</div>

<script>
  const box = document.getElementById("box");
  box.addEventListener("click", () => {
    box.classList.toggle("bg-red-500");
  });
</script>
```

> 🔥 Este script **solo se ejecuta en el cliente**, porque está dentro del HTML del navegador.

---

### 🪄 4. Añadir animaciones con **Framer Motion**

Si usás React en tu proyecto, podés instalar Framer Motion para animar componentes:

```bash
npm install framer-motion
```

Ejemplo (`CardAnimada.jsx`):

```jsx
import { motion } from "framer-motion";

export default function CardAnimada({ title }) {
  return (
    <motion.div
      className="p-6 rounded-xl shadow-lg bg-white"
      whileHover={{ scale: 1.05 }}
      transition={{ type: "spring", stiffness: 300 }}
    >
      <h3>{title}</h3>
      <p>Esta card se anima al pasar el mouse 🚀</p>
    </motion.div>
  );
}
```

Y la usás en Astro:

```astro
---
import CardAnimada from "../components/CardAnimada.jsx";
---

<CardAnimada title="Soy una Card Animada" client:visible />
```

✅ Con `client:visible`, se carga **solo cuando el usuario la ve**, optimizando el rendimiento.

---

### 🧱 5. Ejemplo práctico: “Card Interactiva” con datos dinámicos

Vamos a combinar todo lo aprendido 💪

📁 `components/CardInteractiva.jsx`

```jsx
import { useState, useEffect } from "react";

export default function CardInteractiva() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users/1")
      .then((res) => res.json())
      .then(setData);
  }, []);

  if (!data) return <p>Cargando...</p>;

  return (
    <div className="p-4 border rounded-lg shadow hover:shadow-xl transition-all">
      <h2 className="font-bold text-xl">{data.name}</h2>
      <p>{data.email}</p>
      <p className="text-sm text-gray-600">{data.company.name}</p>
    </div>
  );
}
```

📄 En tu página Astro:

```astro
---
import CardInteractiva from "../components/CardInteractiva.jsx";
---

<CardInteractiva client:load />
```

✅ Este componente:

- Hace fetch a una API.
- Renderiza el resultado.
- Se carga solo en el cliente.

---

### 🧩 6. Cuándo usar cada directiva (resumen)

|Caso de uso|Directiva recomendada|
|---|---|
|Componente que necesita JS desde el inicio|`client:load`|
|Animaciones o efectos ligeros|`client:visible`|
|Componente que no es urgente (optimización)|`client:idle`|
|Componente que usa framework (React/Vue/Svelte) y no Astro|`client:only="react"`|

---