React es una **librería de JavaScript** creada por **Facebook (Meta)** que sirve para construir **interfaces de usuario (UI)** de manera rápida, modular y eficiente.

👉 En otras palabras: te ayuda a crear aplicaciones web (y también móviles con React Native) dividiendo la interfaz en **componentes reutilizables**.

---

### 🔑 Características principales de React

1. **Basado en componentes**
    - Todo en React son piezas pequeñas llamadas _componentes_.
    - Cada componente puede representar un botón, un formulario, una tarjeta, etc.
    - Estos componentes se combinan como piezas de LEGO para armar la interfaz.
2. **Virtual DOM**
    - React no actualiza directamente el DOM del navegador (que es lento).
    - Usa una copia virtual (_Virtual DOM_) y solo aplica los cambios necesarios en la parte que se modificó → esto lo hace **muy rápido**.
3. **Declarativo**
    - En lugar de decir _cómo_ cambiar la interfaz paso a paso, vos describís _qué querés mostrar_ y React se encarga del resto.
4. **Unidireccional (flujo de datos)**
    - Los datos fluyen en una sola dirección: de padres a hijos.
    - Esto hace que sea más fácil controlar y entender cómo cambian los datos en tu aplicación.
5. **Ecosistema gigante**
    - Hay miles de librerías y herramientas que complementan React: React Router (rutas), Redux (estado global), Next.js (SSR y fullstack), etc.

---

### 🔹 Ejemplo básico en React

```jsx
// App.jsx
function App() {
  return (
    <div>
      <h1>¡Hola, mundo con React!</h1>
      <p>Esto es un componente.</p>
    </div>
  );
}

export default App;
```

---

### 🚀 ¿Para qué se usa?

- Aplicaciones web interactivas (Facebook, Instagram, Netflix usan React).
- Dashboards y paneles de control.
- Aplicaciones móviles con **React Native**.
- Sitios web estáticos o dinámicos (con frameworks como **Next.js**).

---
