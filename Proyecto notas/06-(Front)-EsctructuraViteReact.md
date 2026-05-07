# Estructura típica de un proyecto React

```plaintext
mi-app/
│
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   ├── pages/
│   ├── layouts/
│   ├── services/
│   ├── hooks/
│   ├── context/
│   ├── routes/
│   ├── styles/
│   ├── utils/
│   ├── App.jsx
│   └── main.jsx
│
├── package.json
├── vite.config.js
└── node_modules/
```

---

# Explicación de cada parte

---

## `src/`

Es la carpeta más importante.

Contiene todo el código fuente de la aplicación.

---

# Archivos principales

## `main.jsx`

Es el punto de entrada de React.

Ahí se monta la aplicación en el DOM.

Ejemplo:

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")).render(
  <App />
);
```

Podés decir:

> “main.jsx conecta React con el HTML real.”

---

## `App.jsx`

Es el componente principal.

Generalmente contiene:

* rutas
* layouts
* estructura general

Ejemplo:

```jsx
function App() {
  return <h1>Hola mundo</h1>;
}

export default App;
```

---

# Carpetas importantes

---

## `components/`

Contiene componentes reutilizables.

Ejemplos:

```plaintext
components/
├── Button.jsx
├── Navbar.jsx
├── Card.jsx
```

Un componente es una parte reutilizable de la interfaz.

Por ejemplo:

* botón
* navbar
* modal
* formulario

---

## `pages/`

Representa páginas completas.

Ejemplo:

```plaintext
pages/
├── Home.jsx
├── Login.jsx
├── Profile.jsx
```

Normalmente cada ruta tiene una página.

Ejemplo:

```plaintext
/login → Login.jsx
/profile → Profile.jsx
```

---

## `layouts/`

Define estructuras visuales compartidas.

Por ejemplo:

```plaintext
layouts/
├── MainLayout.jsx
├── AdminLayout.jsx
```

Un layout suele contener:

* navbar
* sidebar
* footer

y renderiza páginas dentro.

---

## `services/`

Contiene lógica para comunicarse con el backend.

Ejemplo:

```plaintext
services/
├── authService.js
├── userService.js
```

Ahí suele usarse:

* fetch
* axios
* llamadas HTTP

Ejemplo:

```js
export async function getUsers() {
  const response = await fetch("/api/users");
  return response.json();
}
```

---

## `hooks/`

Custom hooks reutilizables.

Ejemplo:

```plaintext
hooks/
├── useAuth.js
├── useFetch.js
```

Permiten reutilizar lógica entre componentes.

---

## `context/`

Manejo de estado global usando Context API.

Ejemplo:

```plaintext
context/
├── AuthContext.jsx
```

Sirve para compartir información global:

* usuario logueado
* tema
* carrito
* idioma

---

## `routes/`

Configuración de rutas.

Ejemplo:

```plaintext
routes/
├── AppRoutes.jsx
```

Con React Router.

---

## `assets/`

Archivos estáticos internos.

Ejemplo:

```plaintext
assets/
├── logo.png
├── background.jpg
```

---

## `styles/`

CSS global o variables de estilos.

Ejemplo:

```plaintext
styles/
├── global.css
├── variables.css
```

---

## `utils/`

Funciones auxiliares reutilizables.

Ejemplo:

```plaintext
utils/
├── formatDate.js
├── validations.js
```

---

# `public/`

Archivos públicos accesibles directamente.

Por ejemplo:

```plaintext
public/
├── favicon.ico
```

---

# Conceptualmente

Podrías decir:

> “React organiza la aplicación en componentes reutilizables.
> La estructura del proyecto separa responsabilidades para que el código sea más mantenible y escalable.”

---

# Flujo típico de una aplicación React

Podés explicarlo así:

```plaintext
Usuario interactúa con la UI
        ↓
Componente React
        ↓
Hook / Estado
        ↓
Service
        ↓
Backend API
        ↓
Respuesta JSON
        ↓
React actualiza la interfaz
```

---

# Diferencia entre componente y página

Esto suele confundir mucho.

## Componente

Parte reutilizable.

Ejemplo:

```plaintext
Button
Card
Navbar
Input
```

---

## Página

Vista completa asociada a una ruta.

Ejemplo:

```plaintext
Home
Login
Dashboard
```

La página usa varios componentes.

---

# Cómo suelen crecer los proyectos

## Proyecto pequeño

```plaintext
src/
├── components/
├── App.jsx
```

---

## Proyecto mediano

```plaintext
src/
├── components/
├── pages/
├── services/
├── hooks/
```

---

## Proyecto grande

Se agregan:

* arquitectura modular
* feature folders
* state management
* testing
* DTOs
* validaciones
* permisos
* providers

---

# Estructura moderna por feature (muy usada)

En proyecto grandes se utiliza esta otro tipo de organización:

```plaintext
src/
├── features/
│   ├── auth/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── hooks/
```

Ventaja:

Cada módulo tiene todo junto.

Muy útil en proyectos grandes.
