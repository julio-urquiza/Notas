	**Winston** es una librería de **Node.js** muy popular para **logging** (registro de eventos, errores y mensajes en una aplicación).

Sirve para que tu aplicación guarde información útil sobre lo que está ocurriendo, como:

- Errores (por ejemplo, cuando una API falla).
- Advertencias (warnings).
- Información de uso (logs de accesos, consultas a la base de datos, etc.).
- Debugging (mensajes de depuración).

---

### 🔑 Características principales de Winston:

1. **Múltiples transportes**: puedes enviar logs a diferentes lugares al mismo tiempo (consola, archivo, base de datos, servicios externos como Loggly o Elasticsearch).
2. **Niveles de log**: por defecto tiene niveles como `error`, `warn`, `info`, `http`, `debug`, que puedes personalizar.
3. **Formato flexible**: permite dar formato a los mensajes (ej: JSON, texto plano, con colores).
4. **Asíncrono**: funciona bien en aplicaciones Node.js de alto rendimiento.
5. **Extensible**: puedes crear tus propios transportes.

---

### 📌 Ejemplo básico en Node.js

```js
const { createLogger, transports, format } = require('winston');

const logger = createLogger({
  level: 'info', // nivel mínimo de log
  format: format.combine(
    format.timestamp(),
    format.json()
  ),
  transports: [
    new transports.Console(),             // Muestra en consola
    new transports.File({ filename: 'app.log' }) // Guarda en archivo
  ]
});

// Ejemplo de uso
logger.info("Servidor iniciado correctamente");
logger.warn("Advertencia: conexión lenta");
logger.error("Error: no se pudo conectar a la base de datos");
```

---

👉 En resumen: **Winston es como un sistema centralizado de logs** para que tu aplicación pueda registrar lo que pasa y luego puedas depurar problemas o analizar el comportamiento.

---

## 📌 Middleware con Winston en Express

### 1. Configurar `logger.js`


```js
// logger.js
const { createLogger, format, transports } = require("winston");

const logger = createLogger({
  level: "info",
  format: format.combine(
    format.timestamp({ format: "YYYY-MM-DD HH:mm:ss" }),
    format.printf(({ timestamp, level, message }) => {
      return `[${timestamp}] ${level.toUpperCase()}: ${message}`;
    })
  ),
  transports: [
    new transports.Console(),
    new transports.File({ filename: "logs/app.log" })
  ]
});

module.exports = logger;
```

---

### 2. Usarlo en Express

```js
// server.js
const express = require("express");
const logger = require("./logger");

const app = express();

// Middleware para registrar cada request
app.use((req, res, next) => {
  const start = Date.now();

  res.on("finish", () => {
    const duration = Date.now() - start;
    logger.info(`${req.method} ${req.originalUrl} ${res.statusCode} - ${duration}ms`);
  });

  next();
});

// Ruta de ejemplo
app.get("/", (req, res) => {
  logger.info("Ruta / fue llamada");
  res.send("Hola con Winston sin Morgan 🚀");
});

// Middleware de manejo de errores
app.use((err, req, res, next) => {
  logger.error(`Error en ${req.method} ${req.originalUrl}: ${err.message}`);
  res.status(500).send("Algo salió mal 😢");
});

app.listen(3000, () => {
  logger.info("Servidor escuchando en http://localhost:3000");
});
```

---

### 🔍 Qué hace este código:

- Crea un **middleware personalizado** que mide el tiempo de respuesta y guarda:
    - Método HTTP (`GET`, `POST`, etc.)
    - URL solicitada (`/`, `/api/...`)
    - Código de estado (`200`, `404`, `500`, etc.)
    - Tiempo de respuesta (`ms`)
- Guarda todo con Winston tanto en consola como en el archivo `logs/app.log`.
- Maneja errores con `logger.error`.

---

###  Otro ejemplo:

![[Pasted image 20250831173430.png]]![[Pasted image 20250831173521.png]]