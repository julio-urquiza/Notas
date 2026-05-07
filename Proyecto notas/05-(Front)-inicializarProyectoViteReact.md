## ¿Qué es Vite?

Vite es una herramienta que permite crear proyectos frontend modernos rápidamente.
Con React se usa para levantar un entorno de desarrollo con hot reload, bundling y configuración inicial ya preparada.

---

# Inicializar un proyecto React con Vite

## 1. Verificar Node.js

Primero necesitás tener instalado:

* Node.js
* npm (viene incluido con Node)

Podés verificarlo con:

```bash
node -v
npm -v
```

---

## 2. Crear el proyecto

Se ejecuta este comando:

```bash
npm create vite@latest
```

Eso descarga el generador oficial de proyectos de Vite.

---

## 3. Configurar el proyecto

El asistente te va a preguntar:

### Nombre del proyecto

```bash
✔ Project name: › mi-app
```

Ese será el nombre de la carpeta.

---

### Framework

Elegís:

```bash
React
```

---

### Variant

Elegís:

```bash
JavaScript
```
---

## 3.5 Nuevas versiones

En nuevas versiones antiguas de vite era necesario hacer los pasos 4, 5 y 6, actualmente ya no es necesario, ya vite lo hace automáticamente. Igualmente es util saber lo que hace

## 4. Entrar a la carpeta

```bash
cd mi-app
```

---

## 5. Instalar dependencias

```bash
npm install
```

Esto descarga todas las librerías necesarias definidas en el `package.json`.

Por ejemplo:

* React
* React DOM
* Vite
* plugins

---

## 6. Levantar el servidor de desarrollo

```bash
npm run dev
```

Vite inicia un servidor local en modo desarrollo y muestra algo como:

```bash
Local: http://localhost:5173/
```

Entrando a esa URL ves la aplicación funcionando.

---

# Estructura básica del proyecto

Después de crearlo aparecen carpetas importantes:

```plaintext
mi-app/
│
├── node_modules/
├── public/
├── src/
├── package.json
├── vite.config.js
```

---

## ¿Qué hace cada carpeta?

### `src/`

Código fuente principal de la aplicación.

Ahí suele estar:

```plaintext
src/
├── App.jsx
├── main.jsx
├── components/
```

---

### `public/`

Archivos estáticos:

* imágenes
* íconos
* assets públicos

---

### `node_modules/`

Dependencias instaladas por npm.

No se modifica manualmente.

---

### `package.json`

Archivo que define:

* dependencias
* scripts
* configuración del proyecto

Ejemplo:

```json
"scripts": {
  "dev": "vite",
  "build": "vite build"
}
```

---

### `vite.config.js`

Configuración de Vite.

Por ejemplo:

* aliases
* plugins
* variables de entorno
* configuración del servidor

---

# Flujo resumido

```bash
npm create vite@latest
cd mi-app
npm install
npm run dev
```

---

# Conceptualmente


> “Vite genera automáticamente la estructura inicial de una aplicación React.
> Después instalamos las dependencias con npm y ejecutamos un servidor de desarrollo para poder trabajar localmente.”

---

# Diferencia con Create React App

```bash
npx create-react-app
```

Si bien se puede crear un proyecto React con ese comando, hoy Vite es más usado porque:

* inicia más rápido
* compila más rápido
* tiene mejor experiencia de desarrollo
* usa herramientas modernas como ES Modules
