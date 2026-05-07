## 🧠 **1. ¿Qué es el estado (`state`)?**

El **estado** es la **memoria interna del componente**.  
Sirve para **guardar valores que pueden cambiar con el tiempo**, y cuando cambian → React **vuelve a renderizar** el componente con el nuevo valor.

Para manejar estados, React nos da un **hook** llamado `useState`.

---

## ⚙️ **2. Hook `useState`**

### 📘 Sintaxis básica:

```jsx
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Has hecho clic {contador} veces</p>
      <button onClick={() => setContador(contador + 1)}>Sumar</button>
    </div>
  );
}
```

🔍 **Qué está pasando:**

- `useState(0)` → crea una **variable `contador`** y una **función `setContador`** para actualizarla.
- `0` es el **valor inicial**.
- Cuando llamás a `setContador`, React **re-renderiza** el componente mostrando el nuevo valor.

💡 `useState` puede guardar cualquier tipo de dato: número, string, booleano, objeto o array.

---

## 🖱️ **3. Eventos en React**

React usa eventos muy parecidos a los del DOM, pero **en camelCase**.

### Ejemplo:

```jsx
function Boton() {
  function handleClick() {
    alert("¡Hiciste clic!");
  }

  return <button onClick={handleClick}>Presióname</button>;
}
```

📌 Los eventos más comunes:

- `onClick` → al hacer clic
- `onChange` → cuando cambia un input
- `onSubmit` → al enviar un formulario
- `onMouseEnter`, `onMouseLeave`, etc.

---

## 🎯 **4. Renderizado condicional**

Podés mostrar elementos **según una condición**.  
React evalúa expresiones JS dentro de `{}`.

### Ejemplo:

```jsx
function Usuario({ logueado }) {
  return (
    <div>
      {logueado ? <h2>Bienvenido 🖐️</h2> : <h2>Inicia sesión</h2>}
    </div>
  );
}
```

💡 También podés usar `&&` para mostrar algo solo si se cumple la condición:

```jsx
{logueado && <p>Tenés mensajes nuevos</p>}
```

---

## 📋 **5. Listas y el método `.map()`**

Cuando querés mostrar **muchos elementos**, usás `.map()` para renderizarlos dinámicamente.

### Ejemplo:

```jsx
function ListaTareas() {
  const tareas = ["Estudiar React", "Hacer ejercicio", "Leer un libro"];

  return (
    <ul>
      {tareas.map((tarea, index) => (
        <li key={index}>{tarea}</li>
      ))}
    </ul>
  );
}
```

🔑 **IMPORTANTE:** cada elemento debe tener una **propiedad `key` única**, para que React pueda identificarlo correctamente.

---

## 🧩 **6. Ejemplo completo: Contador con control**

```jsx
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  function incrementar() {
    setContador(contador + 1);
  }

  function decrementar() {
    setContador(contador - 1);
  }

  return (
    <div>
      <h2>Contador: {contador}</h2>
      <button onClick={decrementar}>-</button>
      <button onClick={incrementar}>+</button>
      {contador === 10 && <p>¡Llegaste a 10! 🎉</p>}
    </div>
  );
}

export default Contador;
```

✅ **Lo que aprendés acá:**

- Uso de `useState`
- Manejo de eventos (`onClick`)
- Renderizado condicional
- Re-renderizado automático

---

## ✅ **ListaCompras.jsx**

```jsx
import { useState } from "react";

function ListaCompras() {
  const [producto, setProducto] = useState("");
  const [lista, setLista] = useState([]);

  function agregarProducto() {
    if (producto.trim() === "") return;
    setLista([...lista, producto]);
    setProducto("");
  }

  return (
    <div style={{ textAlign: "center", marginTop: "20px" }}>
      <h2>🛒 Lista de Compras</h2>
      <input
        type="text"
        placeholder="Agregar producto..."
        value={producto}
        onChange={(e) => setProducto(e.target.value)}
      />
      <button onClick={agregarProducto} style={{ marginLeft: "10px" }}>
        Agregar
      </button>

      {lista.length === 0 ? (
        <p>No hay productos en la lista 😅</p>
      ) : (
        <ul>
          {lista.map((item, index) => (
            <li key={index}>{item}</li>
          ))}
        </ul>
      )}
    </div>
  );
}

export default ListaCompras;
```

---
