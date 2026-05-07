## 🔹 ¿Qué es Grid?

Es un sistema de diseño en CSS pensado para organizar elementos en **filas y columnas**.  
Con `display: grid;` activás el modo “rejilla” en un contenedor, y podés definir exactamente **cuántas filas y columnas** tendrá.

---

## 🔹 Propiedad clave: `grid-template-columns`

Define **cuántas columnas** tendrá tu grid y su tamaño.

Ejemplo:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 columnas iguales */
}
```

- `fr` significa _fracción_: reparte el espacio disponible.
- `1fr 2fr` → primera columna ocupa 1 parte, segunda ocupa 2 partes.

---

## 🔹 Propiedad complementaria: `grid-template-rows`

Define las filas:

```css
grid-template-rows: 100px 100px; /* 2 filas de 100px */
```

---

## 🔹 Ejemplo: tablero de 3 columnas × 2 filas

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;  /* 3 columnas iguales */
  grid-template-rows: 150px 150px;     /* 2 filas iguales */
  gap: 10px;                           /* espacio entre celdas */
  border: 2px solid black;
}

.item {
  background: lightblue;
  text-align: center;
  font-size: 20px;
  font-weight: bold;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
  <div class="item">4</div>
  <div class="item">5</div>
  <div class="item">6</div>
</div>
```

👉 Resultado:

- 3 columnas,
- 2 filas,
- cada celda con su número.

---

## 🔹 Otros súper poderes de Grid

- **Combinar celdas:**
   ```css
    .item1 {
      grid-column: 1 / 3; /* ocupa de la columna 1 a la 2 */
      grid-row: 1 / 3;    /* ocupa de la fila 1 a la 2 */
    }
    ```

- **Areas con nombre:**    
   ```css
    grid-template-areas: 
      "header header header"
      "sidebar main main"
      "footer footer footer";
    ```
    
- **Responsive con `repeat()` y `auto-fit`:**
   ```css
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    ```
    (crea columnas automáticas que se ajustan a pantallas chicas o grandes).

---

✅ Resumen:

- Grid = filas + columnas → layouts completos.
- Flexbox = una dimensión → fila **o** columna.
- Juntos se usan mucho: **Grid para estructura general**, **Flexbox para alinear contenido dentro de cada celda**.

---
