Perfecto 🔥  
Vamos con el **Módulo 2: Fundamentos de Tailwind CSS**, donde vas a aprender las clases base que se usan TODO el tiempo.

---

# 🎨 Módulo 2: Fundamentos

En este módulo vas a aprender:

1. Colores
2. Espaciado (margin y padding)
3. Tipografía
4. Bordes y sombras
5. Mini ejercicios prácticos

---

## 🟢 1. Colores

Tailwind usa una **escala de colores del 50 al 900**.  
Cuanto mayor el número → más oscuro el color.

Ejemplo:

```html
<div class="bg-blue-500 text-white p-4">Fondo azul medio</div>
<div class="bg-blue-200 text-blue-800 p-4">Fondo azul claro</div>
```

Algunos colores disponibles:

- `gray`, `red`, `blue`, `green`, `yellow`, `purple`, `pink`, `indigo`, `emerald`, `teal`, etc.


💡 También podés usar:

```html
text-red-500   → color del texto  
bg-red-500     → color de fondo  
border-red-500 → color del borde
```

---

## 🧭 2. Espaciado (margin y padding)

Tailwind tiene un sistema de espaciado en múltiplos de 4 px (por defecto):

|Clase|Descripción|
|---|---|
|`m-4`|margin 1 rem (16px)|
|`mt-2`|margin-top 8px|
|`mx-6`|margin horizontal 24px|
|`p-4`|padding 16px|
|`py-2`|padding vertical 8px|

💡 Ejemplo:

```html
<div class="bg-yellow-300 p-4 m-4 rounded">
  Caja con padding y margin
</div>
```

---

## ✍️ 3. Tipografía

Clases más usadas:

- **Tamaño:** `text-sm`, `text-base`, `text-lg`, `text-xl`, `text-2xl`, `text-4xl`, etc.
- **Peso:** `font-light`, `font-normal`, `font-semibold`, `font-bold`.
- **Alineación:** `text-left`, `text-center`, `text-right`.
- **Color:** `text-gray-700`, `text-blue-600`.
- **Decoración:** `underline`, `line-through`, `uppercase`, `tracking-wide`.


Ejemplo:

```html
<h1 class="text-3xl font-bold text-blue-600 mb-2">Título principal</h1>
<p class="text-gray-600 leading-relaxed">
  Tailwind te permite dar estilo al texto sin escribir CSS.
</p>
```

---

## 🟣 4. Bordes y sombras

Clases útiles:

- **Bordes:** `border`, `border-2`, `border-gray-300`.
- **Radio:** `rounded`, `rounded-lg`, `rounded-full`.
- **Sombras:** `shadow`, `shadow-md`, `shadow-lg`, `shadow-xl`.


Ejemplo:

```html
<div class="border border-gray-300 rounded-lg shadow-md p-4">
  Caja con borde y sombra
</div>
```

---

## 💪 5. Ejercicio práctico

Probá esto con el **CDN** (no necesitás Node todavía):

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Tarjeta Tailwind</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 flex items-center justify-center h-screen">

  <div class="bg-white shadow-lg rounded-xl p-6 w-80 text-center">
    <img src="https://placekitten.com/200/200" class="rounded-full mx-auto mb-4" alt="gatito">
    <h2 class="text-xl font-bold text-gray-800 mb-1">Luna</h2>
    <p class="text-gray-500 mb-3">Gatita curiosa y dormilona 🐱</p>
    <button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition">
      Adoptar
    </button>
  </div>

</body>
</html>
```

🔍 Lo que aplicaste:

- Colores (`bg-gray-100`, `text-gray-500`, `bg-blue-500`)
- Espaciado (`p-6`, `mb-4`)
- Tipografía (`text-xl`, `font-bold`)
- Bordes y sombras (`rounded-xl`, `shadow-lg`)
- Hover y transición (`hover:bg-blue-600`, `transition`)


---
