## 🔹 ¿Qué son las props?

- Son **inmutables** → el componente que las recibe no puede cambiarlas.
    
- Se pasan como **atributos en JSX**.
    
- Permiten que un mismo componente sea **reutilizable** con diferentes datos.
    

---

## 🔹 Ejemplo básico

```jsx
function Saludo(props) {
  return <h1>Hola, {props.nombre}!</h1>;
}

// Uso del componente
<Saludo nombre="Julio" />
<Saludo nombre="Ana" />
```

👉 El mismo componente `Saludo` muestra cosas distintas según la **prop `nombre`**.

---

## 🔹 Props con destructuring

Para escribir más limpio, podés “desestructurar” las props:

```jsx
function Saludo({ nombre, edad }) {
  return <p>Hola, soy {nombre} y tengo {edad} años.</p>;
}

// Uso
<Saludo nombre="Julio" edad={25} />
```

---

## 🔹 Props dinámicas

Las props pueden ser **valores, variables, funciones, arrays u objetos**:

```jsx
function Boton({ texto, onClick }) {
  return <button onClick={onClick}>{texto}</button>;
}

// Uso
<Boton texto="Enviar" onClick={() => alert("Enviado!")} />
```

---

## 🔹 `children` (prop especial)

`children` permite pasar contenido **dentro** de un componente.

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}

// Uso
<Card>
  <h2>Título</h2>
  <p>Este es el contenido de la card.</p>
</Card>
```

---

## 🔹 Default props (valores por defecto)

Podés asignar valores por defecto a las props.

```jsx
function Saludo({ nombre = "Invitado" }) {
  return <h1>Hola, {nombre}!</h1>;
}

// Uso
<Saludo />           // Hola, Invitado!
<Saludo nombre="Ana" />  // Hola, Ana!
```

---

## 🔹 Validación de props (opcional)

Con **PropTypes** podés definir qué tipo de dato debería recibir cada prop.

```jsx
import PropTypes from "prop-types";

function Perfil({ nombre, edad }) {
  return <p>{nombre} tiene {edad} años.</p>;
}

Perfil.propTypes = {
  nombre: PropTypes.string.isRequired,
  edad: PropTypes.number
};
```

---

✅ En resumen:

- **Props** = datos que se le pasan al componente.
- Son **inmutables** (el hijo no las cambia).
- Pueden ser valores simples, objetos, funciones o incluso otros componentes.
- `children` permite meter contenido dentro.
- Podés definir **valores por defecto** y **validaciones**.

---
