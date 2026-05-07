# ¿Qué significa “inicializar un proyecto Express”?

Significa:

1. Crear un proyecto Node.js
2. Instalar Express
3. Configurar la estructura básica
4. Levantar un servidor HTTP
5. Preparar el proyecto para desarrollar endpoints

---

# Paso 1 — Crear la carpeta del proyecto

```bash
mkdir backend
cd backend
```

## ¿Qué hace esto?

* `mkdir` crea una carpeta
* `cd` entra a esa carpeta

Acá va a vivir todo el backend.

---

# Paso 2 — Inicializar Node.js

```bash
npm init -y
```

## ¿Qué hace?

Crea el archivo:

```txt
package.json
```

Ese archivo es el “documento de identidad” del proyecto.

Contiene:

* nombre
* versión
* scripts
* dependencias

---

# Package.json

Podés mostrar algo así:

```json
{
  "name": "backend",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",                     //Importante
  "scripts": {                          //Importante
    "dev": "node --watch src/server.js", 
    "start": "node src/server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "packageManager": "pnpm@10.18.2",
  "dependencies": {                     //Importante
    "cors": "^2.8.6",
    "express": "^5.2.1"
  }
}
```

## Idea clave

Node usa este archivo para:

* saber qué librerías instalar
* cómo ejecutar el proyecto

---

# Paso 3 — Instalar Express

```bash
npm install express
```

## ¿Qué hace?

Descarga Express desde npm.

## Explicar npm

npm es el gestor de paquetes de Node.js.

Sirve para instalar librerías.

---

# Qué pasa después

Se crean:

```txt
node_modules/
package-lock.json
```

## node_modules

Contiene todas las dependencias del proyecto.

---

# Paso 4 — Crear la estructura inicial

Ejemplo simple:

```txt
backend/
│
├── src/
│   ├── routes/
│   ├── controllers/
│   ├── services/
│   ├── app.js
│   └── server.js
│
├── package.json
```

---

# Paso 5 — Crear el servidor

## server.js

```js
import app from "./app.js"

const PORT = 3000;

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

---

# Explicar app.listen()

## ¿Qué hace?

Hace que el servidor quede “escuchando” requests HTTP.

---

# Paso 6 — Crear la aplicación Express

## app.js

```js
import express from "express"

const app = express();

app.use(express.json());

app.get("/", (req, res) => {
  res.send("API funcionando");
});

export default app
```

---

# Explicar cada línea

## Importar express

```js
import express from "express"
```

Importa la librería.

---

## Crear la app

```js
const app = express();
```

Crea la aplicación Express.

---

## Middleware JSON

```js
app.use(express.json());
```

Permite recibir JSON en requests.

Ejemplo:

```json
{
  "name": "Julio"
}
```

---

## Crear endpoint

```js
app.get("/", ...)
```

Define una ruta GET.

---

# Explicar req y res

| Objeto | Significado           |
| ------ | --------------------- |
| req    | Request del cliente   |
| res    | Response del servidor |

---

# Paso 7 — Ejecutar el servidor

```bash
node src/server.js
```

---

# Resultado

Si abrís:

```txt
http://localhost:3000
```

Vas a ver:

```txt
API funcionando
```

---

# Scripts

```json
"scripts": {
  "dev": "node --watch src/server.js",
  "start": "node src/server.js"
}
```

---
## ¿Para qué sirve?

```json
"dev": "node --watch src/server.js",
```
Inicia y reinicia automáticamente el servidor cuando cambia el código. Su uso está orientado al desarrollo

```json
"start": "node src/server.js"
```
Inicia servidor, es util en etapas de deployment. Por ahora no se usa 

---


# Ejecutar en desarrollo
En la consola:
```bash
npm run dev
```

---

# Importante

## Diferencia entre:

| Concepto | Función                              |
| -------- | ------------------------------------ |
| Node.js  | Entorno para ejecutar JavaScript     |
| npm      | Gestor de paquetes                   |
| Express  | Framework web                        |

---

# Flujo completo

```txt
Cliente → HTTP Request → Express → Route → Controller → Response
```

---


## Node.js

“Permite ejecutar JavaScript fuera del navegador.”

---

## Express

“Nos ayuda a crear servidores y APIs de forma sencilla.”

---

## Endpoint

“Es una URL que el frontend puede consumir.”

Ejemplo:

```txt
GET /users
POST /login
```

---

# Ejemplo final completo

## app.js

```js
const express = require("express");

const app = express();

app.use(express.json());

app.get("/", (req, res) => {
  res.json({
    message: "Servidor funcionando"
  });
});

module.exports = app;
```

---

## server.js

```js
const app = require("./app");

const PORT = 3000;

app.listen(PORT, () => {
  console.log(`Servidor corriendo en puerto ${PORT}`);
});
```
