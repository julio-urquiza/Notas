En HTML (y en la web en general), **rutas absolutas** y **rutas relativas** son formas de indicar la ubicación de un recurso** (imagen, CSS, JS, otra página, etc.) dentro de un atributo como `href` o `src`.

---

## 🔹 1. Ruta Absoluta

Es una ruta que indica la dirección completa del recurso, incluyendo:

- Protocolo (`http://` o `https://`)
- Dominio
- Ruta completa del archivo

### ✅ Ejemplo:

```html
<a href="https://www.ejemplo.com/blog/articulo.html">Ver artículo</a>
<img src="https://www.ejemplo.com/img/logo.png">
```

### 📌 Características:

- No depende del archivo actual.
- Siempre apunta al mismo lugar.
- Se usa cuando el recurso está en otro dominio o servidor.

---

## 🔹 2. Ruta Relativa

Es una ruta que depende de la ubicación del archivo HTML actual.

No incluye dominio ni protocolo.

### 📂 Supongamos esta estructura:

```
/proyecto
│── index.html
│── /img
│     └── logo.png
│── /pages
      └── contacto.html
```

---

### ✅ Ejemplos de rutas relativas:

### 1️⃣ Archivo en la misma carpeta

```html
<a href="contacto.html">Contacto</a>
```

### 2️⃣ Entrar en una carpeta

```html
<img src="img/logo.png">
```

### 3️⃣ Subir un nivel (`..`)

Si estoy en `/pages/contacto.html` y quiero ir a `index.html`:

```html
<a href="../index.html">Inicio</a>
```

---

## 🔹 Diferencia clave

|Ruta absoluta|Ruta relativa|
|---|---|
|Dirección completa|Depende del archivo actual|
|Incluye dominio|No incluye dominio|
|No cambia según ubicación|Cambia según dónde esté el archivo|

---

## 🎯 Cuándo usar cada una

- 🔗 **Absoluta** → cuando enlazás a otra web.
    
- 📁 **Relativa** → cuando trabajás dentro del mismo proyecto.
    
