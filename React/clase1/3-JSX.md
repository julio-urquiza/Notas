JSX es una **extensión de la sintaxis de JavaScript** que te permite escribir código que **mezcla HTML con JavaScript** dentro de React.

👉 Es como escribir HTML dentro de tu código JS, pero con superpoderes.  
Al final, JSX **se transforma en JavaScript puro** gracias a herramientas como Babel.

---

### 🔑 Características de JSX

1. **Parece HTML, pero no lo es**
    - Podés escribir etiquetas como `<div>`, `<h1>`, `<button>` directamente en tu código JS.
    - React las convierte en llamadas a `React.createElement()` por debajo.
2. **Interactividad con llaves `{}`**
    - Dentro de JSX podés meter variables o expresiones de JavaScript.
    - Ejemplo:
   ```jsx
        const nombre = "Julio";
        <h1>Hola, {nombre}</h1>
        ```
3. **Debe estar dentro de un único elemento padre**
    - El return de un componente debe devolver un solo nodo raíz.
    - Ejemplo correcto:
   ```jsx
        return (
          <div>
            <h1>Título</h1>
            <p>Texto</p>
          </div>
        );
        ```
4. **Atributos en camelCase**
    - En lugar de `class` (como en HTML), se usa `className`.
    - En lugar de `onclick`, se usa `onClick`.
    - Ejemplo:
   ```jsx
        <button onClick={() => alert("Clic!")}>Click aquí</button>
        ```
5. **Soporta componentes personalizados**
    - Podés crear tu propia etiqueta (componente).
    - Ejemplo:
   ```jsx
        function Boton() {
          return <button>Soy un botón</button>;
        }
        
        <Boton />
        ```

---

### 🔹 Ejemplo completo con JSX

```jsx
function App() {
  const usuario = "Julio";
  const edad = 25;

  return (
    <div>
      <h1>Hola, {usuario}</h1>
      <p>Tenés {edad} años</p>
      <button onClick={() => alert("Bienvenido!")}>
        Saludar
      </button>
    </div>
  );
}
```

---

En resumen: **JSX hace que el código en React sea más fácil de leer y escribir**, porque en vez de armar todo con `React.createElement()`, podés usar una sintaxis similar a HTML.

---

# **JSX se “transpila”**

Cuando te digo que **JSX se “transpila”**, me refiero a que el navegador **no entiende JSX directamente**. Los navegadores solo entienden **JavaScript puro** (ECMAScript).

Entonces, entra en juego un proceso llamado **transpilación**.

---

### 🔹 ¿Qué es transpilar?

**Transpilar = transformar un código de un lenguaje o versión a otro equivalente.**

En React:

- Escribís en **JSX** (que parece HTML dentro de JS).
- Una herramienta como **Babel** convierte ese JSX en **JavaScript válido** que el navegador sí entiende.

---

### 🔹 Ejemplo de transpilación en React

👉 Código con **JSX**:

```jsx
const elemento = <h1>Hola Mundo</h1>;
```

👉 Babel lo **transpila** a JavaScript puro:

```js
const elemento = React.createElement("h1", null, "Hola Mundo");
```

Ambos hacen lo mismo, pero escribir JSX es mucho más cómodo.

---

### 🔹 Diferencia entre **compilar** y **transpilar**

- **Compilar**: transformar código a un lenguaje de **nivel más bajo** (ej: C → ensamblador).
- **Transpilar**: transformar código a otro **lenguaje o versión equivalente** (ej: JSX → JS, TypeScript → JS).

---

### 🔹 ¿Por qué es importante?

- Gracias a la transpilación podés usar **JSX, TypeScript o nuevas features de JS** aunque el navegador no las entienda todavía.
- El build final que se entrega al navegador siempre será **JavaScript estándar**.

---
