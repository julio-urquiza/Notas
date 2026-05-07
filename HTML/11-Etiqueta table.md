Las **tablas en HTML** se utilizan para **mostrar datos tabulares**, es decir, información organizada en **filas y columnas**, similar a una hoja de cálculo. Son muy útiles para presentar datos estructurados como listas de precios, horarios, estadísticas, etc.

---

## 1. Estructura básica de una tabla

Una tabla se construye con varias etiquetas que trabajan juntas:

- `<table>` → define la tabla
- `<tr>` → define una fila (**table row**)
- `<td>` → define una celda (**table data**)
- `<th>` → define una celda de encabezado (**table header**)

### Ejemplo básico

```html
<table>
  <tr>
    <th>Nombre</th>
    <th>Edad</th>
    <th>País</th>
  </tr>
  <tr>
    <td>Ana</td>
    <td>25</td>
    <td>Argentina</td>
  </tr>
  <tr>
    <td>Juan</td>
    <td>30</td>
    <td>Chile</td>
  </tr>
</table>
```

Resultado conceptual:

|Nombre|Edad|País|
|---|---|---|
|Ana|25|Argentina|
|Juan|30|Chile|

---

# 2. Etiquetas importantes dentro de una tabla

## `<table>`

Es el **contenedor principal** de la tabla.

```html
<table>
  ...
</table>
```

---

## `<tr>` (table row)

Define **una fila** de la tabla.

```html
<tr>
  <td>Dato</td>
</tr>
```

---

## `<td>` (table data)

Representa **una celda normal** dentro de una fila.

```html
<td>25</td>
```

---

## `<th>` (table header)

Define **una celda de encabezado**.  
Por defecto:

- el texto aparece **en negrita**
- se **centra**

```html
<th>Nombre</th>
```

---

# 3. Estructura semántica de una tabla

HTML permite organizar mejor las tablas con:

- `<thead>` → encabezado
- `<tbody>` → cuerpo
- `<tfoot>` → pie

### Ejemplo

```html
<table>
  <thead>
    <tr>
      <th>Producto</th>
      <th>Precio</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Notebook</td>
      <td>$1000</td>
    </tr>
    <tr>
      <td>Mouse</td>
      <td>$20</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Total</td>
      <td>$1020</td>
    </tr>
  </tfoot>
</table>
```

Esto **no cambia mucho el diseño**, pero mejora:

- **semántica**
- **accesibilidad**
- **organización del código**

---

# 4. Unir celdas

## `colspan`

Permite que **una celda ocupe varias columnas**.

```html
<td colspan="2">Total</td>
```

Ejemplo:

```html
<tr>
  <td colspan="2">Total</td>
</tr>
```

---

## `rowspan`

Permite que **una celda ocupe varias filas**.

```html
<td rowspan="2">Argentina</td>
```

---

# 5. Otros elementos útiles

## `<caption>`

Agrega **un título a la tabla**.

```html
<table>
  <caption>Lista de productos</caption>
</table>
```

---

# 6. Estilos básicos con CSS

Por defecto las tablas **no tienen bordes**, por lo que suele usarse CSS.

```html
<style>
table {
  border-collapse: collapse;
}

td, th {
  border: 1px solid black;
  padding: 8px;
}
</style>
```

---

# 7. Buenas prácticas

✔ Usar tablas **solo para datos tabulares**  
❌ No usarlas para **maquetar páginas** (antes se hacía, hoy se usa **CSS y Flexbox/Grid**).

---

✅ **Resumen rápido**

|Etiqueta|Función|
|---|---|
|`<table>`|contenedor de la tabla|
|`<tr>`|fila|
|`<td>`|celda normal|
|`<th>`|celda de encabezado|
|`<thead>`|encabezado de la tabla|
|`<tbody>`|contenido principal|
|`<tfoot>`|pie de tabla|
|`colspan`|une columnas|
|`rowspan`|une filas|

---

Para que una **tabla se pinte de forma intercalada** (una fila de un color y la siguiente de otro), se usa CSS con el **selector pseudo-clase `:nth-child()`**. Este patrón suele llamarse **“zebra striping”**.

---

# 1. Ejemplo básico

```html
<table>
  <tr>
    <th>Nombre</th>
    <th>Edad</th>
  </tr>
  <tr>
    <td>Ana</td>
    <td>25</td>
  </tr>
  <tr>
    <td>Juan</td>
    <td>30</td>
  </tr>
  <tr>
    <td>Pedro</td>
    <td>22</td>
  </tr>
</table>
```

CSS:

```css
tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:nth-child(odd) {
  background-color: white;
}
```

Resultado conceptual:

|Nombre|Edad|
|---|---|
|Ana|25|
|Juan|30|
|Pedro|22|

Las filas se alternan automáticamente.

---

# 2. Qué significa `nth-child`

`nth-child()` selecciona elementos según su **posición dentro del padre**.

Ejemplos:

```
nth-child(odd)   → filas impares (1,3,5...)
nth-child(even)  → filas pares (2,4,6...)
```

---

# 3. Forma más común (solo cambiar las pares)

Normalmente se escribe así:

```css
tr:nth-child(even) {
  background-color: #f2f2f2;
}
```

Solo se pinta una de las dos filas porque la otra queda con el color normal.

---

# 4. Evitar que el encabezado cambie de color

Si la tabla tiene `<thead>`, lo mejor es aplicar el estilo **solo al `tbody`**:

```css
tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}
```

Ejemplo:

```html
<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Edad</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Ana</td>
      <td>25</td>
    </tr>
    <tr>
      <td>Juan</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
```

---

# 5. Mejora común: efecto hover

Muy usado en tablas de datos.

```css
tbody tr:hover {
  background-color: #ddd;
}
```

---

✅ **Resumen**

Para filas intercaladas se usa:

```css
tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}
```

Esto crea el efecto **zebra** que mejora mucho la **legibilidad de tablas grandes**.

---
