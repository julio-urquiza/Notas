# 🧱 MÓDULO 3: Layout con Tailwind CSS

## 🚀 Objetivos

En este módulo vas a aprender:

1. Cómo usar **Flexbox** en Tailwind
2. Cómo crear **layouts con Grid**
3. Cómo hacer **diseños responsive** usando breakpoints (`sm:`, `md:`, `lg:`, etc.)

---

## 🔹 1. Flexbox en Tailwind

Tailwind te da **clases para todo Flexbox** sin escribir CSS.  
Para activar flex:

```html
<div class="flex">
  <div class="bg-blue-300 p-4">A</div>
  <div class="bg-blue-500 p-4">B</div>
  <div class="bg-blue-700 p-4">C</div>
</div>
```

### Clases más importantes:

|Propósito|Clases|Ejemplo|
|---|---|---|
|Dirección|`flex-row`, `flex-col`|`flex-col` → apila elementos|
|Alinear horizontalmente|`justify-start`, `justify-center`, `justify-between`, `justify-end`|`justify-center` centra en el eje X|
|Alinear verticalmente|`items-start`, `items-center`, `items-end`|`items-center` centra en el eje Y|
|Espaciado automático|`gap-x-4`, `gap-y-2`, `gap-4`|separa hijos|

💡 Ejemplo práctico:

```html
<div class="flex justify-between items-center bg-gray-200 p-4">
  <span>🏠 Inicio</span>
  <span>📞 Contacto</span>
  <span>ℹ️ Info</span>
</div>
```

---

## 🔹 2. Grid en Tailwind

El **grid layout** es perfecto para tarjetas, galerías o secciones de igual tamaño.

### Clases principales:

|Clase|Qué hace|
|---|---|
|`grid`|activa grid|
|`grid-cols-3`|3 columnas|
|`gap-4`|espacio entre celdas|
|`col-span-2`|ocupa 2 columnas|

Ejemplo:

```html
<div class="grid grid-cols-3 gap-4 p-4">
  <div class="bg-red-300 p-4">1</div>
  <div class="bg-red-400 p-4">2</div>
  <div class="bg-red-500 p-4">3</div>
</div>
```

### Autoajuste con minmax (responsive sin media queries)

```html
<div class="grid grid-cols-[repeat(auto-fit,minmax(200px,1fr))] gap-4 p-4">
  <div class="bg-green-300 p-4">A</div>
  <div class="bg-green-400 p-4">B</div>
  <div class="bg-green-500 p-4">C</div>
  <div class="bg-green-600 p-4">D</div>
</div>
```

---

## 🔹 3. Diseño Responsive (Breakpoints)

Tailwind usa prefijos para aplicar estilos según el tamaño de pantalla:

|Tamaño|Prefijo|Min-width|
|---|---|---|
|`sm:`|small|640px|
|`md:`|medium|768px|
|`lg:`|large|1024px|
|`xl:`|extra large|1280px|

👉 Ejemplo:

```html
<div class="bg-blue-300 md:bg-green-300 lg:bg-red-300 p-4">
  Cambia de color según el tamaño de pantalla
</div>
```

👉 Ejemplo responsive con grid:

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 p-4">
  <div class="bg-purple-300 p-4">1</div>
  <div class="bg-purple-400 p-4">2</div>
  <div class="bg-purple-500 p-4">3</div>
</div>
```

✅ 1 columna en móvil  
✅ 2 columnas en tablets  
✅ 3 columnas en desktop

---

## 🧩 Ejercicio práctico del módulo

Creá este layout:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Layout Tailwind</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 min-h-screen">

  <!-- Navbar -->
  <nav class="bg-blue-600 text-white flex justify-between items-center p-4">
    <h1 class="text-xl font-bold">Mi Sitio</h1>
    <div class="space-x-4">
      <a href="#" class="hover:underline">Inicio</a>
      <a href="#" class="hover:underline">Servicios</a>
      <a href="#" class="hover:underline">Contacto</a>
    </div>
  </nav>

  <!-- Contenido principal -->
  <main class="grid grid-cols-1 md:grid-cols-3 gap-4 p-6">
    <section class="bg-white p-4 shadow rounded-lg md:col-span-2">
      <h2 class="text-2xl font-bold mb-2">Artículo principal</h2>
      <p class="text-gray-600">
        Este bloque ocupa 2 columnas en pantallas medianas o mayores.
      </p>
    </section>
    <aside class="bg-white p-4 shadow rounded-lg">
      <h3 class="text-xl font-semibold mb-2">Sidebar</h3>
      <p class="text-gray-600">Aquí van enlaces o anuncios.</p>
    </aside>
  </main>

</body>
</html>
```

👉 Vas a practicar:

- `flex` en la navbar
- `grid` en el contenido
- `responsive` con `md:`
- sombras y bordes redondeados

---
