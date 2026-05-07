## 🎨 Colores en CSS

CSS admite varias formas de definir un color:

### 1. Nombre de color

```css
p {
  color: red; /* rojo */
  background-color: black; /* negro */
}
```

👉 Hay una lista de ~140 nombres estándar (`red`, `blue`, `green`, `yellow`, `orange`, `purple`, `black`, `white`, etc.).

---

### 2. Hexadecimal

```css
h1 {
  color: #ff0000; /* rojo */
  background: #00ff00; /* verde */
}
```

- Formato: `#RRGGBB` (valores de 00 a FF en **hexadecimal**).
- También podés usar la versión corta: `#f00` equivale a `#ff0000`.

---

### 3. RGB / RGBA

```css
div {
  color: rgb(255, 0, 0);   /* rojo */
  background: rgba(0, 0, 255, 0.5); /* azul con 50% de transparencia */
}
```

- **rgb(r, g, b)**: cada valor va de 0 a 255.
- **rgba(r, g, b, a)**: `a` es la opacidad (0 = transparente, 1 = opaco).

---

### 4. HSL / HSLA

```css
button {
  background: hsl(0, 100%, 50%); /* rojo */
  color: hsla(120, 60%, 40%, 0.7); /* verde oscuro semi-transparente */
}
```

- **hsl(hue, saturation, lightness)**:
    - **Hue (tono):** 0 = rojo, 120 = verde, 240 = azul.
    - **Saturation (saturación):** 0% = gris, 100% = color puro.
    - **Lightness (luminosidad):** 0% = negro, 100% = blanco.

👉 HSL es muy usado en diseño moderno porque es más intuitivo para variar tonos y crear paletas.

---

## 📏 Unidades en CSS

### 🔹 Absolutas

- **px (píxeles):** tamaño fijo, no cambia con el zoom ni con la pantalla.
   ```css
    p { font-size: 16px; }
    ```


👉 Ventaja: precisión.  
👉 Desventaja: menos flexible en responsive.

---

### 🔹 Relativas

Se adaptan según el contexto. Son clave en el **diseño responsive**.

1. **% (porcentaje)**  
    Relativo al contenedor padre.
   ```css
    div {
      width: 50%; /* la mitad del ancho del padre */
    }
    ```

2. **em (relative to parent font-size)**  
    Relativo al tamaño de fuente del **elemento padre**.
   ```css
    p {
      font-size: 1.2em; /* 1.2 veces el tamaño del padre */
    }
    ```

3. **rem (relative to root)**  
    Relativo al tamaño de fuente del **html** (raíz).
   ```css
    p {
      font-size: 2rem; /* 2 veces el tamaño base del documento */
    }
    ```


👉 Diferencia entre `em` y `rem`:

- `em` → depende del padre inmediato.
- `rem` → siempre depende del `<html>`.

4. **vh (viewport height)**  
    Relativo al alto de la pantalla.  
    `100vh` = 100% de la altura visible.

5. **vw (viewport width)**  
    Relativo al ancho de la pantalla.  
    `100vw` = 100% del ancho visible.


👉 Ejemplo práctico:

```css
.hero {
  height: 100vh; /* ocupa toda la pantalla */
  width: 100vw;  /* ocupa todo el ancho */
}
```

---

## ⚖️ ¿Cuándo usar cada una?

- **px** → cuando querés precisión exacta (bordes, iconos).
    
- **em / rem** → para fuentes y paddings flexibles.
    
- **%** → cuando querés proporciones relativas a un contenedor.
    
- **vh / vw** → para pantallas completas o layouts fluidos.
    

---