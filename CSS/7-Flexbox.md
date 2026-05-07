## 🔹 ¿Qué es Flexbox?

Es un sistema de diseño que te permite **alinear y distribuir elementos dentro de un contenedor** de forma muy fácil y flexible.  
Con `display: flex;` activás el “modo flex” en un contenedor, y todos sus hijos se vuelven _flex items_.

---

## 🔹 Propiedades más importantes del contenedor

1. **`display: flex;`**  
    Activa Flexbox en el contenedor.

2. **`flex-direction`**  
    Define la dirección principal:
    - `row` → en fila (por defecto).
    - `column` → en columna.
    - `row-reverse` / `column-reverse`.

3. **`justify-content`** (eje principal, horizontal si es `row`)  
    Distribuye los elementos:
    - `flex-start` (al inicio).
    - `center` (centrados).
    - `flex-end` (al final).
    - `space-between` (espaciados con huecos entre ellos).
    - `space-around` (espacios iguales alrededor).
    - `space-evenly` (espacios exactamente iguales).

4. **`align-items`** (eje cruzado, vertical si es `row`)  
    Alinea los elementos verticalmente:
	- **`stretch`** (valor por defecto)
	    - Los ítems se estiran para ocupar todo el alto (si el contenedor es un `row`) o ancho (si es un `column`).
	    - Solo funciona si los ítems no tienen un tamaño fijo en ese eje.
	- **`flex-start`**
	    - Los ítems se pegan al **inicio del eje cruzado**.
	    - Ejemplo: en un `row`, se alinean arriba.
	- **`flex-end`**
	    - Los ítems se pegan al **final del eje cruzado**.
	    - Ejemplo: en un `row`, se alinean abajo.
	- **`center`**
	    - Los ítems se alinean en el **centro del eje cruzado**.
	    - Ejemplo: en un `row`, todos los ítems quedan centrados verticalmente.
	- **`baseline`**
	    - Alinea los ítems en la **línea base del texto**.
	    - Muy útil si tenés cajas con diferentes alturas pero querés que el texto quede alineado.

5. **`flex-wrap`**  
    Permite que los elementos bajen a otra línea si no entran.
	- **`nowrap`** (por defecto)→ Todos los elementos en **una sola fila** (aunque se achiquen).
	- **`wrap`**→  Los elementos **pasan a la siguiente línea** si no entran.
	- **`wrap-reverse`**→  Igual que `wrap`, pero la nueva línea aparece **arriba** (en vez de abajo).

6. **`align-content`**
	- **`stretch`** (valor por defecto)  
	    Las filas se estiran para llenar todo el espacio disponible.
	- **`flex-start`**  
	    Todas las filas se agrupan al **inicio del eje cruzado** (arriba si `flex-direction: row`).
	- **`flex-end`**  
	    Todas las filas se agrupan al **final del eje cruzado** (abajo si `row`).
	- **`center`**  
	    Las filas se agrupan en el **centro del eje cruzado**.
	- **`space-between`**  
	    La primera fila se pega al inicio, la última al final, y las demás se reparten con espacios iguales entre ellas.
	- **`space-around`**  
	    Todas las filas tienen **espacio igual arriba y abajo**, con la mitad de ese espacio en los extremos.
	- **`space-evenly`**  
	    Igual que `space-around`, pero los espacios son **exactamente iguales en todo el eje** (incluyendo bordes).

---

## 🔹 Ejemplo: tu caso

Querés **3 cajas en fila, centradas verticalmente y espaciadas**.

```css
.container {
  display: flex;                 /* Activamos flex */
  justify-content: space-between;/* Espacio entre cajas */
  align-items: center;           /* Centrado vertical */
  height: 200px;                 /* Para que se note el centrado */
  border: 2px solid black;
}

.box {
  width: 60px;
  height: 60px;
  background-color: lightblue;
  text-align: center;
  line-height: 60px; /* centra texto verticalmente */
}
```

```html
<div class="container">
  <div class="box">1</div>
  <div class="box">2</div>
  <div class="box">3</div>
</div>
```

👉 Resultado:

- Las cajas quedan **en fila**,
- **espaciadas** (gracias a `space-between`),
- y **centradas verticalmente** dentro de los 200px de altura.

---

## 🔹 Bonus: tips rápidos con Flexbox

- Si querés que un ítem ocupe más espacio que otro: `flex-grow: 1;`
- Para centrar algo totalmente en pantalla:

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* ocupa toda la pantalla */
}
```

---
