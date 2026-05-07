En **CSS**, `:root` es un **selector pseudo-clase** que apunta al **elemento raíz del documento**.

En un documento **HTML**, el elemento raíz siempre es **`<html>`**, por lo que `:root` en la práctica selecciona ese elemento.

```css
:root {
  background: white;
}
```

Esto es equivalente a:

```css
html {
  background: white;
}
```

## ¿Para qué se usa principalmente?

Aunque técnicamente es igual que `html`, `:root` se usa sobre todo para **definir variables globales de CSS (custom properties)**.

### Ejemplo

```css
:root {
  --color-principal: blue;
  --espaciado: 16px;
}

h1 {
  color: var(--color-principal);
}

p {
  margin: var(--espaciado);
}
```

Aquí:

- `--color-principal`
    
- `--espaciado`
    

son **variables CSS globales** que se pueden usar en cualquier parte del documento con `var()`.

## ¿Por qué se usa `:root` y no `html`?

Hay dos razones principales:

### 1. Es más específico que `html`

`:root` tiene **mayor especificidad**, por lo que sus estilos tienen prioridad frente a `html`.

### 2. Es el estándar para variables globales

La convención en CSS moderno es declarar las **variables globales** dentro de `:root`.

## Ejemplo típico en proyectos

```css
:root {
  --color-primary: #3498db;
  --color-secondary: #2ecc71;
  --font-main: Arial, sans-serif;
}

body {
  font-family: var(--font-main);
}

button {
  background: var(--color-primary);
}
```

Esto permite **centralizar la configuración visual del sitio**.

## Resumen

`:root` se usa para:

- Seleccionar el **elemento raíz (`html`)**
    
- **Definir variables CSS globales**
    
- Tener **mayor especificidad que `html`**
    
- Centralizar **colores, tamaños, tipografías, etc.**
    

✔ Es una práctica muy común en **CSS moderno y sistemas de diseño**.

---