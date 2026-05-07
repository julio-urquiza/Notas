## 🎯 Objetivo del módulo

- Entender cómo funcionan los **inputs controlados**
- Crear formularios con múltiples campos
- Validar los datos (de forma manual y automática)
- Usar `react-hook-form` y `Yup` para validaciones más avanzadas

---

## 🧩 1. Inputs controlados

Un **input controlado** es aquel cuyo valor **viene del estado**.  
El input no “guarda” su valor internamente: React lo controla por medio de `useState`.

```jsx
import { useState } from "react";

function FormularioSimple() {
  const [nombre, setNombre] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("Nombre:", nombre);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        placeholder="Tu nombre"
        value={nombre}
        onChange={(e) => setNombre(e.target.value)}
      />
      <button type="submit">Enviar</button>
    </form>
  );
}

export default FormularioSimple;
```

🧠 El `value` del input viene del estado (`nombre`), y `onChange` actualiza ese estado.  
Eso permite a React **saber exactamente qué hay escrito** en cada campo.

---

## 🧱 2. Formularios con múltiples campos

Podés manejar varios campos en un solo objeto de estado:

```jsx
function FormularioMultiple() {
  const [form, setForm] = useState({ nombre: "", email: "" });

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(form);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input name="nombre" placeholder="Nombre" onChange={handleChange} />
      <input name="email" placeholder="Email" onChange={handleChange} />
      <button>Enviar</button>
    </form>
  );
}
```

👉 Notá cómo usamos `[e.target.name]` para actualizar el campo correcto del objeto.

---

## ✅ 3. Validaciones manuales

Podés validar dentro del `handleSubmit`:

```jsx
const handleSubmit = (e) => {
  e.preventDefault();
  if (!form.nombre || !form.email.includes("@")) {
    alert("Por favor, completá todos los campos correctamente");
    return;
  }
  console.log("Formulario válido:", form);
};
```

---

## ⚡ 4. `react-hook-form`: validaciones profesionales

Ahora vamos con la forma moderna y optimizada 💪

Primero instalá las dependencias:

```bash
npm install react-hook-form
```

Luego en tu componente:

```jsx
import { useForm } from "react-hook-form";

function FormReactHook() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm();

  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input
        {...register("nombre", { required: "El nombre es obligatorio" })}
        placeholder="Nombre"
      />
      {errors.nombre && <p>{errors.nombre.message}</p>}

      <input
        {...register("email", {
          required: "El email es obligatorio",
          pattern: { value: /\S+@\S+\.\S+/, message: "Email inválido" },
        })}
        placeholder="Email"
      />
      {errors.email && <p>{errors.email.message}</p>}

      <button>Enviar</button>
    </form>
  );
}
```

✅ `react-hook-form`:

- No requiere `useState` para cada input
- Valida automáticamente
- Optimiza el rendimiento
- Devuelve los errores en `errors`

---

## 🧮 5. Validaciones con `Yup` (esquemas)

Para validaciones más avanzadas:

```bash
npm install @hookform/resolvers yup
```

Luego:

```jsx
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as yup from "yup";

const schema = yup.object({
  nombre: yup.string().required("El nombre es obligatorio"),
  email: yup.string().email("Email inválido").required("El email es obligatorio"),
}).required();

function FormYup() {
  const { register, handleSubmit, formState: { errors } } = useForm({
    resolver: yupResolver(schema),
  });

  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("nombre")} placeholder="Nombre" />
      <p>{errors.nombre?.message}</p>

      <input {...register("email")} placeholder="Email" />
      <p>{errors.email?.message}</p>

      <button>Enviar</button>
    </form>
  );
}
```

🧠 `Yup` te deja definir reglas declarativas, muy útiles en formularios grandes.

---

## 💪 Ejercicio propuesto

1. Crea un formulario con campos: `nombre`, `email`, `edad`
2. Usá `react-hook-form` con `Yup` para validar:
    - `nombre`: requerido
    - `email`: formato válido
    - `edad`: número entre 18 y 99
3. Mostrá mensajes de error debajo de cada input
4. Al enviar, mostrale al usuario los datos validados en pantalla

---

## 🧾 Resumen

|Concepto|Descripción|Hook / Librería|
|---|---|---|
|Input controlado|Valor manejado por estado|`useState`|
|Formularios grandes|Agrupados en un objeto|`useState`|
|Validaciones automáticas|Declarativas y escalables|`react-hook-form`, `Yup`|

---

```jsx
{errors.nombre && <p>{errors.nombre.message}</p>}
```

es una forma **condicional** de mostrar un mensaje de error en React.  
Vamos a desglosarla paso a paso 👇

---

### 🔹 1. `errors`

En este caso, `errors` viene del **React Hook Form** (de la función `useForm()`), y contiene los errores de validación de los campos del formulario.

Por ejemplo:

```js
errors = {
  nombre: {
    type: "required",
    message: "El nombre es obligatorio"
  }
}
```

---

### 🔹 2. `errors.nombre`

Esto comprueba si existe un error para el campo **nombre**.  
Si **no hay error**, `errors.nombre` será `undefined`.  
Si **hay error**, tendrá un objeto con información del error.

---

### 🔹 3. `&&`

El operador lógico **AND (`&&`)** se usa aquí para **renderizar condicionalmente**.

En React:

```jsx
condición && <Componente />
```

significa que si `condición` es verdadera (no es `undefined`, `null`, `false`, `0` o `""`), entonces se renderiza el `<Componente />`.

