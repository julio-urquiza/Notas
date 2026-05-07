## 🧠 ¿Qué hace exactamente?

Cuando un servidor responde a una petición HTTP (por ejemplo, enviando HTML, JSON, imágenes, etc.), **envía texto sin comprimir por defecto**.  
Eso hace que las respuestas pesen más y tarden más en llegar.

La librería **`compression`** usa el algoritmo **Gzip** (y a veces Brotli, si el cliente lo soporta) para **comprimir esos datos** en el servidor y **enviarlos comprimidos** al navegador.

El navegador luego **los descomprime automáticamente** antes de mostrarlos, sin que tengas que hacer nada.

---

## ⚙️ Instalación

```bash
npm install compression
```

---

## 🚀 Uso básico con Express

```js
import express from 'express';
import compression from 'compression';

const app = express();

// 🔹 Activás la compresión en todas las respuestas
app.use(compression());

app.get('/', (req, res) => {
  res.send('Hola mundo comprimido 😄');
});

app.listen(3000, () => console.log('Servidor en http://localhost:3000'));
```

➡️ Con eso, **todas las respuestas** que salgan del servidor serán comprimidas si el cliente (navegador o API consumer) lo soporta.

---

## 🧩 ¿Cómo funciona internamente?

1. El cliente (por ejemplo Chrome o Postman) manda en su encabezado:
   ```
    Accept-Encoding: gzip, deflate, br
    ```
2. `compression` detecta ese encabezado y aplica el método de compresión más adecuado (normalmente **gzip**).
3. El servidor agrega este encabezado a la respuesta:
   ```
    Content-Encoding: gzip
    ```
4. El navegador descomprime automáticamente la respuesta antes de mostrarla.

---

## ⚙️ Opciones comunes

Podés personalizar su comportamiento:

```js
app.use(compression({
  level: 6,            // Nivel de compresión (0–9) → 9 = máximo
  threshold: 1024,     // Solo comprime respuestas mayores a 1KB
  filter: (req, res) => {
    if (req.headers['x-no-compression']) {
      return false;    // Permite desactivar compresión manualmente
    }
    return compression.filter(req, res);
  }
}));
```

---

## 📈 Beneficios

✅ **Reduce el tamaño de las respuestas** (a veces hasta 70–80%)  
✅ **Acelera el tiempo de carga** de tu API o sitio web  
✅ **Reduce consumo de ancho de banda**  
✅ **Totalmente transparente** para el cliente (no requiere cambios del lado del navegador)

---

## ⚠️ Cuándo no conviene usarlo

- En archivos ya comprimidos (por ejemplo `.zip`, `.jpg`, `.png`, `.mp4`), porque **no gana nada y consume CPU**.
- En APIs internas o microservicios dentro de una misma red local (la compresión puede ser un gasto innecesario).

---
