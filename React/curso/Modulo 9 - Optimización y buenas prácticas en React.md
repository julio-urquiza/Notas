## 🚀 **Objetivo del módulo**

Aprender a optimizar el rendimiento de tus aplicaciones React y aplicar patrones usados en proyectos reales.

---

## 🔹 1. `React.memo()`

### 🧠 Qué es:

`React.memo` es una **función que evita que un componente funcional se vuelva a renderizar** si sus props no cambiaron.

### 🧩 Ejemplo:

```jsx
const Usuario = React.memo(function Usuario({ nombre }) {
  console.log("Renderizando usuario...");
  return <p>{nombre}</p>;
});
```

Ahora, si el componente padre se vuelve a renderizar pero la prop `nombre` **no cambia**,  
`Usuario` **no se vuelve a renderizar**.

🧩 **Ideal para:** componentes que reciben props y hacen render costoso (tablas, listas, imágenes, etc.)

---

## 🔹 2. `useMemo()`

### 🧠 Qué hace:

`useMemo` **memoriza un cálculo** (el resultado de una función) para no volver a hacerlo si las dependencias no cambian.

### 🧩 Ejemplo:

```jsx
const resultado = useMemo(() => {
  return listaUsuarios.filter(u => u.activo);
}, [listaUsuarios]);
```

✅ React solo ejecuta el filtro si `listaUsuarios` cambia.  
Si no, usa el valor **guardado en memoria**.

🧩 **Ideal para:** cálculos pesados (filtros, sorting, etc.)

---

## 🔹 3. `useCallback()`

### 🧠 Qué hace:

`useCallback` **memoriza una función**, evitando que se vuelva a crear en cada render.

### 🧩 Ejemplo:

```jsx
const manejarClick = useCallback(() => {
  console.log("Click!");
}, []);
```

✅ Cada vez que el componente se renderiza, la referencia de `manejarClick` sigue siendo la misma,  
lo que ayuda a evitar renders innecesarios en componentes hijos que reciben esa función como prop.

🧩 **Ideal para:** callbacks que se pasan a componentes hijos.

---

## 🔹 4. Lazy Loading

### 🧠 Qué es:

“Lazy loading” o carga diferida significa **cargar componentes solo cuando se necesitan**,  
en lugar de incluir todo en el bundle inicial.

### 🧩 Ejemplo:

```jsx
import React, { lazy, Suspense } from "react";

const PaginaPerfil = lazy(() => import("./PaginaPerfil"));

function App() {
  return (
    <Suspense fallback={<p>Cargando...</p>}>
      <PaginaPerfil />
    </Suspense>
  );
}
```

✅ React solo carga `PaginaPerfil` cuando se intenta renderizar.  
Esto mejora **el tiempo de carga inicial**.

---

## 🔹 5. `Suspense`

`<Suspense>` se usa para mostrar un **componente de carga temporal** mientras algo se está importando (por ejemplo, con lazy loading).

```jsx
<Suspense fallback={<p>Cargando componente...</p>}>
  <ComponentePesado />
</Suspense>
```

🧩 **Ideal para:** mejorar la experiencia de usuario cuando partes del sitio tardan en cargarse.

---

## 🔹 6. Estructura profesional de proyectos

Una estructura recomendada para React es:

```
src/
 ├─ components/
 │   ├─ Button/
 │   │   ├─ Button.jsx
 │   │   └─ Button.css
 │   └─ Navbar/
 │       ├─ Navbar.jsx
 │       └─ Navbar.css
 ├─ pages/
 │   ├─ Home.jsx
 │   └─ About.jsx
 ├─ hooks/
 │   └─ useAuth.js
 ├─ context/
 │   └─ AuthContext.jsx
 ├─ services/
 │   └─ api.js
 ├─ assets/
 │   └─ logo.png
 ├─ App.jsx
 └─ main.jsx
```

📦 **Ventajas:**

- Separás lógica (hooks), UI (components) y páginas (pages)
- Escala mejor en equipos grandes
- Más fácil de mantener y refactorizar

---

## 🧭 **Resumen del módulo**

|Concepto|Qué hace|Cuándo usar|
|---|---|---|
|`React.memo`|Evita re-renders innecesarios|Componentes puros|
|`useMemo`|Memoriza resultados de cálculos|Cálculos costosos|
|`useCallback`|Memoriza funciones|Callbacks pasados a hijos|
|`lazy` y `Suspense`|Carga diferida de componentes|Mejorar performance inicial|
|Estructura modular|Organización limpia del proyecto|Siempre|
