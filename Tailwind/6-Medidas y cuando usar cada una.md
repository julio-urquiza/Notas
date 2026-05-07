## 🧭 1. Regla general

**Usá unidades relativas (%, rem, vw, vh, fr)** siempre que puedas.  
**Usá unidades fijas (px)** solo cuando realmente necesites un tamaño exacto.

---

## ⚙️ 2. Tipos de medidas y cuándo usarlas

### 🔹 `px` (píxeles)

- ✅ Precisión total: íconos, bordes, sombras, líneas.
- ❌ No escala bien en pantallas pequeñas o grandes.

👉 **Usalo para:** bordes, íconos, sombras o ajustes finos.  
**Ejemplo:**

```css
.icono { width: 24px; height: 24px; }
```

---

### 🔹 `%` (porcentaje)

- Se adapta al **contenedor padre**.
- Ideal para hacer layouts flexibles.

👉 **Usalo para:** anchos o alturas relativas a su contenedor.  
**Ejemplo:**

```css
img { width: 100%; } /* ocupa todo el ancho del div padre */
```

---

### 🔹 `vw` y `vh` (viewport width/height)

- 1vw = 1% del ancho de la ventana.
- 1vh = 1% del alto de la ventana.

👉 **Usalo para:** secciones completas o diseños de pantalla completa.  
**Ejemplo:**

```css
.hero { height: 100vh; } /* ocupa toda la pantalla */
```

---

### 🔹 `rem` y `em`

- `1rem` = tamaño de fuente raíz (`html`).
- `1em` = tamaño relativo al elemento padre.

👉 **Usalo para:** texto, paddings, márgenes y espaciado.  
**Ejemplo:**

```css
h1 { font-size: 2rem; } /* 2 veces el tamaño base */
```

Tailwind lo simplifica:

```html
<h1 class="text-2xl">Título</h1>
```

---

### 🔹 `fr` (solo en Grid)

- Representa una **fracción del espacio disponible**.  
    👉 Perfecto para dividir un grid en proporciones flexibles.


**Ejemplo:**

```css
.grid {
  display: grid;
  grid-template-columns: 1fr 2fr; /* columna 2 ocupa el doble */
}
```

---

## 🧱 3. Medidas recomendadas por tipo de elemento

|Elemento|Medida recomendada|Ejemplo|
|---|---|---|
|**Navbar/Footer**|`width: 100%` o `100vw`, altura fija en `px` o `rem`|`h-16` en Tailwind|
|**Hero / portada**|`height: 100vh`|`min-h-screen` en Tailwind|
|**Contenedores principales**|`max-width` en `px` o `rem` + `width: 100%`|`max-w-7xl mx-auto`|
|**Texto**|`rem` o clases de Tailwind (`text-base`, `text-lg`)||
|**Cards**|`width` en `%` o `max-w` + padding en `rem`|`max-w-sm p-4`|
|**Imagenes**|`width: 100%` y `height: auto`||

---

## 💡 4. En Tailwind, esto se simplifica mucho:

Algunos ejemplos prácticos:

```html
<!-- Sección completa -->
<section class="min-h-screen flex items-center justify-center bg-gray-100">

<!-- Contenedor centrado y con ancho máximo -->
<div class="max-w-5xl w-full mx-auto p-6">

<!-- Card adaptable -->
<div class="w-full sm:w-1/2 lg:w-1/3 p-4">
  <div class="bg-white p-6 rounded-2xl shadow">
    <h2 class="text-xl font-semibold mb-2">Título</h2>
  </div>
</div>
```

---

## 🧩 5. Regla de oro

> **“Diseñá en proporciones, no en píxeles.”**  
> Usá unidades relativas (`%`, `vh`, `rem`, `fr`) para que el diseño **fluya** y se adapte a pantallas chicas o grandes sin romperse.

---
