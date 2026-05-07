Tailwind **es un framework de CSS** que funciona con un enfoque llamado **utility-first** (clases utilitarias).  
En vez de escribir CSS desde cero o usar componentes ya diseñados (como en Bootstrap), te da un montón de clases pequeñas y específicas que aplicás directamente en el HTML para dar estilo.

Por ejemplo:

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded">
  Click aquí
</button>
```

Ese botón está hecho sin escribir CSS adicional.  
Cada clase significa algo concreto:

- `bg-blue-500` → fondo azul (tono 500 de la paleta).
- `text-white` → texto blanco.
- `px-4` → padding horizontal de 1rem.
- `py-2` → padding vertical de 0.5rem.
- `rounded` → bordes redondeados.

### Ventajas de Tailwind

- **Rápido para prototipar** → armás interfaces sin casi tocar archivos CSS.
- **Consistente** → todas las clases siguen la misma escala de medidas, colores y espaciados.
- **Altamente personalizable** → podés modificar la configuración (tailwind.config.js) para usar tu propia paleta, tipografías, breakpoints, etc.
- **Responsive fácil** → con prefijos (`sm:`, `md:`, `lg:`) definís cómo se adapta en distintos tamaños de pantalla.

Ejemplo responsive:

```html
<div class="text-sm md:text-base lg:text-lg">
  Texto que cambia de tamaño según la pantalla
</div>
```

👉 En resumen: **Tailwind no te da componentes listos, sino un sistema de utilidades para que armes tus propios diseños rápido y de forma controlada**.
