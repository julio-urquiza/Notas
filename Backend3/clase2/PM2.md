**PM2** (Process Manager 2) es una **herramienta de administración de procesos para Node.js**, que te permite **ejecutar, monitorear y mantener en línea** tus aplicaciones Node de forma profesional, especialmente en **entornos de producción**.

---

## 🚀 ¿Qué hace PM2?

PM2 mantiene tus apps **corriendo siempre**, incluso si se caen, y además ofrece funciones avanzadas como:

- **Reinicio automático** si tu app se detiene o falla
- **Balanceo de carga (cluster mode)**
- **Logs centralizados**
- **Monitoreo en tiempo real**
- **Configuraciones persistentes (ecosystem.config.js)**
- **Deploy automático**

---

## 🧩 Instalación

```bash
npm install -g pm2
```

Con eso lo instalás de forma global para poder usar el comando `pm2` en cualquier proyecto.

---

## ⚙️ Uso básico

Ejemplo con un archivo `server.js`:

```bash
pm2 start server.js
```

Esto:

- Inicia tu aplicación
- Le asigna un nombre automático (por ejemplo, `server`)
- La mantiene activa aunque cierres la terminal o se caiga

Podés ver el estado de todas tus apps con:

```bash
pm2 list
```

Y ver logs en vivo:

```bash
pm2 logs
```

---

## 🧠 Modos de ejecución

### 🔹 Modo normal

Ejecuta un solo proceso:

```bash
pm2 start app.js
```

### 🔹 Modo clúster (para usar todos los núcleos del CPU)

```bash
pm2 start app.js -i max
```

Esto crea **varias instancias** de tu aplicación y las balancea automáticamente.  
Ideal para aprovechar CPUs multinúcleo.

---

## 🧾 Guardar la configuración

Para mantener tus procesos activos incluso tras un reinicio del servidor:

```bash
pm2 save
pm2 startup
```

El primer comando guarda los procesos actuales.  
El segundo crea el script necesario para iniciarlos automáticamente al arrancar el sistema operativo.

---

## 🧩 Ecosystem File

Podés crear un archivo de configuración llamado `ecosystem.config.js`:

```js
export default {
  apps: [
    {
      name: 'api',
      script: './server.js',
      instances: 'max',
      exec_mode: 'cluster',
      env: {
        NODE_ENV: 'development',
      },
      env_production: {
        NODE_ENV: 'production',
      }
    }
  ]
};
```

Y levantarlo con:

```bash
pm2 start ecosystem.config.js --env production
```

---

## 📊 Monitoreo

Podés monitorear tus procesos:

```bash
pm2 monit
```

Esto abre una consola interactiva que muestra uso de CPU, memoria, uptime, etc.  
También existe una versión web (PM2 Plus / Keymetrics) para monitoreo remoto.

---

## 🧹 Otros comandos útiles

|Comando|Descripción|
|---|---|
|`pm2 stop all`|Detiene todas las apps|
|`pm2 restart all`|Reinicia todas|
|`pm2 delete all`|Elimina todas del gestor|
|`pm2 reload all`|Reinicia sin downtime (útil en producción)|

---

## 💡 Ventajas

✅ Mantiene tu app viva 24/7  
✅ Reinicia automáticamente en caso de errores  
✅ Facilita escalar con múltiples núcleos  
✅ Facilita despliegues y monitoreo  
✅ Compatible con Docker y Nginx como proxy inverso

---
