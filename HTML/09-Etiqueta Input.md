La etiqueta `<input>` en HTML se usa para **capturar datos del usuario** dentro de un formulario. Es un **elemento vacío (void)**, por lo que no tiene etiqueta de cierre.

---

# 1️⃣ Sintaxis básica

```html
<input type="text">
```

Generalmente se usa dentro de `<form>`:

```html
<form>
  <input type="text" name="usuario">
</form>
```

---

# 2️⃣ Atributo más importante: `type`

El comportamiento del `<input>` depende del valor de `type`.

## 🔹 `type="text"`

Campo de texto simple.

```html
<input type="text" name="nombre">
```

---

## 🔹 `type="password"`

Oculta los caracteres ingresados.

```html
<input type="password" name="clave">
```

---

## 🔹 `type="email"`

Valida formato de correo automáticamente.

```html
<input type="email" name="correo">
```

---

## 🔹 `type="number"`

Permite solo valores numéricos.

```html
<input type="number" name="edad" min="0" max="120">
```

---

## 🔹 `type="date"`

Selector de fecha.

```html
<input type="date" name="fecha">
```

---

## 🔹 `type="checkbox"`

Selección múltiple.

```html
<input type="checkbox" name="acepto">
```

---

## 🔹 `type="radio"`

Selección única dentro del mismo `name`.

```html
<input type="radio" name="genero" value="m">
<input type="radio" name="genero" value="f">
```

---

## 🔹 `type="file"`

Subida de archivos.

```html
<input type="file" name="documento">
```

---

## 🔹 `type="submit"`

Envía el formulario.

```html
<input type="submit" value="Enviar">
```

---

# 3️⃣ Atributos fundamentales

## 🔹 `name`

Clave con la que se enviará el dato al servidor.

```html
<input type="text" name="usuario">
```

---

## 🔹 `value`

Valor inicial o valor enviado.

```html
<input type="text" value="Julio">
```

---

## 🔹 `placeholder`

Texto guía dentro del campo.

```html
<input type="text" placeholder="Ingrese su nombre">
```

---

## 🔹 `required`

Campo obligatorio.

```html
<input type="email" required>
```

---

## 🔹 `readonly`

No editable.

```html
<input type="text" value="ID123" readonly>
```

---

## 🔹 `disabled`

Deshabilitado (no se envía).

```html
<input type="text" disabled>
```

---

# 4️⃣ Relación con `<label>`

Siempre es buena práctica asociarlo a una etiqueta `<label>` para accesibilidad:

```html
<label for="usuario">Usuario</label>
<input type="text" id="usuario" name="usuario">
```

También puede envolverse:

```html
<label>
  Usuario
  <input type="text" name="usuario">
</label>
```

---

# 5️⃣ Validación nativa del navegador

HTML5 permite validaciones sin JavaScript:

```html
<input 
  type="text" 
  pattern="[A-Za-z]{3,}" 
  title="Mínimo 3 letras">
```

---

# 6️⃣ Diferencia con `<textarea>`

`<input>` es para una sola línea.  
Si necesitás múltiples líneas:

```html
<textarea name="mensaje"></textarea>
```

---

# 7️⃣ Resumen técnico

- Elemento vacío
- Depende del atributo `type`
- Puede validarse sin JS
- Se usa dentro de `<form>`
- Se identifica por `name`
- Mejora accesibilidad con `<label>`

---
