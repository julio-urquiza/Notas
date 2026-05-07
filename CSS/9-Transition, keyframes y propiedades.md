## 🔹 1. **Transiciones (`transition`)**

Sirven para que los cambios de estilo (por ejemplo, al hacer hover) no sean **instantáneos**, sino que tengan un **efecto suave**.

```css
.btn {
  background: blue;
  color: white;
  padding: 10px 20px;
  transition: background 0.3s ease; /* cambia en 0.3s */
}

.btn:hover {
  background: red;
}
```

👉 Resultado: al pasar el mouse, el botón cambia de **azul a rojo suavemente** en 0.3 segundos.  
Sin `transition`, el cambio sería inmediato.

---

## 🔹 2. **Animaciones (`@keyframes`)**

Permiten crear movimientos o cambios más complejos y repetitivos.

```css
@keyframes girar {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.circulo {
  width: 50px;
  height: 50px;
  background: purple;
  border-radius: 50%;
  animation: girar 2s linear infinite;
}
```

👉 Resultado: el círculo gira **infinitamente**.  
Podés animar propiedades como colores, posiciones, tamaños, opacidad, etc.

---

## 🔹 3. **Variables CSS (`custom properties`)**

Son como **“variables” en programación**, pero dentro del CSS.  
Se definen en un selector (normalmente en `:root` para que estén disponibles en todo el documento).

```css
:root {
  --color-principal: #3498db;
  --espaciado: 16px;
}

.card {
  background: var(--color-principal);
  margin: var(--espaciado);
  padding: var(--espaciado);
}
```

👉 Ventaja: si querés cambiar el **color principal** o el **espaciado**, solo modificás la variable en un solo lugar.  
Esto hace que el código sea más **ordenado y fácil de mantener**.

---

📌 En resumen:

- **Transition** → suaviza cambios.
- **Animation** → movimientos complejos con `@keyframes`.
- **Variables** → reuso de valores, consistencia y mantenimiento fácil.

---
