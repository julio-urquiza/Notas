Yarn es un **administrador de paquetes** para proyectos de JavaScript. Es similar a **npm** (Node Package Manager), y se usa para instalar, actualizar y gestionar las dependencias de tu proyecto, es decir, las librerías o módulos que tu aplicación necesita para funcionar.

Algunas cosas clave sobre Yarn:

1. **Rápido y confiable:** Yarn descarga paquetes en paralelo, lo que hace que la instalación sea más rápida que npm en muchas situaciones.

2. **Lockfile:** Yarn crea un archivo llamado `yarn.lock` que asegura que todos los desarrolladores de un proyecto instalen exactamente las mismas versiones de las dependencias, evitando errores por diferencias de versión.

3. **Workspaces:** Permite manejar proyectos monorepo (varios paquetes dentro de un mismo repositorio) de manera más eficiente.

4. **Comandos básicos:**
    - `yarn init` → Inicializa un proyecto con Yarn.
    - `yarn add [paquete]` → Instala un paquete y lo agrega a las dependencias.
    - `yarn remove [paquete]` → Elimina un paquete.
    - `yarn install` → Instala todas las dependencias listadas en `package.json`.

---
# Instalación

Para instalar **Yarn** en Windows, Mac o Linux hay varias formas. Te explico las más comunes:

---

### **1. Usando npm (ya que tienes Node.js)**

Si ya tienes Node.js instalado, puedes instalar Yarn globalmente con:

```bash
npm install -g yarn
```

Luego, verifica la instalación con:

```bash
yarn --version
```

Si te muestra un número de versión, ya está listo.

---

### **2. Usando Chocolatey (en Windows)**

Si tienes **Chocolatey**, puedes instalar Yarn con:

```powershell
choco install yarn
```

Y luego verificar con:

```powershell
yarn --version
```

---

### **3. Usando instalador oficial**

También puedes descargar el instalador oficial para Windows o Mac desde la página de Yarn:

🔗 [https://classic.yarnpkg.com/lang/en/docs/install](https://classic.yarnpkg.com/lang/en/docs/install)

Sigue las instrucciones según tu sistema operativo.

---

💡 **Tip:** No necesitas instalar Node.js aparte si instalas Yarn desde su instalador oficial, porque viene con su propia versión de Node.js.
