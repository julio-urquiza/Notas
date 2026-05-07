# 📦 El Box Model en CSS

Cada elemento en una página se representa como una **caja rectangular**.  
Esa caja está compuesta por 4 áreas:

```
┌──────────────────────────┐
│        Margin            │   (margen externo)
│ ┌──────────────────────┐ │
│ │       Border         │ │   (borde)
│ │ ┌──────────────────┐ │ │
│ │ │     Padding      │ │ │   (relleno interno)
│ │ │ ┌──────────────┐ │ │ │
│ │ │ │   Content    │ │ │ │   (contenido: texto, img…)
│ │ │ └──────────────┘ │ │ │
│ │ └──────────────────┘ │ │
│ └──────────────────────┘ │
└──────────────────────────┘
```

---

## 🔹 1. Content (contenido)

Es lo que está dentro de la caja: texto, imágenes, botones, etc.

```css
.caja {
  width: 200px; /* ancho del contenido */
  height: 100px; /* alto del contenido */
}
```

---

## 🔹 2. Padding (relleno interno)

Espacio entre el contenido y el borde. **Agranda el área clickeable** en botones, por ejemplo.

```css
.caja {
  padding: 20px; /* aplica a todos los lados */
}
```

👉 Se puede controlar cada lado:

```css
padding-top: 10px;
padding-right: 15px;
padding-bottom: 20px;
padding-left: 5px;
```

O con atajos:

```css
padding: 10px 15px 20px 5px; /* top right bottom left */
```

---

## 🔹 3. Border (borde)

Delimita el área de la caja. Puede tener grosor, estilo y color.

```css
.caja {
  border: 2px solid red; /* grosor, estilo y color */
}
```

Estilos comunes: `solid`, `dashed`, `dotted`, `double`, `none`.

---

## 🔹 4. Margin (margen externo)

Espacio entre la caja y otras cajas (afuera del borde).

```css
.caja {
  margin: 30px;
}
```

👉 Igual que `padding`, se puede aplicar por lados:  
`margin-top`, `margin-right`, etc.

---

## 📏 Ejemplo completo

```css
.caja {
  width: 200px;       /* contenido */
  height: 100px;
  padding: 20px;      /* relleno */
  border: 5px solid blue;
  margin: 30px;       /* espacio externo */
  background: lightyellow;
}
```

👉 El tamaño total de la caja sería:

```
Total width = width + padding izq/der + border izq/der + margin izq/der
Total height = height + padding top/bottom + border top/bottom + margin top/bottom
```

Con los valores de arriba:

- Ancho total = `200 + (20+20) + (5+5) + (30+30) = 310px`
- Alto total = `100 + (20+20) + (5+5) + (30+30) = 210px`

---

## ⚡ Tip: `box-sizing`

Por defecto, CSS **suma padding y border al ancho/alto**.  
Si querés que el `width` incluya todo (más fácil de calcular), usá:

```css
* {
  box-sizing: border-box;
}
```

👉 Esto hace que el `width` sea **el tamaño final de la caja**, sin cálculos raros.  
Es una buena práctica y casi todos los proyectos modernos lo usan.

---

📌 En resumen:

- **Content** = lo que se ve (texto, img).
- **Padding** = espacio interno.
- **Border** = línea alrededor.
- **Margin** = espacio externo con otras cajas.

---
## 🔹 El problema sin `box-sizing`

Imaginá que tenés esta caja:

```css
.caja {
  width: 200px;
  padding: 20px;
  border: 5px solid red;
}
```

- `width: 200px` → parece que la caja debería medir **200px de ancho**.
- Pero en realidad, **el navegador suma el padding y el border al ancho total**:

```
ancho total = width + padding izquierdo + padding derecho + border izquierdo + border derecho
ancho total = 200 + 20 + 20 + 5 + 5 = 250px
```

👉 O sea, aunque vos le digas 200px, termina midiendo **250px**.

---

## 🔹 Con `box-sizing: border-box`

Si agregás:

```css
* {
  box-sizing: border-box;
}
```

Entonces el navegador **no suma el padding ni el border al ancho**, sino que los incluye dentro del `width`.

En el mismo ejemplo:

```css
.caja {
  width: 200px;
  padding: 20px;
  border: 5px solid red;
  box-sizing: border-box;
}
```

Ahora:

```
ancho total = 200px exactos
```

👉 El `padding` y el `border` se ajustan **dentro** de esos 200px.  
La caja nunca se pasa del tamaño que definiste.

---

## 📌 Diferencia visual

- **Sin `border-box`:** la caja se hace más grande de lo que vos pusiste.
- **Con `border-box`:** la caja siempre mide lo que dijiste en `width` o `height`.

Por eso, casi todos los proyectos modernos empiezan el CSS con esto:

```css
* {
  box-sizing: border-box;
}
```

Así todo es más predecible.

---
