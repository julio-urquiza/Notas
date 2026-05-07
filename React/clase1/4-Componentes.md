En **React**, los **componentes** son la pieza fundamental: todo lo que construís en una aplicación se arma combinando componentes, como si fueran bloques de Lego.

👉 Te cuento lo esencial:

### 1. ¿Qué es un componente?

Un componente es una función (o clase en versiones antiguas) que devuelve **JSX** (esa mezcla de HTML y JS). Cada componente representa una **parte de la interfaz**: un botón, un formulario, una card, o incluso la página entera.

Ejemplo de un componente simple:

```jsx
function Saludo() {
  return <h1>Hola, mundo!</h1>;
}
```

### 2. Tipos de componentes

- **Componentes de función (function components):**  
    Son los más usados hoy en día. Simples funciones que retornan JSX.
   ```jsx
    const Boton = () => <button>Click!</button>;
    ```
- **Componentes de clase:**  
    Se usaban antes de los _hooks_. Hoy están en desuso, pero todavía existen en proyectos viejos.
   ```jsx
    class Boton extends React.Component {
      render() {
        return <button>Click!</button>;
      }
    }
    ```
    
### 3. Props (propiedades)

Los componentes pueden recibir datos como parámetros llamados **props**.

```jsx
function Saludo(props) {
  return <h1>Hola, {props.nombre}!</h1>;
}

// Uso
<Saludo nombre="Julio" />
```

### 4. Estado (state)

El estado es la "memoria interna" de un componente. Se maneja con **hooks** como `useState`.

```jsx
import { useState } from "react";

function Contador() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Clicks: {count}</p>
      <button onClick={() => setCount(count + 1)}>Sumar</button>
    </div>
  );
}
```

### 5. Composición de componentes

Podés **armar componentes dentro de otros** para estructurar tu app.

```jsx
function App() {
  return (
    <div>
      <Saludo nombre="Julio" />
      <Contador />
    </div>
  );
}
```

En resumen:

- Un componente es una función que retorna JSX.
- Se pueden **reutilizar** en diferentes partes.
- Manejan **props** (datos de afuera) y **estado** (datos internos).
- Son **componibles**: se arman unos dentro de otros.

