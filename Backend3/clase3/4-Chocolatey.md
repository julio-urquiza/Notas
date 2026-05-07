**Chocolatey** es un **gestor de paquetes para Windows**, muy parecido a **apt** en Linux o **Homebrew** en macOS. 🍫

---
### 🔹 Para qué sirve

- Permite **instalar, actualizar y desinstalar programas** desde la línea de comandos.
- Automatiza procesos que normalmente harías manualmente (descargar instalador, clickear “Next”, configurar rutas).
- Muy útil para desarrolladores que quieren configurar entornos rápidamente.

---

### 🔹 Ejemplos de uso

1. Instalar **Node.js**:

```powershell
choco install nodejs-lts -y
```

2. Instalar **NGINX**:

```powershell
choco install nginx -y
```

3. Actualizar un programa:

```powershell
choco upgrade nodejs -y
```

4. Desinstalar un programa:

```powershell
choco uninstall nginx -y
```

---

### 🔹 Ventajas

- Rápido y automatizado.
- Permite tener **versiones específicas** de software.
- Funciona bien con scripts de instalación para proyectos o servidores.

---

En resumen: **Chocolatey te permite instalar y gestionar software en Windows de forma simple desde la terminal**, sin tener que descargar manualmente cada instalador.

Si querés, puedo explicarte **cómo usar Chocolatey para instalar NGINX y levantar un proyecto Node.js completo en Windows** paso a paso.
# Instalación
---

## 1️⃣ Abrir PowerShell como administrador

1. Presioná **Windows** en tu teclado y escribí `PowerShell`.
2. Hacé **clic derecho** sobre **Windows PowerShell** → **Ejecutar como administrador**.
3. Confirmá la ventana de control de cuentas de usuario (UAC) haciendo clic en **Sí**.

> ⚠️ Necesitas abrirlo **como administrador**, si no la instalación fallará.

---

## 2️⃣ Ejecutar el script de instalación

En la ventana de PowerShell admin, copiá y pegá el siguiente comando y presioná **Enter**:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = `
[System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

- Esto descarga e instala Chocolatey automáticamente.
- El `Set-ExecutionPolicy Bypass` permite ejecutar scripts temporalmente.

---

## 3️⃣ Verificar la instalación

Cerrá la terminal y abrila de nuevo como administrador (para que tome las variables de entorno).  
Luego ejecutá:

```powershell
choco -v
```

- Si devuelve un número de versión, ✅ Chocolatey ya está instalado correctamente.

---
