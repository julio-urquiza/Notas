Docker es una **plataforma de virtualización ligera** que permite crear, ejecutar y administrar aplicaciones dentro de **contenedores**.

🔹 **Un contenedor** es como una “cajita” que incluye todo lo necesario para que una aplicación funcione:

- Código fuente
- Librerías
- Dependencias
- Configuraciones

De esta forma, no importa en qué sistema operativo o computadora ejecutes el contenedor: siempre se comportará igual.

---

### 📦 Diferencia con una máquina virtual

- **Máquina virtual (VM):** simula un sistema operativo completo, con kernel y recursos dedicados. Consume más memoria y CPU.
- **Contenedor (Docker):** comparte el kernel del sistema anfitrión, es más ligero y arranca en segundos.

---

### 🚀 ¿Para qué se usa Docker?

1. **Portabilidad:** la aplicación corre igual en desarrollo, testing y producción.
2. **Aislamiento:** cada contenedor es independiente, evitando conflictos de versiones o dependencias.
3. **Escalabilidad:** se pueden levantar múltiples instancias fácilmente.
4. **Integración con DevOps:** funciona muy bien con CI/CD, Kubernetes, etc.

---

## 🔹 1. Instalación de Docker

### En **Windows 10/11**

1. Descarga **Docker Desktop** desde la página oficial:  
    👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Ejecuta el instalador y sigue los pasos.
3. Una vez instalado, abre Docker Desktop (te pedirá activar **WSL 2** o **Hyper-V**, depende de tu sistema).
4. Para verificar que funciona, abre **PowerShell** y ejecuta:
   ```powershell
	 docker --version
    ```
    Si ves la versión, está bien instalado ✅

---

## 🔹 2. Cómo usar Docker (básico)

### a) Probar con "Hello World"

Ejecuta:

```bash
docker run hello-world
```

👉 Esto descarga una imagen y la ejecuta dentro de un contenedor.

---

### b) Descargar y correr una imagen (ejemplo con NGINX)

```bash
docker run -d -p 8080:80 nginx
```

- `-d` → lo ejecuta en segundo plano.
- `-p 8080:80` → expone el puerto 80 del contenedor en el 8080 de tu PC.  
    👉 Abre en navegador: `http://localhost:8080`

---

### c) Ver contenedores activos

```bash
docker ps
```

### d) Parar un contenedor

```bash
docker stop <id_contenedor>
```

### e) Eliminar contenedores e imágenes

```bash
docker rm <id_contenedor>
docker rmi <nombre_imagen>
```

---

## 🔹 3. Crear tu propia app con Docker

Ejemplo: aplicación **Node.js**

1. Crear `Dockerfile`:

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

2. Construir la imagen:

```bash
docker build -t mi-app .
```

3. Ejecutar:

```bash
docker run -p 3000:3000 mi-app
```

Tu aplicación estará disponible en `http://localhost:3000`.

---