La etiqueta `<img>` en **HTML** se utiliza para **incrustar imágenes** dentro de un documento. Es un elemento fundamental para contenido visual y pertenece a los **elementos vacíos (void elements)**, es decir, **no tiene etiqueta de cierre**.

---

## 1️⃣ Sintaxis básica

```html
<img src="ruta-de-la-imagen.jpg" alt="Descripción de la imagen">
```

---

## 2️⃣ Atributos principales

### 🔹 `src` (source) — obligatorio

Especifica la **ruta o URL** de la imagen.

```html
<img src="imagen.jpg">
<img src="/assets/img/logo.png">
<img src="https://dominio.com/foto.webp">
```

Puede ser:

- Ruta relativa
- Ruta absoluta
- URL externa

---

### 🔹 `alt` (alternative text) — obligatorio por accesibilidad

Proporciona un **texto alternativo** que se muestra si la imagen no carga y es utilizado por lectores de pantalla.

```html
<img src="perfil.jpg" alt="Foto de perfil de usuario">
```

Buenas prácticas:

- Describir el contenido
- No usar frases como "imagen de..."
- Si es decorativa: `alt=""`

---

## 3️⃣ Atributos comunes adicionales

### 🔹 `width` y `height`

Definen dimensiones en píxeles (sin unidad).

```html
<img src="foto.jpg" alt="Paisaje" width="300" height="200">
```

⚠️ Se recomienda definirlos para evitar **layout shift**.

---

### 🔹 `title`

Muestra un tooltip al pasar el mouse.

```html
<img src="icono.png" alt="Configuración" title="Abrir configuración">
```

---

### 🔹 `loading`

Optimiza la carga.

```html
<img src="foto.jpg" alt="Paisaje" loading="lazy">
```

Valores:

- `lazy` → carga diferida
- `eager` → carga inmediata

---

## 4️⃣ Buenas prácticas modernas

### ✅ Usar formatos optimizados

- WebP
- AVIF

### ✅ Controlar con CSS

En lugar de usar width/height en HTML:

```css
img {
  max-width: 100%;
  height: auto;
}
```

---

## 5️⃣ Imágenes responsivas

### 🔹 `srcset`

Permite múltiples versiones según resolución.

```html
<img 
  src="imagen-800.jpg"
  srcset="imagen-400.jpg 400w, imagen-800.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
  alt="Ejemplo responsivo">
```

El navegador elige la mejor opción según el viewport.

---

## 6️⃣ Relación con `<figure>` y `<figcaption>`

Para imágenes con descripción:

```html
<figure>
  <img src="grafico.png" alt="Gráfico de ventas 2025">
  <figcaption>Ventas del primer trimestre</figcaption>
</figure>
```

---

## 7️⃣ Errores comunes

❌ Olvidar `alt`  
❌ Usar imágenes demasiado pesadas  
❌ No definir dimensiones  
❌ Usar imágenes solo para texto (afecta SEO y accesibilidad)

---

## Resumen técnico

- Elemento vacío
- Requiere `src`
- Debe incluir `alt`
- Soporta carga diferida
- Permite comportamiento responsivo

---