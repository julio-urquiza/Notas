Perfecto 🚀  
En **React**, los **Hooks** son funciones especiales que te permiten **usar el estado y otras características de React sin necesidad de escribir clases**.

Aparecieron en **React 16.8** y cambiaron totalmente la forma en que se construyen los componentes.

---

## 🔑 ¿Qué son los hooks?

Son **funciones predefinidas** (y también personalizables) que te permiten:

- Manejar estado (`useState`)
- Responder a efectos secundarios como llamadas a APIs (`useEffect`)
- Acceder al contexto (`useContext`)
- Optimizar rendimiento (`useMemo`, `useCallback`)
- Manejar referencias a elementos o valores mutables (`useRef`)
- Crear tus propios **custom hooks**

---

## 🧩 Hooks más importantes

### 1. **useState**

Sirve para manejar variables de estado dentro de un componente funcional.

```jsx
import { useState } from "react";

function Contador() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Has hecho clic {count} veces</p>
      <button onClick={() => setCount(count + 1)}>Sumar</button>
    </div>
  );
}
```

---

### 2. **useEffect**

Sirve para manejar **efectos secundarios** (fetch, timers, subscripciones).  
Se ejecuta después del renderizado.

```jsx
import { useEffect, useState } from "react";

function Usuarios() {
  const [usuarios, setUsuarios] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsuarios(data));
  }, []); // [] → se ejecuta solo una vez

  return <ul>{usuarios.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}
```

---

### 3. **useContext**

Permite acceder a un **Contexto** sin necesidad de `props` en cadena.

```jsx
const TemaContext = React.createContext("light");

function Componente() {
  const tema = useContext(TemaContext);
  return <h1>Tema actual: {tema}</h1>;
}
```

---

### 4. **useRef**

Permite guardar valores que **no provocan re-render** o acceder a elementos del DOM.

```jsx
import { useRef } from "react";

function InputFocus() {
  const inputRef = useRef(null);

  const enfocar = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={enfocar}>Enfocar</button>
    </>
  );
}
```

---

### 5. **useMemo** y **useCallback**

Optimización:

- **useMemo**: memoriza valores calculados.
- **useCallback**: memoriza funciones para que no se creen de nuevo en cada render.

---

## ⚡ Reglas de los Hooks

1. Solo se usan en **componentes funcionales** o en **custom hooks**.
2. Se deben llamar siempre en el **mismo orden** (no dentro de `if`, `for`, etc).
3. Siempre empiezan con el prefijo **“use”**.

---