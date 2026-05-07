**NVM** significa **Node Version Manager**.

Es una herramienta que te permite **instalar, gestionar y cambiar fácilmente entre diferentes versiones de Node.js** en tu computadora.

🔑 Con NVM puedes:

- Instalar varias versiones de Node.js en paralelo.
- Cambiar rápidamente de una versión a otra (`nvm use 18`, `nvm use 20`, etc.).
- Definir una versión por defecto para nuevos shells.
- Probar tus proyectos con distintas versiones de Node sin complicarte.

👉 Ejemplo de uso básico:

```bash
# Instalar una versión específica de Node.js
nvm install 20

# Usar esa versión
nvm use 20

# Ver la versión actual en uso
node -v

# Ver todas las versiones instaladas
nvm ls
```

Esto es muy útil porque muchas veces los proyectos requieren versiones distintas de Node.js, y con NVM no necesitas reinstalar manualmente.

---
## 🔧 Uso básico de NVM

### 1. Ver las versiones de Node disponibles

```bash
nvm ls-remote
```

Esto lista todas las versiones oficiales de Node.js que podés instalar.

---

### 2. Instalar una versión específica

```bash
nvm install 20
```

👉 Esto instala Node.js **v20**.  
También podés instalar la última versión estable con:

```bash
nvm install node
```

---

### 3. Ver qué versiones tenés instaladas

```bash
nvm ls
```

Ejemplo de salida:

```
->     v20.5.0
       v18.17.0
default -> 18 (-> v18.17.0)
```

El `->` indica la versión que estás usando actualmente.

---

### 4. Cambiar de versión

```bash
nvm use 18
```

Ahora tu terminal usará Node.js **v18**.

---

### 5. Definir una versión por defecto

```bash
nvm alias default 20
```

Cada vez que abras una nueva terminal, se usará la versión **20**.

---

### 6. Ejecutar un comando con una versión específica (sin cambiar globalmente)

```bash
nvm run 18 app.js
```

Ejecuta `app.js` con Node v18 aunque estés usando otra versión por defecto.

---

👉 Ejemplo de flujo típico:

```bash
nvm install 18
nvm install 20
nvm use 20
node -v   # muestra v20.x.x
nvm use 18
node -v   # muestra v18.x.x
```

---

## 🪟 Paso a paso: instalar y usar NVM en Windows

### 1. Desinstalar Node.js si lo tenés instalado

- Abrí **Panel de control > Programas > Desinstalar un programa**
- Eliminá **Node.js**
- Si quedó la carpeta `C:\Program Files\nodejs\`, borrala manualmente

⚠️ Esto es importante para evitar conflictos de rutas.

---
### 2. Instalar NVM para Windows

1. Entrá al repo oficial:  
    👉 [nvm-windows releases](https://github.com/coreybutler/nvm-windows/releases)
2. Descargá el instalador `nvm-setup.exe` (versión más reciente).
3. Ejecutá el instalador:
    - Elegí una carpeta para **NVM** (ej: `C:\nvm`)
    - Elegí una carpeta para **Node.js** (ej: `C:\Program Files\nodejs`)
    - Terminar instalación.

---
### 3. Probar NVM

Abrí **PowerShell** o **CMD** y escribí:

```powershell
nvm version
```

👉 Si te muestra un número (ej: `1.1.12`), ya está instalado.

---

### 4. Instalar Node.js con NVM

Ahora podés instalar Node a través de NVM:

```powershell
nvm install 20.5.0   # instala esa versión exacta
nvm install latest   # instala la última versión estable
```

---

### 5. Usar una versión

```powershell
nvm use 20.5.0
```

Eso activa Node.js v20.5.0 en tu terminal.

Verificá:

```powershell
node -v
npm -v
```

---

### 6. Listar versiones instaladas

```powershell
nvm list
```

---

👉 Flujo típico:

```powershell
nvm install 18.17.0
nvm install 20.5.0
nvm use 20.5.0   # ahora usás v20
node -v          # muestra v20.5.0
nvm use 18.17.0  # cambiás a v18
node -v          # muestra v18.17.0
```

---

¿Querés que te arme una **mini guía con capturas de pantalla** para que veas el paso a paso visual en Windows, o te alcanza con los comandos?