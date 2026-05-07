## ¿Qué es Emmet en HTML?

**Emmet** es un plugin (integrado por defecto en muchos editores modernos) que permite escribir **abreviaciones** y expandirlas automáticamente a código HTML (y CSS) completo. Su objetivo es acelerar el flujo de maquetado utilizando una sintaxis inspirada en selectores CSS.

Está disponible en editores como:

- Visual Studio Code
- Sublime Text
- WebStorm

En VS Code viene activado por defecto.

---

## ¿Cómo funciona?

Escribes una abreviatura y presionas `Tab` (o `Enter`, según configuración).  
Ejemplo:

```html
div
```

Presionas `Tab` y se expande a:

```html
<div></div>
```

---

## Sintaxis básica de Emmet

Emmet usa operadores similares a CSS:

### 1. Crear etiquetas

```html
p
```

→

```html
<p></p>
```

---

### 2. Jerarquía (`>`) – hijo directo

```html
ul>li
```

→

```html
<ul>
    <li></li>
</ul>
```

---

### 3. Hermanos (`+`)

```html
h1+p
```

→

```html
<h1></h1>
<p></p>
```

---

### 4. Multiplicación (`*`)

```html
li*3
```

→

```html
<li></li>
<li></li>
<li></li>
```

---

### 5. Clases (`.`)

```html
div.container
```

→

```html
<div class="container"></div>
```

---

### 6. IDs (`#`)

```html
div#main
```

→

```html
<div id="main"></div>
```

---

### 7. Atributos (`[]`)

```html
input[type="text" placeholder="Nombre"]
```

→

```html
<input type="text" placeholder="Nombre">
```

---

### 8. Texto interno (`{}`)

```html
a{Click aquí}
```

→

```html
<a href="">Click aquí</a>
```

---

### 9. Numeración automática (`$`)

```html
li.item$*3
```

→

```html
<li class="item1"></li>
<li class="item2"></li>
<li class="item3"></li>
```

---

## Ejemplo práctico completo

Abreviatura:

```html
div.container>header>h1{Mi sitio}+nav>ul>li*3>a{Sección $}
```

Expansión:

```html
<div class="container">
    <header>
        <h1>Mi sitio</h1>
        <nav>
            <ul>
                <li><a href="">Sección 1</a></li>
                <li><a href="">Sección 2</a></li>
                <li><a href="">Sección 3</a></li>
            </ul>
        </nav>
    </header>
</div>
```

Esto ahorra muchísimo tiempo en estructuras repetitivas.

---

## Ventajas técnicas

- Reduce errores de sintaxis.
- Acelera prototipado.
- Mejora productividad en maquetado.
- Compatible también con CSS (por ejemplo `m10` → `margin: 10px;`).

---