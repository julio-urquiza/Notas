En HTML, un **formulario** se define con la etiqueta `<form>` y se utiliza para **recopilar datos del usuario** y enviarlos a un servidor para su procesamiento.

Es un elemento fundamental en aplicaciones web: login, registro, búsquedas, carga de datos, etc.

---

## 1️⃣ Estructura básica de un formulario

```html
<form action="/procesar" method="POST">
  <label for="nombre">Nombre:</label>
  <input type="text" id="nombre" name="nombre">

  <button type="submit">Enviar</button>
</form>
```

---

## 2️⃣ Atributos principales de `<form>`

### 🔹 `action`

Indica **a dónde se envían los datos** (URL del servidor).

```html
<form action="/login">
```

Puede ser:

- Ruta relativa → `/procesar`
- Ruta absoluta → `https://midominio.com/procesar`

---

### 🔹 `method`

Define el método HTTP:

- `GET` → Envía los datos por la URL
    - Visible en la barra del navegador
    - Se usa para búsquedas o consultas
- `POST` → Envía los datos en el cuerpo de la petición
    - No visible en la URL
    - Se usa para datos sensibles o creación/modificación

```html
<form method="POST">
```

---

### 🔹 `enctype`

Define el tipo de codificación de datos (importante para subir archivos).

- `application/x-www-form-urlencoded` (por defecto)
- `multipart/form-data` → obligatorio para `<input type="file">`
- `text/plain`

Ejemplo para subir archivos:

```html
<form method="POST" enctype="multipart/form-data">
```

---

## 3️⃣ Elementos más usados dentro de un formulario

### 🔹 `<input>`

Es el campo más versátil.

Tipos comunes:

```html
<input type="text">
<input type="email">
<input type="password">
<input type="number">
<input type="checkbox">
<input type="radio">
<input type="file">
<input type="date">
```

---

### 🔹 `<label>`

Asocia texto descriptivo a un input (mejora accesibilidad).

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

El `for` debe coincidir con el `id`.

---

### 🔹 `<textarea>`

Para textos largos.

```html
<textarea name="mensaje" rows="4" cols="50"></textarea>
```

---

### 🔹 `<select>` y `<option>`

Lista desplegable.

```html
<select name="pais">
  <option value="ar">Argentina</option>
  <option value="cl">Chile</option>
</select>
```

---

### 🔹 `<button>`

```html
<button type="submit">Enviar</button>
<button type="reset">Resetear</button>
<button type="button">Botón normal</button>
```

Tipos:

- `submit` → envía el formulario
- `reset` → limpia los campos
- `button` → no hace nada por defecto (se usa con JS)

---

## 4️⃣ El atributo más importante: `name`

Sin `name`, el input **no se envía al servidor**.

Ejemplo:

```html
<input type="text" name="usuario">
```

Cuando se envía con `POST`, el servidor recibe algo como:

```
usuario=Julio
```

---

## 5️⃣ Validaciones HTML nativas

HTML5 permite validaciones sin JavaScript:

```html
<input type="email" required>
<input type="text" minlength="3" maxlength="10">
<input type="number" min="1" max="10">
```

Atributos útiles:

- `required`
- `pattern`
- `min`
- `max`
- `minlength`
- `maxlength`

---

## 6️⃣ Ejemplo completo profesional

```html
<form action="/registro" method="POST">

  <div>
    <label for="nombre">Nombre</label>
    <input type="text" id="nombre" name="nombre" required>
  </div>

  <div>
    <label for="email">Email</label>
    <input type="email" id="email" name="email" required>
  </div>

  <div>
    <label for="password">Contraseña</label>
    <input type="password" id="password" name="password" minlength="6" required>
  </div>

  <div>
    <button type="submit">Crear cuenta</button>
  </div>

</form>
```

---

## 7️⃣ Flujo real en una aplicación

1. Usuario completa formulario
2. Navegador genera petición HTTP
3. Servidor recibe los datos
4. Backend valida
5. Devuelve respuesta (redirect, JSON, error, etc.)

---

## 8️⃣ Concepto clave

Un formulario en HTML:

- No procesa datos
- Solo los envía
- El procesamiento ocurre en el servidor o con JavaScript

---
