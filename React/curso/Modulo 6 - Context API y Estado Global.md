### 🎯 Objetivo

Entender cómo usar **Context API** y **useContext** para manejar **estado global**, como el tema oscuro/claro, idioma o usuario logueado.

---

## 🧠 1. El problema del “Prop Drilling”

En React, los datos normalmente se pasan **por props**:

```jsx
function App() {
  return <Hijo valor="Hola" />;
}
```

Pero si necesitás pasar el mismo dato a muchos niveles (App → Hijo → Nieto → Bisnieto), terminás con esto:

```jsx
<App>
  <Hijo valor="Hola">
    <Nieto valor="Hola">
      <Bisnieto valor="Hola" />
    </Nieto>
  </Hijo>
</App>
```

😩 Esto se llama **prop drilling** (perforar props).

Para evitarlo, usamos **Context API**, que nos deja **compartir datos globalmente** sin pasarlos manualmente por cada nivel.

---

## ⚙️ 2. Crear un Contexto

1. **Crear un archivo** `ThemeContext.jsx`:

```jsx
import { createContext, useState } from "react";

export const ThemeContext = createContext();

export function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme((prev) => (prev === "light" ? "dark" : "light"));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}
```

👉 Este archivo:

- Crea un contexto.
- Define un **estado global (`theme`)**.
- Provee funciones (como `toggleTheme`) a toda la app.

---

## 🧩 3. Envolver la aplicación con el Provider

En `main.jsx`:

```jsx
import { ThemeProvider } from "./context/ThemeContext";

createRoot(document.getElementById("root")).render(
  <ThemeProvider>
    <App />
  </ThemeProvider>
);
```

Ahora **todos los componentes dentro de `<App />`** pueden acceder al contexto.

---

## 🪄 4. Usar el contexto en un componente

Por ejemplo, en `Navbar.jsx`:

```jsx
import { useContext } from "react";
import { ThemeContext } from "../context/ThemeContext";

function Navbar() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <nav
      style={{
        background: theme === "light" ? "#fff" : "#222",
        color: theme === "light" ? "#000" : "#fff",
        padding: "1rem",
      }}
    >
      <span>Modo: {theme}</span>
      <button onClick={toggleTheme} style={{ marginLeft: "1rem" }}>
        Cambiar tema
      </button>
    </nav>
  );
}

export default Navbar;
```

🧠 `useContext(ThemeContext)` te permite **leer y modificar** el valor global.

---

## 🌑 5. Efecto global (modo oscuro)

Podés usar el valor del contexto en el `App.jsx` también:

```jsx
import { useContext } from "react";
import { ThemeContext } from "./context/ThemeContext";
import Navbar from "./components/Navbar";

function App() {
  const { theme } = useContext(ThemeContext);

  return (
    <div
      style={{
        height: "100vh",
        background: theme === "light" ? "#f5f5f5" : "#111",
        color: theme === "light" ? "#111" : "#f5f5f5",
        transition: "0.3s",
      }}
    >
      <Navbar />
      <h1>Bienvenido a mi App</h1>
    </div>
  );
}

export default App;
```

🔄 Todo cambia automáticamente cuando el usuario hace clic en “Cambiar tema”.

---

## 💪 Ejercicio propuesto

Crea una app con **Context API** que tenga:

- Un **navbar** con un botón para cambiar entre _modo claro y oscuro_.
- Un **texto o tarjeta** que cambie su color automáticamente al cambiar el tema.
- Bonus: guarda el modo en `localStorage` para que se mantenga al recargar la página.

---

## ✅ Resumen

|Concepto|Hook / Componente|Función|
|---|---|---|
|`createContext()`|Crear un contexto global||
|`<Context.Provider>`|Compartir el valor global||
|`useContext()`|Acceder al valor global||
|`ThemeProvider`|Componente que envuelve toda la app||

---
