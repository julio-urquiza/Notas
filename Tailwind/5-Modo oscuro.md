https://tailwindcss.com/docs/dark-mode#toggling-dark-mode-manually
## Descripción general

Ahora que el modo oscuro es una característica de primera clase de muchos sistemas operativos, se está volviendo cada vez más común diseñar una versión oscura de su sitio web para combinar con el diseño predeterminado.

Para que esto sea lo más fácil posible, Tailwind incluye una `dark`variante que te permite diseñar tu sitio de manera diferente cuando el modo oscuro está habilitado:
![[5-Pasted image 20251008223419.png]]

``` html
<div class="bg-white dark:bg-gray-800 rounded-lg px-6 py-8 ring shadow-xl ring-gray-900/5">
  <div>
    <span class="inline-flex items-center justify-center rounded-md bg-indigo-500 p-2 shadow-lg">
      <svg class="h-6 w-6 stroke-white" ...>
        <!-- SVG content -->
      </svg>
    </span>
  </div>

  <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight">
    Writes upside-down
  </h3>

  <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm">
    The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.
  </p>
</div>

```

De forma predeterminada, se utiliza la `prefers-color-scheme`función de medios CSS, pero también puedes crear sitios que admitan alternar el modo oscuro manualmente anulando la variante oscura.

## Activar y desactivar el modo oscuro manualmente

Si desea que su tema oscuro sea controlado por un selector CSS en lugar de la `prefers-color-scheme`consulta de medios, anule la `dark`variante para usar su selector personalizado:

``` css
@import "tailwindcss";@custom-variant dark (&:where(.dark, .dark *));
```

Ahora, en lugar de que `dark:*`las utilidades se apliquen en función de `prefers-color-scheme`, se aplicarán siempre que la `dark`clase esté presente anteriormente en el árbol HTML:

``` html
<html class="dark">
	<body>
		<div class="bg-white dark:bg-black">
			<!-- ... -->    
		</div>
	</body>
</html>
```

La forma en que agrega la `dark`clase al `html`elemento depende de usted, pero un enfoque común es utilizar un poco de JavaScript que actualiza el `class`atributo y sincroniza esa preferencia en algún lugar como `localStorage`.

### Uso de un atributo de datos

Para usar un atributo de datos en lugar de una clase para activar el modo oscuro, simplemente anule la `dark`variante con un selector de atributos:

``` css
@import "tailwindcss";@custom-variant dark (&:where([data-theme=dark], [data-theme=dark] *));
```

Ahora, las utilidades del modo oscuro se aplicarán siempre que el `data-theme`atributo se configure en `dark`algún lugar del árbol:

``` html
<html data-theme="dark">
	<body>  
		<div class="bg-white dark:bg-black"> 
			<!-- ... -->   
		</div> 
	</body>
</html>
```

### Con soporte para temas del sistema
Para crear conmutadores de tema de tres vías que admitan el modo claro, el modo oscuro y el tema del sistema, use un selector de modo oscuro personalizado y la `window.matchMedia()`API para detectar el tema del sistema y actualizar el `html`elemento cuando sea necesario.

A continuación se muestra un ejemplo sencillo de cómo puede admitir el modo claro y el modo oscuro, además de respetar las preferencias del sistema operativo:

espagueti.js

``` js
// On page load or when changing themes, best to add inline in `head` to avoid FOUC
document.documentElement.classList.toggle( 
	"dark",
	localStorage.theme === "dark" || 
		(!("theme" in localStorage) && window.matchMedia("(prefers-color-scheme: dark)").matches),
);
// Whenever the user explicitly chooses light mode
localStorage.theme = "light";
// Whenever the user explicitly chooses dark mode
localStorage.theme = "dark";
// Whenever the user explicitly chooses to respect the OS preference
localStorage.removeItem("theme");
```

Nuevamente, puedes administrar esto como quieras, incluso almacenar la preferencia del lado del servidor en una base de datos y renderizar la clase en el servidor: depende totalmente de ti.