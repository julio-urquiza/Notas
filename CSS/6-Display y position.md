# 📐 Display

El atributo `display` define **cómo se comporta una caja en el flujo de la página**.

### 🔹 `block`

- Ocupa **todo el ancho disponible**.
- Empuja lo que viene después a la siguiente línea.  
    Ejemplos: `<div>`, `<p>`, `<h1>`…

```css
div {
  display: block;
}
```

### 🔹 `inline`

- Ocupa **solo el espacio necesario**.
- Se ubica en la **misma línea** con otros elementos.  
    Ejemplos: `<span>`, `<a>`, `<strong>`…

```css
span {
  display: inline;
}
```

### 🔹 `inline-block`

- Se comporta como `inline` (se alinea con otros en la misma línea).
- **Pero admite width, height, margin y padding verticales** (cosa que `inline` no hace).

```css
img {
  display: inline-block;
}
```

👉 Ejemplo rápido:

```html
<p>
  Texto normal <span style="background:yellow;">inline</span>
  <div style="background:lightblue;">block</div>
  <span style="display:inline-block; width:100px; background:lightgreen;">inline-block</span>
</p>
```

---

# 📍 Position

El atributo `position` controla **cómo se coloca un elemento en relación a otros**.

### 🔹 `static` (por defecto)

- El navegador coloca los elementos en orden normal, uno debajo del otro.
- No se puede mover con `top`, `left`, etc.

### 🔹 `relative`

- Se coloca en su posición normal, **pero podés moverlo** con `top`, `right`, `bottom`, `left`.
- **Deja el espacio original reservado**.

```css
.caja {
  position: relative;
  top: 20px;  /* baja 20px desde donde estaría */
  left: 10px;
}
```

### 🔹 `absolute`

- Se coloca en relación a su **primer ancestro con `position: relative` (o el `<html>` si no hay)**.
- Se **saca del flujo normal**, no ocupa espacio en la página.

```css
.hijo {
  position: absolute;
  top: 0;
  right: 0;
}
```

### 🔹 `fixed`

- Se coloca en relación a la **ventana del navegador**.
- No se mueve aunque hagas scroll.  
    👉 Perfecto para menús o botones flotantes.

```css
.menu {
  position: fixed;
  top: 0;
  width: 100%;
}
```

### 🔹 `sticky`

- Se comporta como `relative`… hasta que se hace scroll y llega a un punto (`top`, `bottom`), y ahí se vuelve **fijo**.
- Muy usado para cabeceras que se “pegan” al llegar arriba.

```css
.header {
  position: sticky;
  top: 0;
}
```

---

# 🧪 Ejercicio práctico: Menú fijo arriba

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      margin: 0;
      font-family: Arial;
    }
    .menu {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      background: darkblue;
      color: white;
      padding: 15px;
      text-align: center;
    }
    .contenido {
      margin-top: 70px; /* para que no tape el menú */
      height: 2000px;  /* contenido largo para scrollear */
      background: linear-gradient(white, lightgray);
    }
  </style>
</head>
<body>
  <div class="menu">Soy un menú fijo arriba</div>
  <div class="contenido">Bajá con scroll y el menú sigue ahí 👆</div>
</body>
</html>
```

---

📌 En resumen:

- `block`, `inline`, `inline-block` → controlan cómo se comporta una caja en la **línea y ancho**.
- `static`, `relative`, `absolute`, `fixed`, `sticky` → controlan su **posición en la página**.

---
## 1️⃣ `static` (por defecto)

- **Recomendado para:** la mayoría de los elementos normales, texto, párrafos, divs simples.
- No necesitas moverlos ni hacer overlays.
- **Ventaja:** es el comportamiento más natural, fácil de mantener.

---

## 2️⃣ `relative`

- **Recomendado para:**
    - Ajustar ligeramente un elemento respecto a su posición normal.
    - Crear un **referente para hijos con `absolute`**.
- **Ejemplo:** mover un botón 10px hacia abajo sin alterar el flujo de otros elementos.

---

## 3️⃣ `absolute`

- **Recomendado para:**
    - Posicionar elementos dentro de un contenedor específico.
    - Crear overlays, menús desplegables o tooltips.
- **Cuidado:** se saca del flujo, así que otros elementos pueden “chocar” si no se planifica bien.

---

## 4️⃣ `fixed`

- **Recomendado para:**
    - Menús que siempre deben estar visibles (header fijo, botón “scroll to top”).
    - Elementos flotantes en la pantalla que no cambian al hacer scroll.
- **Cuidado:** puede cubrir contenido si no dejás espacio suficiente.

---

## 5️⃣ `sticky`

- **Recomendado para:**
    - Cabeceras o barras que se quieren **pegar al hacer scroll** pero solo dentro de un contenedor.
    - Listas con títulos que se mantienen visibles mientras haces scroll.
- **Ventaja:** combina lo mejor de `relative` y `fixed`.
- **Cuidado:** funciona solo dentro del contenedor padre; si el padre es pequeño, el sticky no se nota.

---

### ✅ Resumen práctico

|Position|Uso recomendado|
|---|---|
|static|Elementos normales, texto, divs simples|
|relative|Ajustes pequeños, referente para absolute|
|absolute|Overlays, tooltips, dropdowns dentro de un contenedor|
|fixed|Menús y elementos que deben estar siempre visibles|
|sticky|Cabeceras o barras que se “pegan” al hacer scroll dentro de un contenedor|

---

💡 **Tip general:**

- Siempre que puedas, **usa `static` o `relative`** para no complicar el flujo.
- `absolute` y `fixed` son poderosos, pero si abusás se puede volver un “caos” en el diseño.
- `sticky` es genial para interfaces modernas, como tablas o listas con headers pegajosos.

---