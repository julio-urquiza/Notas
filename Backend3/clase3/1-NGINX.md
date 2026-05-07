**NGINX** es un **servidor web** de alto rendimiento que también puede funcionar como:

- **Proxy inverso** (reverse proxy)
- **Balanceador de carga** (load balancer)
- **Servidor de correo (IMAP/POP3/SMTP proxy)**

Se diseñó originalmente para ser **rápido, ligero y eficiente en el uso de recursos**, especialmente para manejar muchas conexiones concurrentes.

### Sus usos principales:

1. **Servidor web** → Sirve archivos estáticos (HTML, CSS, imágenes, etc.) de manera muy eficiente.
2. **Proxy inverso** → Recibe las peticiones de los clientes y las redirige a otros servidores de aplicaciones (por ejemplo, Node.js, .NET, Java, etc.).
3. **Balanceo de carga** → Distribuye el tráfico entre varios servidores para mejorar rendimiento y disponibilidad.
4. **Seguridad y caching** → Se usa para cachear contenido y proteger aplicaciones backend de accesos directos.
### Comparación rápida:

- **Apache**: muy popular, flexible, pero más pesado en conexiones concurrentes.
- **NGINX**: más rápido en alto volumen de tráfico, muy usado en sitios grandes como Netflix, GitHub o Dropbox.

👉 En resumen: **NGINX es un servidor web y proxy inverso muy rápido y eficiente, usado para servir contenido y gestionar tráfico en aplicaciones web modernas.**

# Instalación

---

## 🔹 Paso 1: Descargar NGINX portátil

1. Andá a la web oficial:  
    👉 [https://nginx.org/en/download.html](https://nginx.org/en/download.html)
2. Descargá la versión **Stable Windows** (`nginx-x.x.x.zip`).
3. Extraé el ZIP dentro de tu proyecto, por ejemplo:

```
C:\miapp\nginx
```

Dentro de esa carpeta vas a ver: `conf`, `html`, `logs`, `temp`.

---

## 🔹 Paso 2: Configurar NGINX para tu proyecto

1. Abrí el archivo de configuración:

```
C:\miapp\nginx\conf\nginx.conf
```

2. Agregá dentro de `http { ... }` un bloque `server` que apunte a tu app Node.js (ejemplo puerto 3000):

```nginx
server {
    listen       80;
    server_name  localhost;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

3. Guardá el archivo.

---

## 🔹 Paso 3: Levantar NGINX para tu proyecto

1. Abrí PowerShell en la carpeta del proyecto:

```powershell
cd C:\miapp\nginx
```

2. Ejecutá NGINX:

```powershell
.\nginx.exe
```

- Esto levanta NGINX **solo para este proyecto**.
- Para recargar cambios:

```powershell
.\nginx.exe -s reload
```

- Para cerrar NGINX:

```powershell
.\nginx.exe -s quit
```

---

## 🔹 Paso 4: Probar tu proyecto Node.js

1. Ejecutá tu app Node.js (por ejemplo con Express) en el puerto 3000:

```powershell
cd C:\miapp
node server.js
```

2. Abrí el navegador y visitá:

```
http://localhost
```

✅ Ahora tu proyecto Node.js está servido **a través de NGINX portátil**, sin afectar otros proyectos.

---

💡 **Ventajas de NGINX portátil por proyecto**:

- No se instala globalmente → no modifica el sistema.
- Podés tener **distintas versiones de NGINX** por proyecto.
- Ideal para desarrollo o pruebas locales.

---