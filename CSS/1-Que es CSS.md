CSS significa **Cascading Style Sheets** o en español **Hojas de Estilo en Cascada**.  
Es un **lenguaje de diseño** que se usa junto con **HTML** para dar estilo y presentación a las páginas web.

👉 Con **HTML** defines la **estructura** (qué elementos hay: títulos, párrafos, botones, imágenes…).  
👉 Con **CSS** defines la **apariencia** (colores, tamaños, márgenes, animaciones, posiciones…).

### Ejemplo básico

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 {
      color: blue;          /* El texto será azul */
      font-size: 36px;      /* Tamaño de fuente */
      text-align: center;   /* Centrado */
    }

    p {
      color: gray;
      line-height: 1.5;
    }
  </style>
</head>
<body>
  <h1>Hola, mundo</h1>
  <p>Esto es un párrafo con estilo.</p>
</body>
</html>
```

### Cosas importantes de CSS

- **Selectores** → dicen a qué elemento aplicar estilos (`h1`, `.clase`, `#id`).
    
- **Propiedades** → definen qué característica cambiar (`color`, `font-size`, `margin`).
    
- **Valores** → asignan el estilo (`red`, `20px`, `center`).
    
- **Cascada** → si hay varios estilos, el navegador decide cuál aplicar siguiendo reglas de **prioridad**.
    

🔹 En resumen: **HTML es el esqueleto** de la web y **CSS es la ropa, los colores y el maquillaje** que la hace atractiva.
