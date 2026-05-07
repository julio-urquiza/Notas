
## 🔹 1. ¿Qué es ?

- Es una técnica para que tu sitio web **se adapte a distintos tamaños de pantalla**:
    - celulares
    - tablets
    - computadoras de escritorio
- La idea es que el contenido **se vea bien y sea usable** sin importar el dispositivo.

---

## 🔹 2. Media Queries

- Son **reglas condicionales en CSS** que aplican estilos **solo si se cumple cierta condición**, normalmente relacionada con **ancho, alto o tipo de dispositivo**.

### Sintaxis básica:

```css
@media (max-width: 600px) {
  body {
    background: lightblue;
  }
}
```

- `@media` → indica que es una regla condicional.
- `(max-width: 600px)` → se activa solo si la **pantalla tiene como máximo 600px de ancho**.
- Dentro de las llaves `{}` → estilos que se aplican solo en esa condición.

---

### 🔹 Otros ejemplos comunes

1️⃣ **Estilo para pantallas grandes**

```css
@media (min-width: 1200px) {
  body {
    background: lightgreen;
  }
}
```

2️⃣ **Rango de tamaños**

```css
@media (min-width: 601px) and (max-width: 1199px) {
  body {
    background: lightyellow;
  }
}
```

3️⃣ **Dispositivos con orientación específica**

```css
@media (orientation: portrait) {
  body {
    font-size: 18px;
  }
}
```

---

## 🔹 3. Ejemplo práctico

```css
body {
  background: white;
  font-size: 16px;
}

@media (max-width: 600px) {
  body {
    background: lightblue; /* para celulares */
    font-size: 14px;
  }
}

@media (min-width: 601px) and (max-width: 1024px) {
  body {
    background: lightyellow; /* para tablets */
    font-size: 15px;
  }
}
```

- **Resultado:**
    - Pantallas < 600px → fondo azul, fuente más pequeña
    - Entre 601px y 1024px → fondo amarillo, fuente un poco más grande
    - Mayor a 1024px → fondo blanco, fuente normal

---

✅ **Resumen rápido:**

- Responsive design = adaptar el diseño a distintos dispositivos
- Media queries = CSS condicional según tamaño, orientación, resolución, etc.
- Son esenciales para que tu web sea **usable y atractiva en móviles, tablets y desktops**.
