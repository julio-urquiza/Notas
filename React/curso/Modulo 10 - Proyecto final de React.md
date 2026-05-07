## 🧩 **Objetivo**

Construir una aplicación funcional en React que te permita:

- ✅ Agregar tareas
- ✅ Marcarlas como completadas
- ✅ Eliminarlas
- ✅ Guardarlas en memoria local
- ✅ Usar rutas, hooks y context API

---

## 🏗️ **Estructura del proyecto**

```
src/
 ├─ components/
 │   ├─ TaskItem.jsx
 │   └─ TaskForm.jsx
 ├─ context/
 │   └─ TaskContext.jsx
 ├─ pages/
 │   ├─ Home.jsx
 │   └─ About.jsx
 ├─ App.jsx
 ├─ main.jsx
```

---

## ⚙️ Paso 1: Crear el contexto global

📄 **`src/context/TaskContext.jsx`**

```jsx
import { createContext, useState } from "react";

export const TaskContext = createContext();

export function TaskProvider({ children }) {
  const [tasks, setTasks] = useState([]);

  const addTask = (text) => {
    const newTask = { id: Date.now(), text, completed: false };
    setTasks([...tasks, newTask]);
  };

  const toggleTask = (id) => {
    setTasks(tasks.map(t => 
      t.id === id ? { ...t, completed: !t.completed } : t
    ));
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter(t => t.id !== id));
  };

  return (
    <TaskContext.Provider value={{ tasks, addTask, toggleTask, deleteTask }}>
      {children}
    </TaskContext.Provider>
  );
}
```

💡 Este contexto maneja todo el **estado global** de las tareas.

---

## ⚙️ Paso 2: Crear el formulario para agregar tareas

📄 **`src/components/TaskForm.jsx`**

```jsx
import { useState, useContext } from "react";
import { TaskContext } from "../context/TaskContext";

export default function TaskForm() {
  const [text, setText] = useState("");
  const { addTask } = useContext(TaskContext);

  const handleSubmit = (e) => {
    e.preventDefault();
    if (!text.trim()) return;
    addTask(text);
    setText("");
  };

  return (
    <form onSubmit={handleSubmit} className="flex gap-2 my-4">
      <input
        type="text"
        value={text}
        onChange={(e) => setText(e.target.value)}
        placeholder="Nueva tarea..."
        className="border px-2 py-1 rounded w-full"
      />
      <button className="bg-blue-500 text-white px-4 rounded">Agregar</button>
    </form>
  );
}
```

---

## ⚙️ Paso 3: Crear la lista de tareas

📄 **`src/components/TaskItem.jsx`**

```jsx
import { useContext } from "react";
import { TaskContext } from "../context/TaskContext";

export default function TaskItem({ task }) {
  const { toggleTask, deleteTask } = useContext(TaskContext);

  return (
    <li className="flex justify-between items-center border-b py-2">
      <span
        onClick={() => toggleTask(task.id)}
        className={`cursor-pointer ${task.completed ? "line-through text-gray-500" : ""}`}
      >
        {task.text}
      </span>
      <button onClick={() => deleteTask(task.id)} className="text-red-500">
        ❌
      </button>
    </li>
  );
}
```

---

## ⚙️ Paso 4: Página principal

📄 **`src/pages/Home.jsx`**

```jsx
import { useContext } from "react";
import { TaskContext } from "../context/TaskContext";
import TaskForm from "../components/TaskForm";
import TaskItem from "../components/TaskItem";

export default function Home() {
  const { tasks } = useContext(TaskContext);

  return (
    <div className="p-4 max-w-md mx-auto">
      <h1 className="text-2xl font-bold mb-4">Gestor de Tareas ✅</h1>
      <TaskForm />
      <ul>
        {tasks.length === 0 && <p>No hay tareas todavía.</p>}
        {tasks.map(task => <TaskItem key={task.id} task={task} />)}
      </ul>
    </div>
  );
}
```

---

## ⚙️ Paso 5: Página “About”

📄 **`src/pages/About.jsx`**

```jsx
export default function About() {
  return (
    <div className="p-4 max-w-md mx-auto">
      <h1 className="text-2xl font-bold mb-4">Acerca de</h1>
      <p>Esta app fue creada con React + Context + Hooks.</p>
    </div>
  );
}
```

---

## ⚙️ Paso 6: Configurar rutas y contexto global

📄 **`src/App.jsx`**

```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import { TaskProvider } from "./context/TaskContext";
import Home from "./pages/Home";
import About from "./pages/About";

export default function App() {
  return (
    <TaskProvider>
      <Router>
        <nav className="flex gap-4 p-4 bg-gray-100">
          <Link to="/">Inicio</Link>
          <Link to="/about">Acerca de</Link>
        </nav>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
        </Routes>
      </Router>
    </TaskProvider>
  );
}
```

---

## ⚙️ Paso 7: Montar la app

📄 **`src/main.jsx`**

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

---

## 🎯 **Resultado final**

Una app completa que:

- Usa **Context API** para manejar estado global
- Usa **Hooks** (`useState`, `useContext`)
- Usa **React Router**
- Tiene **componentes reutilizables**
- Cumple buenas prácticas de estructura

---
