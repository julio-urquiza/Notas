### 🎯 Objetivo

Entender cómo y cuándo React ejecuta el código dentro de los componentes, y aprender a usar el **hook `useEffect`** para manejar efectos secundarios (fetch, suscripciones, timers, etc.).

---

## 🧠 1. ¿Qué es el ciclo de vida de un componente?

En React, los componentes **pasan por tres etapas principales**:

1. **Montaje (Mounting)** → cuando el componente se muestra por primera vez.
2. **Actualización (Updating)** → cuando cambian sus props o su estado.
3. **Desmontaje (Unmounting)** → cuando el componente se elimina del DOM.

Antes, en _class components_, existían métodos como `componentDidMount`, `componentDidUpdate`, y `componentWillUnmount`.  
En los componentes funcionales modernos, **todo eso se maneja con `useEffect`**.

---

## ⚙️ 2. ¿Qué es `useEffect`?

`useEffect` es un **hook** que te permite ejecutar código en ciertos momentos del ciclo de vida.

```jsx
import { useState, useEffect } from "react";

function Contador() {
  const [count, setCount] = useState(0);

  // useEffect se ejecuta después de que el componente se renderiza
  useEffect(() => {
    console.log("El componente se montó o se actualizó");
  });

  return (
    <div>
      <p>Has hecho clic {count} veces</p>
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </div>
  );
}
```

---

## 🧩 3. Controlar cuándo se ejecuta `useEffect`

El segundo parámetro de `useEffect` define **cuándo** se ejecuta:

### 🕐 a) En cada renderizado

```jsx
useEffect(() => {
  console.log("Se ejecuta siempre");
});
```

### ⚡ b) Solo una vez (al montar)

```jsx
useEffect(() => {
  console.log("Solo al montar el componente");
}, []);
```

### 🔁 c) Cuando cambia una dependencia

```jsx
useEffect(() => {
  console.log("El contador cambió:", count);
}, [count]);
```

---

## 🧹 4. Limpiar efectos (cleanup)

Cuando un componente se desmonta, podemos ejecutar una **función de limpieza**.

Ejemplo: eliminar un `setInterval` o un `EventListener`:

```jsx
useEffect(() => {
  const intervalo = setInterval(() => {
    console.log("tick");
  }, 1000);

  // cleanup: se ejecuta cuando el componente se desmonta
  return () => clearInterval(intervalo);
}, []);
```

---

## 🌐 5. Ejemplo práctico: Fetch de datos

```jsx
import { useState, useEffect } from "react";

function Usuarios() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => res.json())
      .then((data) => setUsers(data));
  }, []); // solo al montar

  return (
    <div>
      <h2>Usuarios</h2>
      <ul>
        {users.map((u) => (
          <li key={u.id}>{u.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

``` jsx
import { useState, useEffect } from "react";

function Usuarios() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => {
        if (!res.ok) throw new Error("Error en la respuesta del servidor");
        return res.json();
      })
      .then((data) => setUsers(data))
      .catch((err) => setError(err.message))
      .finally(() => setLoading(false));
  }, []); // se ejecuta solo al montar

  if (loading) return <p>Cargando usuarios...</p>;
  if (error) return <p>❌ Error: {error}</p>;

  return (
    <div>
      <h2>Lista de usuarios</h2>
      <ul>
        {users.map((u) => (
          <li key={u.id}>{u.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

## ✅ 6. Buenas prácticas

- Siempre incluye las **dependencias necesarias** en el array del `useEffect`.
- Si `useEffect` se vuelve complejo, **divídelo** en varios efectos más pequeños.
- Usa `cleanup` cuando agregues listeners, timers o suscripciones.
- No usar `useEffect` para cálculos o lógica de renderizado (solo efectos “externos”).
- Siempre manejar **loading** y **errores** al hacer peticiones.  
- Colocar las dependencias correctas en el array de `useEffect`.

---

``` jsx
import { useState, useEffect } from "react";

function Usuarios() {
  const [user, setUser] = useState({});
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    fetch("https://randomuser.me/api/?results=5")
      .then((res) => {
        if (!res.ok) throw new Error("Error en la respuesta del servidor");
        return res.json();
      })
      .then((data) => setUser(data))
      .catch((err) => setError(err.message))
      .finally(() => setLoading(false));
  }, []); // se ejecuta solo al montar

  if (loading) return <p>Cargando usuarios...</p>;
  if (error) return <p>❌ Error: {error}</p>;

  return (
    <div>
        <h2>Usuarios</h2>
        <ul>
            {user.results.map((u) => (
                <div>
                    <img src={u.picture.large} alt="a"/>
                    <li key={u.id.value}>
	                    {u.name.title} 
	                    {u.name.first} 
	                    {u.name.last}
					</li>
                <div/>
            ))}
        </ul>
    </div>
  );
}
export default Usuarios;
```