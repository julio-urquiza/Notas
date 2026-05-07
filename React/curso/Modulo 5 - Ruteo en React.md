### 🎯 Objetivo

Aprender a configurar y usar **React Router** para crear aplicaciones con múltiples vistas, rutas dinámicas y navegación fluida sin recargar la página.

---

## ⚙️ 1. Instalación de React Router

Primero, instalamos el paquete:

```bash
npm install react-router-dom
```

---

## 🧱 2. Estructura básica de rutas

En tu archivo principal, normalmente `main.jsx` o `index.jsx`, vas a envolver tu app con el **`BrowserRouter`**:

```jsx
import { createRoot } from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";

createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

Y dentro de tu `App.jsx` definís las rutas:

```jsx
import { Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
    </Routes>
  );
}

export default App;
```

👉 Cada `<Route>` define un **path (URL)** y el **componente** que se renderiza ahí.

---

## 🧩 3. Navegación entre páginas

Para navegar sin recargar la página, se usa el componente **`Link`**:

```jsx
import { Link } from "react-router-dom";

function Navbar() {
  return (
    <nav>
      <Link to="/">Inicio</Link>
      <Link to="/about">Acerca de</Link>
    </nav>
  );
}
```

También podés navegar de forma **programática** (por ejemplo, luego de un formulario o acción) usando **`useNavigate`**:

```jsx
import { useNavigate } from "react-router-dom";

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    // lógica de login...
    navigate("/dashboard");
  }

  return <button onClick={handleLogin}>Entrar</button>;
}
```

---

## 🧭 4. Rutas dinámicas (`useParams`)

Podés tener rutas con variables (por ejemplo, `/productos/5`):

```jsx
import { Route, Routes } from "react-router-dom";
import Producto from "./pages/Producto";

function App() {
  return (
    <Routes>
      <Route path="/producto/:id" element={<Producto />} />
    </Routes>
  );
}
```

Y acceder al parámetro usando **`useParams`**:

```jsx
import { useParams } from "react-router-dom";

function Producto() {
  const { id } = useParams();

  return <h2>Detalle del producto #{id}</h2>;
}
```

---

## 🧱 5. Layouts y rutas anidadas

Podés crear una estructura con **layouts** para que algunas partes se mantengan fijas (por ejemplo, un navbar o sidebar):

```jsx
// App.jsx
import { Routes, Route, Outlet, Link } from "react-router-dom";

function Layout() {
  return (
    <div>
      <nav>
        <Link to="/">Inicio</Link>
        <Link to="/blog">Blog</Link>
      </nav>
      <hr />
      <Outlet /> {/* Aquí se renderizan las rutas hijas */}
    </div>
  );
}

function Blog() {
  return <h2>Página del Blog</h2>;
}

function Home() {
  return <h2>Página de inicio</h2>;
}

export default function App() {
  return (
    <Routes>
      <Route path="/" element={<Layout />}>
        <Route index element={<Home />} /> {/* Ruta por defecto */}
        <Route path="blog" element={<Blog />} />
      </Route>
    </Routes>
  );
}
```

---

## 🧩 6. Rutas 404 (No encontrada)

Si ninguna ruta coincide, podés mostrar una página personalizada:

```jsx
<Route path="*" element={<h2>404 - Página no encontrada</h2>} />
```

---

## ✅ Resumen

|Concepto|Hook / Componente|
|---|---|
|Definir rutas|`<Routes>`, `<Route>`|
|Navegación por links|`<Link to="/ruta" />`|
|Navegación programática|`useNavigate()`|
|Parámetros en la URL|`useParams()`|
|Agrupar rutas con layout|`<Outlet />`|

---

## 🧭 Diferencia entre `<Route>` y `<Link>`

### 🧱 **1. `<Route>` → Define qué se muestra en cada URL**

El componente `<Route>` se usa para **declarar las rutas** de tu aplicación.  
Básicamente le decís:

> “Cuando el usuario esté en esta URL, mostrale este componente”.

Ejemplo:

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```

📌 Significa:

- Cuando la URL sea `/`, se renderiza el componente `<Home />`
- Cuando la URL sea `/about`, se renderiza `<About />`

🧠 **`<Route>` no crea navegación**, solo define qué se muestra según la ruta actual.

---

### 🧭 **2. `<Link>` → Permite navegar entre rutas**

El componente `<Link>` sirve para **cambiar de página** sin recargar la app.  
Hace lo mismo que un `<a href="...">`, pero sin recargar el navegador (navegación SPA: _Single Page Application_).

Ejemplo:

```jsx
<nav>
  <Link to="/">Inicio</Link>
  <Link to="/about">Sobre nosotros</Link>
</nav>
```

📌 Al hacer clic, React Router **actualiza la URL** y **renderiza el componente** correcto (según tus `<Route>`).

---

### 🔁 En resumen

|Componente|Qué hace|Ejemplo|
|---|---|---|
|`<Route>`|Define **qué componente se muestra** según la URL|`<Route path="/about" element={<About />} />`|
|`<Link>`|Permite **navegar a otra URL** sin recargar|`<Link to="/about">Ir a About</Link>`|

---

### 🧠 Analogía rápida

|Caso|Explicación|
|---|---|
|`<Route>`|Es como el **mapa** de tu sitio: “si estás en `/about`, mostrá esta página”.|
|`<Link>`|Es como un **botón o enlace** que lleva al usuario a otra parte del mapa.|

---
