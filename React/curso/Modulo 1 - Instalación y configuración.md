## 🧩 **1. ¿Qué es React y por qué usarlo?**

**React** es una **biblioteca de JavaScript** desarrollada por **Facebook (Meta)** para construir **interfaces de usuario (UI)** de forma **rápida, modular y eficiente**.

🔹 **Ventajas principales:**

- **Componentes reutilizables:** cada parte de tu interfaz (botones, formularios, etc.) es un componente independiente.
- **Virtual DOM:** React actualiza solo lo necesario en pantalla → mejora el rendimiento.
- **Unidireccionalidad de datos:** el flujo de datos es más fácil de rastrear.
- **Gran comunidad y ecosistema:** miles de librerías y recursos.

👉 En resumen: React te permite crear aplicaciones web **rápidas, escalables y mantenibles**.

---

## ⚙️ **2. Instalación y configuración del entorno**

### 📦 Requisitos:

1. **Node.js** (versión 18 o superior)  
    🔗 [https://nodejs.org](https://nodejs.org/)
2. **Editor recomendado:** [VS Code](https://code.visualstudio.com/)
3. **Navegador:** Chrome o Edge (para usar las DevTools)

---

## 🚀 **3. Crear tu primer proyecto**

Hoy en día la mejor forma es con **Vite** (más liviano y rápido que Create React App).

### ▶️ Paso a paso:

1️⃣ En una terminal, ejecutá:

```bash
npm create vite@latest mi-app-react
```

2️⃣ Elegí:

```
✔ Framework: › React
✔ Variant: › JavaScript
```

3️⃣ Entrá al proyecto:

```bash
cd mi-app-react
```

4️⃣ Instalá las dependencias:

```bash
npm install
```

5️⃣ Iniciá el servidor:

```bash
npm run dev
```

🖥️ Luego abrí la URL que te muestra la terminal (por defecto: `http://localhost:5173`)

¡Listo! 🎉 ya tenés tu proyecto React funcionando.

---

## 🗂️ **4. Estructura de carpetas y archivos**

Cuando abrís el proyecto vas a ver algo como esto:

```
mi-app-react/
├── index.html
├── package.json
├── vite.config.js
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── assets/
    └── components/
```

📘 **Archivos clave:**

- `index.html` → el HTML principal (solo uno).
- `main.jsx` → punto de entrada; aquí React se monta al DOM.
- `App.jsx` → componente raíz de tu aplicación.
- `components/` → donde vas a guardar tus componentes.

---

## 🧱 **5. JSX: qué es y cómo funciona**

**JSX (JavaScript XML)** es una extensión de JavaScript que te permite **escribir HTML dentro del código JS**.

Ejemplo:

```jsx
function App() {
  return <h1>Hola React 👋</h1>;
}
```

👉 Aunque parezca HTML, en realidad JSX se transforma a **JavaScript puro**.  
Por ejemplo:

```jsx
<h1>Hola</h1>
```

se convierte internamente en:

```js
React.createElement('h1', null, 'Hola');
```

🔹 Las etiquetas deben estar **cerradas correctamente**.  
🔹 Solo se puede **retornar un elemento raíz**, por eso se usa `<div>` o `<>...</>` (fragmento).

---

## ⚛️ **6. Componentes: función, props y retorno**

Un **componente** en React es **una función que devuelve JSX**.

Ejemplo básico:

```jsx
function Saludo() {
  return <h2>¡Hola desde un componente!</h2>;
}
```

Y se usa dentro de otro componente:

```jsx
function App() {
  return (
    <div>
      <Saludo />
    </div>
  );
}

export default App;
```

📦 **Props:**  
Sirven para enviar datos a los componentes hijos:

```jsx
function Saludo({ nombre }) {
  return <h2>Hola {nombre} 👋</h2>;
}

function App() {
  return <Saludo nombre="Julio" />;
}
```

---
