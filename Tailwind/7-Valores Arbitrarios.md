### 1. Valores Arbitrarios para Utilidades Existentes

Si necesitas un valor específico para una utilidad (como ancho, alto, color, etc.) que no está en la escala de tu tema, simplemente pones el valor dentro de corchetes después del prefijo de la utilidad.

**Sintaxis:** `[utilidad]-[valor]`

**Ejemplos:**

| Propósito                           | Clase de Tailwind | CSS Resultante (ejemplo)     |
| ----------------------------------- | ----------------- | ---------------------------- |
| **Ancho** de 42 píxeles             | `w-[42px]`        | `width: 42px;`               |
| **Alto** de 10 rem                  | `h-[10rem]`       | `height: 10rem;`             |
| **Color de fondo** con código hex   | `bg-[#316ff6]`    | `background-color: #316ff6;` |
| **Margen** superior de 0.5 pulgadas | `mt-[0.5in]`      | `margin-top: 0.5in;`         |
| **Tamaño de fuente** de 22 píxeles  | `text-[22px]`     | `font-size: 22px;`           |

Puedes usar funciones de CSS como `calc()` dentro de los corchetes:
- **Ejemplo con `calc()`:** `h-[calc(100vh-10px)]` genera `height: calc(100vh - 10px);`
    - **Importante:** Para los espacios en funciones como `calc()`, usa un **guion bajo** (`_`) en lugar de un espacio. Tailwind lo convertirá automáticamente en un espacio: `w-[calc(100%_-_3rem)]`

### 2. Propiedades Arbitrarias (CSS Completo)

Si necesitas usar una propiedad CSS para la cual Tailwind no tiene una utilidad integrada (o quieres establecer una variable CSS), puedes usar los corchetes sin prefijo de utilidad, escribiendo la propiedad completa.
**Sintaxis:** `[propiedad: valor]`

**Ejemplos:**

- **Propiedad CSS arbitraria:** `<div class="[mask-type:luminance]">` genera `mask-type: luminance;`
- **Definir una variable CSS:** `<div class="[--gutter-width:1rem]">` genera `--gutter-width: 1rem;`
- **URL de fondo:** `<div class="bg-[url('/path/to/image.jpg')]">`

### 3. Variantes Arbitrarias (Selectores CSS)

Para aplicar estilos basados en selectores CSS complejos (como `nth-child`, selectores de atributo, etc.), puedes usar los corchetes para escribir un selector completo como una variante.
**Sintaxis:** `[&selector]:[utilidad]`

**Ejemplos:**

- **Último hijo de un `ul` en `sm`:** `<li class="sm:last:border-none">` (Si ya existe la variante) o usando selector arbitrario: `<li class="sm:[&:last-child]:border-none">`
- **Estilo a un hijo con atributo:** `<div class="[&>[data-active]+span]:text-blue-600">`
    - Esto aplica `text-blue-600` al `span` que sigue inmediatamente a un elemento con el atributo `data-active`.

### Consejos Clave

- **Usa guion bajo (`_`) para los espacios:** Dentro de los corchetes, un guion bajo se convierte en un espacio (necesario para funciones como `calc()` o valores como `grid-cols-[1fr_500px_2fr]`).
- **Ten cuidado con el uso excesivo:** Los valores arbitrarios son ideales para valores únicos o excepcionales. Si vas a reutilizar un valor, es mejor **personalizar tu tema** en el archivo `tailwind.config.js` para mantener la consistencia y aprovechar el sistema de diseño de Tailwind.
- **Compatibilidad:** Los valores arbitrarios funcionan a partir de **Tailwind CSS v3.0** (gracias al motor JIT, que ahora está activado por defecto).