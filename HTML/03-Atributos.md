En HTML casi todas las etiquetas aceptan **atributos**, que sirven para **dar información extra o modificar su comportamiento**.

No hace falta memorizar los más raros; con los **principales atributos** vas a poder trabajar en el 90% de los casos:

---

## 📌 Atributos globales (se pueden usar en casi cualquier etiqueta)

- **`id`** → Identificador único.
```html
    <p id="intro">Hola</p>
```
- **`class`** → Permite agrupar elementos para CSS o JS.
```html
    <div class="card"></div>
```
- **`style`** → CSS en línea (no muy recomendable).
```html
    <h1 style="color:red;">Título</h1>
```
  
- **`title`** → Texto emergente (tooltip).
```html
    <abbr title="HyperText Markup Language">HTML</abbr>
```

- **`hidden`** → Oculta un elemento.
- **`tabindex`** → Orden de tabulación.
- **`contenteditable`** → Hace el contenido editable.

---

## 📌 Atributos comunes para enlaces e imágenes

- **`href`** (en `<a>`) → URL de destino.
```html
    <a href="https://google.com">Ir a Google</a>
```

- **`src`** (en `<img>`, `<script>`, `<iframe>`, etc.) → Ruta del recurso.
```html
    <img src="foto.jpg" alt="Foto de perfil">
```

- **`alt`** (en `<img>`) → Texto alternativo (accesibilidad).
- **`target`** (en `<a>`) → Dónde abrir el enlace (`_blank`, `_self`, etc.).
- **`rel`** (en `<a>`, `<link>`) → Relación con el destino (ej: `nofollow`, `stylesheet`).

---

## 📌 Atributos comunes para formularios

- **`type`** (en `<input>`) → Tipo de campo (`text`, `password`, `email`, `number`, etc.).
- **`name`** → Nombre del campo (clave que viaja en el form).
- **`value`** → Valor inicial.
- **`placeholder`** → Texto de ayuda dentro del campo.
- **`required`** → Campo obligatorio.
- **`checked`** (para checkbox/radio).
- **`selected`** (para option).
- **`disabled`** → Deshabilitado.
- **`readonly`** → Solo lectura.
- **`maxlength`** / **`minlength`** → Longitud del texto.
- **`min`** / **`max`** → Rango numérico o fecha.

---

## 📌 Atributos multimedia

- **`controls`** (en `<audio>`, `<video>`) → Muestra los controles.
- **`autoplay`** → Reproduce automáticamente.
- **`loop`** → Repite el contenido.
- **`muted`** → Comienza sin sonido.
- **`width`** / **`height`** → Dimensiones.

---

## 📌 Atributos para tablas

- **`colspan`** → Combina columnas.
- **`rowspan`** → Combina filas.

---

## 📌 Atributos de accesibilidad (muy importantes ⚡)

- **`aria-*`** → Mejoran accesibilidad para lectores de pantalla.
- **`role`** → Define el rol semántico de un elemento.

---

👉 Resumen:  
Si te tuviera que dar un **kit básico** de atributos imprescindibles serían:

- `id`, `class`, `style`
- `href`, `src`, `alt`, `target`
- `type`, `name`, `value`, `placeholder`, `required`
- `width`, `height`
- `title`

---
