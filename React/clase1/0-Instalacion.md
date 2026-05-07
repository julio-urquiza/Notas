Para instalar **React** tenés varias formas, dependiendo de cómo quieras armar tu proyecto 👇

---

### 🔹 Opción 1: Usar **Vite** (la más rápida y recomendada)

Vite es un bundler moderno, mucho más liviano que Create React App.

1. Abrí la terminal y corré:
   ```bash
    npm create vite@latest
    ```
2. Poné un nombre al proyecto (ej: `mi-app`).
3. Elegí el framework: **React** o **React + TypeScript** si lo querés con TS.
4. Entrá a la carpeta:
   ```bash
    cd mi-app
    ```
5. Instalá dependencias:
   ```bash
    npm install
    ```
6. Levantá el servidor:
   ```bash
    npm run dev
    ```

👉 Tu app estará disponible en `http://localhost:5173/`

---

### 🔹 Opción 2: Usar **Create React App (CRA)** (más clásico, pero pesado)

1. En la terminal corré:
   ```bash
    npx create-react-app mi-app
    ```
2. Entrá a la carpeta:
   ```bash
    cd mi-app
    ```
3. Levantá el servidor:
   ```bash
    npm start
    ```

👉 Se abre en `http://localhost:3000/`

---

### 🔹 Opción 3: Instalar React manualmente en un proyecto existente

Si ya tenés un proyecto con Node:

```bash
npm install react react-dom
```

Y configurás un bundler como Vite, Webpack o Parcel.

---

⚡ Recomendación: Usá **Vite** para proyectos nuevos porque es más rápido y moderno que CRA.
