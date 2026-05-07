
CSS (**Cascading Style Sheets**) es un lenguaje que define la presentación visual de un documento HTML: colores, tamaños, fuentes, márgenes, disposición de elementos, animaciones, etc.  
La palabra **Cascading (en cascada)** significa que las reglas se aplican siguiendo una jerarquía (prioridad).

### Orden de prioridad

1. **Estilos inline** (más específicos).
2. **Estilos internos (en `<style>`)**.
3. **Estilos externos (archivo `.css`)**.
4. **Estilos por defecto del navegador** (los que trae Chrome, Firefox, etc.).

👉 Esto significa que si el mismo elemento tiene varios estilos, **gana el más específico y el último definido**.

---

## 🔹 Formas de aplicar CSS

### 1. Inline (en línea)

Escribir estilos directamente en el HTML con el atributo `style`.

```html
<p style="color: red; font-size: 20px;">Texto rojo y grande</p>
```

✅ Ventaja: rápido y simple para un único cambio.  
❌ Desventaja: difícil de mantener en proyectos grandes (se mezcla HTML y CSS).

---

### 2. Interno (en la etiqueta `<style>`)

Los estilos se colocan dentro del mismo archivo HTML, en la cabecera (`<head>`).

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      color: blue;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <p>Texto azul con CSS interno</p>
</body>
</html>
```

✅ Ventaja: útil para proyectos chicos o pruebas rápidas.  
❌ Desventaja: si tenés muchas páginas, se repite el código en cada una.

---

### 3. Externo (archivo separado `.css`)

Es la forma más usada en proyectos profesionales. Se crea un archivo independiente (ej: `styles.css`) y se enlaza al HTML con `<link>`.

📂 Estructura:

```
index.html
styles.css
```

📄 `index.html`

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p class="texto">Texto con CSS externo</p>
</body>
</html>
```

📄 `styles.css`

```css
.texto {
  color: green;
  font-size: 22px;
}
```

✅ Ventajas:

- Separación de estructura (HTML) y diseño (CSS).
- Se puede reutilizar el mismo CSS en muchas páginas.
- Más fácil de mantener y escalar.

---

📌 **Resumen rápido:**

- **Inline**: usar sólo para pruebas rápidas.
- **Interno**: sirve en prototipos o ejemplos simples.
- **Externo**: la mejor práctica para proyectos reales.

---