## 🧩 **1. Qué son las props**

**Props** (abreviatura de _properties_) son **datos que se envían desde un componente padre a uno hijo**.  
Te permiten **reutilizar componentes** y hacerlos más dinámicos.

📘 Las props son **solo de lectura** (no se pueden modificar dentro del hijo).

---

### 🔹 Ejemplo básico:

```jsx
function Saludo({ nombre }) {
  return <h2>Hola, {nombre} 👋</h2>;
}

function App() {
  return (
    <div>
      <Saludo nombre="Julio" />
      <Saludo nombre="María" />
    </div>
  );
}
```

🔍 Qué pasa:

- `App` envía una prop llamada `nombre` a `Saludo`.
- El componente hijo la recibe como argumento y la usa dentro del JSX.

---

## ⚙️ **2. Enviar funciones como props**

También podés pasar **funciones** como props.  
Esto sirve cuando el componente hijo necesita **comunicar algo hacia el padre** (por ejemplo, un evento o acción).

---

### 🔹 Ejemplo: el hijo avisa al padre

```jsx
function Boton({ onSaludar }) {
  return <button onClick={onSaludar}>Saludar</button>;
}

function App() {
  function mostrarSaludo() {
    alert("¡Hola desde el padre!");
  }

  return <Boton onSaludar={mostrarSaludo} />;
}
```

📘 Explicación:

- El **padre** (`App`) define una función.
- Se la pasa al **hijo** (`Boton`) por props.
- El hijo la ejecuta cuando el usuario hace clic.

Así el flujo de datos va en sentido inverso → del hijo al padre.

---

## 🔁 **3. Flujo de datos en React**

📈 El flujo de datos es **unidireccional**:

```
Padre → Hijo → Nieto
```

Cada componente tiene su propio estado y puede enviar datos hacia abajo (props),  
pero si el hijo necesita modificar algo del padre, debe hacerlo a través de una **función que el padre le pasó**.

---

## ⚠️ **4. Prop drilling (y cómo evitarlo)**

El **prop drilling** ocurre cuando tenés que pasar una prop por **muchos niveles de componentes** solo para que un componente lejano la use.

Ejemplo:

```
App → ComponenteA → ComponenteB → ComponenteC
```

Y la prop se necesita solo en `C`.

🧠 En esos casos, se suele usar:

- **Context API**
- **Zustand** o **Redux**  
    para evitar pasar props innecesarias.

(Pero eso lo veremos en módulos más avanzados 😉)

---

## 🎯 **5. Ejemplo práctico — Lista dinámica con input**

Vamos a armar un mini proyecto con **dos componentes**:

- `App` (padre)
- `Lista` (hijo)

### 🔹 App.jsx

```jsx
import { useState } from "react";
import Lista from "./components/Lista";

function App() {
  const [items, setItems] = useState([]);
  const [nuevoItem, setNuevoItem] = useState("");

  function agregarItem() {
    if (nuevoItem.trim() === "") return;
    setItems([...items, nuevoItem]);
    setNuevoItem("");
  }

  return (
    <div>
      <h2>📦 Lista dinámica</h2>
      <input
        type="text"
        placeholder="Nuevo ítem..."
        value={nuevoItem}
        onChange={(e) => setNuevoItem(e.target.value)}
      />
      <button onClick={agregarItem}>Agregar</button>

      {/* Paso la lista al componente hijo */}
      <Lista elementos={items} />
    </div>
  );
}

export default App;
```

---

### 🔹 components/Lista.jsx

```jsx
function Lista({ elementos }) {
  if (elementos.length === 0) {
    return <p>No hay elementos 😅</p>;
  }

  return (
    <ul>
      {elementos.map((el, index) => (
        <li key={index}>{el}</li>
      ))}
    </ul>
  );
}

export default Lista;
```

---

📘 **Qué aprendés con este ejercicio:**

- El estado (`items`) vive en el padre.
- El hijo (`Lista`) **recibe los datos** mediante `props`.
- Cuando se actualiza el estado en el padre, React vuelve a renderizar el hijo automáticamente.

---
