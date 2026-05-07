La librería **`http-proxy-middleware`** es una herramienta muy útil en el ecosistema de **Node.js** y **Express** (y también en proyectos React o Vite durante desarrollo).  
Sirve para **crear proxies HTTP directamente desde tu aplicación Node**, sin necesidad de configurar un proxy inverso externo como Nginx.

---

## 🧠 ¿Qué es `http-proxy-middleware`?

Es un **middleware** (intermediario) que se usa en un servidor Express o en el entorno de desarrollo de React para **redirigir peticiones** a otro servidor o API.

👉 En pocas palabras:

> Permite que tu servidor Node o tu frontend actúe como un **proxy**, reenviando las peticiones HTTP a otro destino.

---

## 🧩 ¿Por qué se usa?

Principalmente para:

1. **Evitar problemas de CORS** (cuando tu frontend y tu backend están en dominios distintos).
2. **Unificar rutas** durante desarrollo.
3. **Redirigir tráfico** a diferentes microservicios.
4. **Agregar headers, logs o filtros personalizados** antes de enviar la petición al destino real.

---

## ⚙️ Instalación

```bash
npm install http-proxy-middleware
```

---

## 🚀 Uso básico con Express

```js
import express from 'express';
import { createProxyMiddleware } from 'http-proxy-middleware';

const app = express();

// 🔹 Cualquier petición que empiece con /api se redirige al servidor destino
app.use('/api', createProxyMiddleware({
  target: 'https://jsonplaceholder.typicode.com', // Servidor destino
  changeOrigin: true,  // Cambia el origen del host a coincidir con el destino
}));

app.listen(3000, () => {
  console.log('Servidor en http://localhost:3000');
});
```

👉 Ahora, si accedés a:

```
http://localhost:3000/api/users
```

El middleware **redirige internamente** esa solicitud a:

```
https://jsonplaceholder.typicode.com/users
```

Y devuelve la respuesta al cliente como si viniera de tu propio servidor.

---

## ⚙️ Explicación de las opciones más comunes

|Opción|Descripción|
|---|---|
|`target`|URL del servidor destino (donde se enviará la petición).|
|`changeOrigin`|Cambia el encabezado `Host` de la petición al del destino. Es útil para evitar bloqueos por CORS.|
|`pathRewrite`|Permite modificar la ruta antes de reenviarla.|
|`onProxyReq`|Permite interceptar la solicitud antes de enviarla (por ejemplo, agregar headers).|
|`onProxyRes`|Permite modificar la respuesta antes de devolverla al cliente.|
|`secure`|Si es `false`, permite conectar a servidores HTTPS con certificados no válidos (solo en desarrollo).|

---

## 🧩 Ejemplo con `pathRewrite`

```js
app.use('/api', createProxyMiddleware({
  target: 'https://jsonplaceholder.typicode.com',
  changeOrigin: true,
  pathRewrite: {
    '^/api': '', // 🔹 elimina el prefijo /api antes de enviar
  },
}));
```

👉 `GET /api/posts` → se convierte en `GET https://jsonplaceholder.typicode.com/posts`

---

## 💻 Ejemplo con React (vite o CRA)

En proyectos **React**, también se usa en el archivo `vite.config.js` o `setupProxy.js` para evitar CORS durante desarrollo.

**Ejemplo (Vite):**

```js
export default {
  server: {
    proxy: {
      '/api': {
        target: 'http://localhost:4000',
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, ''),
      },
    },
  },
};
```

---

## 🛠️ Casos de uso reales

- 🌐 Un frontend React que hace peticiones a una API Node.
- 🧩 Un gateway API que enruta tráfico a microservicios distintos.
- 🔐 Añadir autenticación o logs sin tocar los servidores backend.
- 🧪 Simular un entorno productivo localmente.

---

## 🚀 En resumen

|Concepto|Descripción|
|---|---|
|Nombre|`http-proxy-middleware`|
|Tipo|Middleware para Express (y React dev server)|
|Uso principal|Redirigir peticiones HTTP a otro servidor (proxy)|
|Beneficios|Evita CORS, permite reescritura de rutas, agrega seguridad y flexibilidad|
|Alternativa|Usar un proxy inverso externo como Nginx o Traefik|

---
