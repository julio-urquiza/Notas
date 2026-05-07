## 🔹 1. Selector por **etiqueta**

Afecta a **todas las etiquetas** de un mismo tipo en la página.

```css
p {
  color: blue;
}
```

👉 Este código vuelve **azules todos los `<p>`** del documento.  
✔️ Útil cuando querés un estilo global para un elemento común (ej: todos los párrafos).  
❌ Pero si necesitás que un solo párrafo sea diferente, vas a necesitar clases o ids.

---

## 🔹 2. Selector por **clase**

Se aplica a todos los elementos que tengan el atributo `class="..."`.

```css
.destacado {
  font-weight: bold;
  color: red;
}
```

📄 HTML:

```html
<p class="destacado">Este párrafo está en negrita y rojo.</p>
<p>Este no tiene clase, así que mantiene su estilo normal.</p>
```

✔️ Ventaja: podés **reutilizar** la misma clase en muchos elementos.  
✔️ Se pueden aplicar **múltiples clases** a un mismo elemento:

```html
<p class="destacado grande">Texto especial</p>
```

---

## 🔹 3. Selector por **id**

Se aplica a un único elemento que tenga `id="..."`.

```css
#titulo {
  font-size: 24px;
  text-align: center;
}
```

📄 HTML:

```html
<h1 id="titulo">Soy un título único</h1>
```

✔️ Ventaja: sirve para **identificar un elemento único** en la página.  
❌ Problema: **los ids no deberían repetirse** en el mismo documento.  
👉 En CSS moderno se recomienda usar más **clases** que ids, porque los ids tienen **más peso en la cascada** y complican la organización.

---

## 🔹 Diferencias principales

|Selector|Símbolo|Uso típico|Reutilizable|Peso en CSS|
|---|---|---|---|---|
|Etiqueta|`p {}`|Estilo global para una etiqueta|Sí (afecta a todas)|Bajo|
|Clase|`.clase {}`|Estilos compartidos|Sí|Medio|
|Id|`#id {}`|Un solo elemento único|No|Alto|

---

## 🔹 Ejemplo combinado

📄 HTML:

```html
<h1 id="titulo">Encabezado principal</h1>
<p class="destacado">Texto destacado en rojo.</p>
<p>Texto común en azul.</p>
```

📄 CSS:

```css
p {
  color: blue;
}
.destacado {
  color: red;
  font-weight: bold;
}
#titulo {
  color: green;
  text-transform: uppercase;
}
```

👉 Resultado:

- Todos los `<p>` → azules.
- El `<p class="destacado">` → rojo y negrita (su clase pisa al estilo general de `p`).
- El `<h1 id="titulo">` → verde y mayúsculas.

---