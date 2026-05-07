`helmet` en **npm** es un **middleware de seguridad para aplicaciones Express (Node.js)**.

Su objetivo principal es **proteger tu aplicación web configurando automáticamente cabeceras HTTP seguras**, reduciendo riesgos de ataques comunes como:

- **Cross-Site Scripting (XSS)**
- **Clickjacking**
- **Inyección de contenido en cabeceras**
- **Exposición de información sensible en cabeceras HTTP por defecto**

---

### ¿Cómo funciona?

Cuando lo usas en una aplicación con **Express**, Helmet ajusta varias cabeceras de seguridad, por ejemplo:

- `Content-Security-Policy` → controla qué recursos puede cargar el navegador.
- `X-Frame-Options` → evita que tu sitio sea embebido en iframes (protección contra clickjacking).
- `Strict-Transport-Security` → fuerza el uso de HTTPS.
- `X-Content-Type-Options` → evita que el navegador interprete mal tipos de archivo.
- `Referrer-Policy` → controla qué información del _referer_ se envía en las peticiones.

---

### Instalación

```bash
npm install helmet
```

---

### Uso básico en Express

```js
import express from "express";
import helmet from "helmet";

const app = express();

// Activar Helmet
app.use(helmet());

app.get("/", (req, res) => {
  res.send("App segura con Helmet 🚀");
});

app.listen(3000, () => {
  console.log("Servidor en http://localhost:3000");
});
```

Con esta configuración, ya aplicas un conjunto de cabeceras seguras por defecto.  
Si quieres, puedes configurar Helmet para activar o desactivar ciertas políticas:

```js
app.use(
  helmet({
    contentSecurityPolicy: false, // Desactiva CSP si causa conflictos
  })
);
```

---