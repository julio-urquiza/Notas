# 🧩 MÓDULO 4: Componentes prácticos

👉 Objetivo: aprender a combinar las clases de Tailwind para crear componentes **listos para usar**.

---

## 🔹 1. Botones

Los botones son un clásico para empezar, y con Tailwind podés hacerlos muy rápido.

### Ejemplo básico:

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded">
  Botón simple
</button>
```

### Con efectos hover y transición:

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition">
  Botón interactivo
</button>
```

💡 `hover:` aplica el estilo al pasar el mouse.  
💡 `transition` hace que el cambio sea suave.

---

### Variantes rápidas:

```html
<button class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-600">Aceptar</button>
<button class="bg-gray-300 text-gray-800 px-4 py-2 rounded hover:bg-gray-400">Cancelar</button>
<button class="border border-blue-500 text-blue-500 px-4 py-2 rounded hover:bg-blue-500 hover:text-white">Ver más</button>
```

---

## 🔹 2. Tarjetas (Cards)

Una **card** combina imagen, texto y botón.

```html
<div class="bg-white shadow-lg rounded-lg p-6 w-80 text-center">
  <img src="https://placekitten.com/200/200" alt="gatito" class="rounded-full mx-auto mb-4">
  <h2 class="text-xl font-bold text-gray-800 mb-2">Luna</h2>
  <p class="text-gray-600 mb-4">Gatita curiosa y dormilona 🐱</p>
  <button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition">Adoptar</button>
</div>
```

🔸 Usás:

- `shadow-lg` → sombra elegante
    
- `rounded-lg` → esquinas suaves
    
- `text-center`, `mb-4` → alineación y espaciado
    
- `hover:bg-*` → efecto interactivo
    

---

## 🔹 3. Formularios

Tailwind también hace que los formularios se vean limpios sin CSS adicional.

```html
<form class="bg-white p-6 rounded-lg shadow-md w-80">
  <h2 class="text-xl font-bold text-gray-800 mb-4">Iniciar sesión</h2>

  <input type="email" placeholder="Email"
         class="w-full border border-gray-300 rounded px-3 py-2 mb-3 focus:outline-none focus:ring-2 focus:ring-blue-400">

  <input type="password" placeholder="Contraseña"
         class="w-full border border-gray-300 rounded px-3 py-2 mb-4 focus:outline-none focus:ring-2 focus:ring-blue-400">

  <button class="bg-blue-500 text-white w-full py-2 rounded hover:bg-blue-600 transition">
    Entrar
  </button>
</form>
```

💡 `focus:ring-2 focus:ring-blue-400` → resalta el input al hacer clic.  
💡 `w-full` → el campo ocupa todo el ancho.

---

## 🔹 4. Navbar Responsive

Una navbar sencilla que se adapta a pantallas pequeñas:

```html
<nav class="bg-gray-800 text-white px-6 py-4 flex flex-wrap justify-between items-center">
  <h1 class="text-xl font-bold">Mi Sitio</h1>
  <ul class="flex space-x-4 text-sm">
    <li><a href="#" class="hover:text-blue-400">Inicio</a></li>
    <li><a href="#" class="hover:text-blue-400">Servicios</a></li>
    <li><a href="#" class="hover:text-blue-400">Contacto</a></li>
  </ul>
</nav>
```

Y si querés hacerla **responsive con colapsado**, usás `hidden`, `md:flex` o `block`:

```html
<ul class="hidden md:flex space-x-6">
  ...
</ul>
```

💡 Así solo aparece el menú en pantallas medianas o más grandes.

---

## 💪 Ejercicio del módulo

Creá un formulario de contacto con una card:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Formulario Tailwind</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen">

  <div class="bg-white p-6 rounded-lg shadow-lg w-96">
    <h2 class="text-2xl font-bold mb-4 text-gray-800">Contáctanos</h2>

    <input type="text" placeholder="Nombre"
           class="w-full border border-gray-300 rounded px-3 py-2 mb-3 focus:outline-none focus:ring-2 focus:ring-blue-400">

    <input type="email" placeholder="Correo electrónico"
           class="w-full border border-gray-300 rounded px-3 py-2 mb-3 focus:outline-none focus:ring-2 focus:ring-blue-400">

    <textarea placeholder="Mensaje"
              class="w-full border border-gray-300 rounded px-3 py-2 mb-4 h-24 focus:outline-none focus:ring-2 focus:ring-blue-400"></textarea>

    <button class="bg-blue-500 text-white w-full py-2 rounded hover:bg-blue-600 transition">
      Enviar
    </button>
  </div>

</body>
</html>
```

✅ Vas a practicar:

- Inputs con focus
    
- Botón interactivo
    
- Bordes, sombras y espaciado
    
- Estructura de componentes reutilizables
    

---