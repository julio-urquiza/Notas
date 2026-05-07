**dotenv** es una librería de Node.js que sirve para **cargar variables de entorno** desde un archivo llamado `.env` a `process.env`.

Se usa para **guardar configuraciones sensibles** o que cambian según el entorno, como:

- API keys
- passwords
- puertos
- URLs de base de datos
- modos (`dev`, `prod`)

---

## 📦 Instalación

```bash
npm install dotenv
```

---

## 🗂 Crear archivo `.env`

```env
PORT=3000
DB_PASSWORD=supersecreto
NODE_ENV=development
```

---

## 🔌 Cómo se usa

En tu archivo principal (por ejemplo `index.js`):

```js
require('dotenv').config();

console.log(process.env.PORT);        // 3000
console.log(process.env.DB_PASSWORD); // supersecreto
```

> `dotenv` carga las variables del archivo `.env` al objeto `process.env`.

---

## 😎 Ejemplo real usando Express

```js
require('dotenv').config();
const express = require('express');

const app = express();
const PORT = process.env.PORT || 8080;

app.get('/', (req, res) => {
  res.send('Servidor corriendo!');
});

app.listen(PORT, () => {
  console.log(`Servidor en http://localhost:${PORT}`);
});
```

---

## 🔒 Importante: No subir `.env` al repositorio

Agregalo a `.gitignore`:

```
.env
```

Así evitás exponer contraseñas en GitHub.

---

## 🧠 ¿Por qué usar dotenv?

|Problema sin dotenv|Solución con dotenv|
|---|---|
|Claves escritas “hardcodeadas” en el código|Variables externas y seguras|
|Configuración distinta en dev/prod|Cambiás `.env` según el entorno|
|Dificultad para compartir datos sensibles|Se pasa `.env.example` sin claves reales|

---

## 🏁 Resumen

- **dotenv** carga variables desde un archivo `.env` a `process.env`.
- Se usa para **configuración** y **datos sensibles**.
- Previene **exponer claves** en tu código.
- Muy común en apps Node, Express, Nest, Next, etc.

---
Sí, **se puede usar variables de entorno sin `dotenv`**, pero depende de **cómo las quieras cargar**.

---

## ✅ 1. **Si ya están definidas en el sistema**

No necesitás `dotenv`.

Ejemplo en Linux/Mac:

```bash
PORT=3000 node index.js
```

Ejemplo en Windows (PowerShell):

```bash
$env:PORT="3000"; node index.js
```

Y en tu código Node:

```js
console.log(process.env.PORT);
```

---

## ✅ 2. **Node.js 20+ permite cargar `.env` sin dotenv**

Desde **Node v20** existe el flag:

```bash
node --env-file=.env index.js
```

Tu `.env`:

```
PORT=3000
```

Tu código:

```js
console.log(process.env.PORT);
```

👉 Esto reemplaza a `dotenv` en entornos modernos.

---

## ✅ 3. **Docker / Servicios en la nube**

En contenedores y servidores puedes pasar variables sin `.env`, por ejemplo:

```bash
docker run -e PORT=3000 mi-app
```

---

## ✅ 4. **Pero si querés cargar `.env` automáticamente en desarrollo…**

Ahí sí conviene `dotenv`, porque:

- No tenés que setear variables manualmente cada vez
- Funciona igual en Windows, Mac y Linux
- Es más cómodo para proyectos en equipo

---

## 🧠 Resumen claro

|Forma|¿Carga `.env`?|¿Requiere dotenv?|Ideal para|
|---|---|---|---|
|Variables exportadas en el sistema|❌ No|❌ No|Producción / Servidores|
|`node --env-file=.env` (Node 20+)|✅ Sí|❌ No|Proyectos modernos|
|`require('dotenv').config()`|✅ Sí|✅ Sí|Desarrollo local / compatibilidad|

---

## 🎯 Conclusión

- **Sí**, podés usar variables de entorno sin `dotenv`.
- Si estás en **Node 20+**, podés usar:
   ```bash
    node --env-file=.env server.js
    ```
- `dotenv` solo es necesario cuando querés **automatizar la carga de `.env` en desarrollo** o cuando estás en versiones más viejas de Node.

---