---

### 🔹 4. `<p>{errors.nombre.message}</p>`

Si existe un error, muestra un párrafo con el mensaje del error.  
Por ejemplo:

```html
<p>El nombre es obligatorio</p>
```

---

### 🔹 🔁 Todo junto:

```jsx
{errors.nombre && <p>{errors.nombre.message}</p>}
```

significa:

> “Si hay un error en el campo `nombre`, mostrar el mensaje del error en un `<p>`; si no, no mostrar nada.”

---

### 💡 Ejemplo completo:

```jsx
<form onSubmit={handleSubmit(onSubmit)}>
  <input {...register("nombre", { required: "El nombre es obligatorio" })} />
  {errors.nombre && <p>{errors.nombre.message}</p>}
  <button type="submit">Enviar</button>
</form>
```

Si el usuario deja el campo vacío y presiona “Enviar”, se mostrará:

```
El nombre es obligatorio
```

---

```jsx
{...register("nombre", { required: "El nombre es obligatorio" })}
```

es **una de las más importantes** cuando usás **React Hook Form**.  
Vamos a explicarla paso a paso 👇

---

### 🔹 1. `register()`

`register` es una **función** que te da el hook `useForm()` de la librería `react-hook-form`.

Su propósito es **conectar un input** al sistema de formularios — es decir, para que React Hook Form pueda:

- Leer su valor,
- Validarlo,
- Detectar cambios,
- Y mostrar errores si los hay.

---

### 🔹 2. Primer parámetro: `"nombre"`

Es el **nombre del campo**.  
Así es como React Hook Form identifica cada input internamente.

Por ejemplo:

```jsx
register("nombre")
register("email")
register("password")
```

Cada uno crea una “entrada” diferente dentro del formulario.

---

### 🔹 3. Segundo parámetro: `{ required: "El nombre es obligatorio" }`

Este es un **objeto de validación**.  
Aquí le decís qué reglas debe cumplir el campo.

En este caso:

- `required` significa que el campo es obligatorio.
- El texto `"El nombre es obligatorio"` es el **mensaje de error** que se mostrará si el usuario no lo completa.

También podrías poner otras validaciones, por ejemplo:

```js
register("email", { 
  required: "El email es obligatorio", 
  pattern: { value: /^\S+@\S+$/, message: "El email no es válido" }
})
```

---

### 🔹 4. Los tres puntos `...` (spread operator)

El **spread operator (`...`)** sirve para **inyectar** las propiedades que devuelve `register()` dentro del `<input>`.

La función `register()` devuelve algo así:

```js
{
  onChange: ƒ,
  onBlur: ƒ,
  name: "nombre",
  ref: ƒ
}
```

Entonces, al poner:

```jsx
<input {...register("nombre", { required: "El nombre es obligatorio" })} />
```

es equivalente a:

```jsx
<input
  name="nombre"
  onChange={...}
  onBlur={...}
  ref={...}
/>
```

De esta forma el input queda **conectado al formulario** y React Hook Form puede controlarlo sin que vos tengas que escribir toda la lógica manualmente.

---

### 💡 En resumen:

🔸 `register()` → conecta el input con React Hook Form  
🔸 `"nombre"` → identifica el campo  
🔸 `{ required: "El nombre es obligatorio" }` → regla de validación  
🔸 `...` → inserta automáticamente las props necesarias en el `<input>`

---

```js
formState: { errors }
```

---

## 🧩 1. El contexto

Esta línea aparece dentro de una **desestructuración** del objeto que devuelve el hook `useForm()`:

```js
const { register, handleSubmit, formState: { errors } } = useForm();
```

`useForm()` devuelve un objeto grande con muchas propiedades, entre ellas una llamada `formState`.

---

## 🧠 2. ¿Qué es `formState`?

`formState` es **un objeto interno de React Hook Form** que guarda todo el **estado actual del formulario**.

Por ejemplo:

```js
formState = {
  errors: { ... },          // errores de validación
  isDirty: false,           // si se cambió algún campo
  isValid: true,            // si el formulario está válido
  isSubmitting: false,      // si se está enviando
  touchedFields: { ... },   // campos que fueron tocados
}
```

---

## 🎯 3. ¿Qué hace `formState: { errors }`?

Esta parte:

```js
formState: { errors }
```

es **una desestructuración anidada**.

👉 Significa:  
“Del objeto `formState`, extraé solo la propiedad `errors` y guardala en una variable llamada `errors`”.

Es lo mismo que hacer:

```js
const formulario = useForm();
const errors = formulario.formState.errors;
```

Pero de forma más compacta.

---

## ⚙️ 4. ¿Qué contiene `errors`?

`errors` es un **objeto** que guarda los errores actuales de validación, uno por cada campo con problema.

Por ejemplo, si el usuario no completó el nombre:

```js
errors = {
  nombre: {
    type: "required",
    message: "El nombre es obligatorio"
  }
}
```

Entonces podés mostrar el error así:

```jsx
{errors.nombre && <p>{errors.nombre.message}</p>}
```

---

## 💡 En resumen

|Elemento|Qué representa|
|---|---|
|`formState`|Estado completo del formulario|
|`formState.errors`|Todos los errores actuales|
|`formState: { errors }`|Desestructura solo la parte de errores para usarla fácilmente|

---

💬 **En otras palabras:**

> `formState: { errors }` es solo una forma de decirle a React Hook Form:  
> “De todo el estado del formulario, solo necesito los errores”.

---