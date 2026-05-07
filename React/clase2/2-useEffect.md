`useEffect` se usa para **manejar efectos secundarios** en un componente funcional. En React, los efectos secundarios son cosas que ocurren **fuera del flujo normal de renderizado**, como:

- Consultas a APIs (fetch, axios).
- Suscripciones a eventos (scroll, resize, websockets).
- Modificar el DOM directamente.
- Guardar datos en localStorage o en un backend.

---

### Sintaxis básica

```jsx
import { useEffect } from "react";

function MiComponente() {
  useEffect(() => {
    console.log("El componente se montó o actualizó");

    return () => {
      console.log("El componente se va a desmontar");
    };
  }, []); // Dependencias

  return <div>Hola</div>;
}
```

---

### Explicación de cada parte

1. **Primero el callback**:
   ```js
    () => {
        console.log("efecto");
    }
    ```
    Este código se ejecuta **después de que React renderiza el componente**.
2. **Return opcional**:
   ```js
    return () => { console.log("cleanup") }
    ```
    Esto es para “limpiar” efectos, por ejemplo cancelar un timer o quitar un listener.
3. **Array de dependencias `[]`**:
    - Si está vacío `[]` → se ejecuta **solo una vez** al montar el componente (como `componentDidMount`).
    - Si tiene variables `[count, user]` → se ejecuta cada vez que alguna de esas variables cambie.
    - Si no se pone nada → se ejecuta **después de cada render**.

---

### Ejemplo práctico: fetch de datos

```jsx
import { useEffect, useState } from "react";

function Usuarios() {
  const [usuarios, setUsuarios] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsuarios(data));
  }, []); // Solo al montar

  return (
    <ul>
      {usuarios.map(u => (
        <li key={u.id}>{u.name}</li>
      ))}
    </ul>
  );
}
```

Aquí `useEffect` hace la llamada a la API **solo cuando el componente se monta**, y luego actualiza el estado.

---