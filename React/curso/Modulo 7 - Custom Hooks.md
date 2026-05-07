## 🎯 Objetivo

Aprender a **crear tus propios hooks** para **reutilizar lógica de estado y efectos** entre distintos componentes.

---

## 🧠 1. ¿Qué es un Custom Hook?

Un **Custom Hook** (hook personalizado) es una **función de JavaScript** que:

- Empieza con la palabra `use`
- Puede usar otros hooks de React (`useState`, `useEffect`, etc.)
- Devuelve valores o funciones que podés usar en tus componentes    

🟢 Sirve para **extraer lógica repetida** y mantener tu código más organizado.

---

## 🧩 2. Ejemplo clásico: `useLocalStorage`

Queremos guardar y recuperar datos del `localStorage`, pero de forma **automática** y **reutilizable**.

Creamos un archivo:  
📁 `src/hooks/useLocalStorage.js`

```jsx
import { useState, useEffect } from "react";

export function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    const stored = localStorage.getItem(key);
    return stored ? JSON.parse(stored) : initialValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}
```

👉 Explicación:

- Lee el valor del `localStorage` al inicio.
- Guarda automáticamente el nuevo valor cuando cambia.
- Devuelve `[value, setValue]` igual que `useState`.

---

## 🧪 3. Cómo usarlo

```jsx
import { useLocalStorage } from "./hooks/useLocalStorage";

function App() {
  const [nombre, setNombre] = useLocalStorage("nombreUsuario", "");

  return (
    <div>
      <input
        value={nombre}
        onChange={(e) => setNombre(e.target.value)}
        placeholder="Tu nombre..."
      />
      <p>Hola, {nombre || "invitado"} 👋</p>
    </div>
  );
}

export default App;
```

✅ Si recargás la página, el valor sigue ahí gracias al `localStorage`.

---

## 🌐 4. Otro ejemplo: `useFetch`

Podemos crear un hook para hacer peticiones a APIs fácilmente.

📁 `src/hooks/useFetch.js`

```jsx
import { useState, useEffect } from "react";

export function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    if (!url) return;

    setLoading(true);
    fetch(url)
      .then((res) => {
        if (!res.ok) throw new Error("Error en la solicitud");
        return res.json();
      })
      .then((data) => setData(data))
      .catch((err) => setError(err.message))
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading, error };
}
```

🧩 Y lo usamos así:

```jsx
import { useFetch } from "./hooks/useFetch";

function Users() {
  const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/users");

  if (loading) return <p>Cargando...</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <ul>
      {data.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}

export default Users;
```

---

## 💡 5. Cuándo conviene crear un Custom Hook

✅ Cuando tenés **lógica repetida** entre varios componentes.  
✅ Cuando querés **separar lógica de presentación**.  
✅ Cuando necesitás **manejar side effects** (fetch, localStorage, etc.).

❌ No conviene hacerlo si solo lo usás **una vez** o si no aporta claridad.

---

## 🧠 6. Ejercicios

1. Crea un `useWindowWidth()` que devuelva el ancho actual de la ventana.
2. Crea un `useTheme()` que cambie el modo claro/oscuro y lo guarde en localStorage.
3. Crea un `useFetch()` con **cancelación automática** si cambia la URL.

---

## ✅ Resumen

| Hook              | Función                        | Reutilizable |
| ----------------- | ------------------------------ | ------------ |
| `useState`        | Manejar estado interno         | ❌            |
| `useEffect`       | Efectos secundarios            | ❌            |
| `useLocalStorage` | Guardar estado en localStorage | ✅            |
| `useFetch`        | Obtener datos desde una API    | ✅            |

---