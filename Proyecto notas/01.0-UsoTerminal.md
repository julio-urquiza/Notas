# 🧠 Guía mental: Uso de la consola en desarrollo

## 1. Cómo abrir la terminal desde una carpeta (Windows)

La idea clave acá es:

> *La terminal siempre se abre “parada” en una carpeta.*

### 🔹 Métodos principales

* **Barra de direcciones (el más importante)**

  * Vas a la barra
  * Borrás todo
  * Escribís:

```bash
wt
```

→ Abre **Windows Terminal** (recomendado)

```bash
cmd
```

→ Abre **Command Prompt (CMD)**

```bash
powershell
```

→ Abre **PowerShell**

👉 Este método es clave porque abre la terminal **directamente en esa carpeta**.

---

### 🔹 Click derecho

* **Shift + Click derecho**

  * Permite abrir:

    * PowerShell
    * Git Bash
    * Terminal (según configuración)

👉 Esto depende de cómo tenga configurado Windows cada uno.

---

### 🔹 Nota sobre terminales

Explicalo simple:

* **Windows Terminal (wt)** → moderno, recomendado
* **CMD** → viejo, limitado
* **PowerShell** → más potente
* **Git Bash** → estilo Linux (muy usado en dev)

👉 Idea clave:

> “Todas hacen lo mismo, cambia la interfaz y algunas capacidades.”

---

## 2. Abrir el proyecto en el editor

En la barra de direcciones del explorador de archivos:

```bash
code .
```

👉 Traducción:

> “Abrí Visual Studio Code en la carpeta actual”

Esto evita:

* abrir VS Code manualmente
* buscar la carpeta

---

## 3. Navegación en la consola

Acá estás enseñando **cómo moverse en el sistema de archivos**.

### 🔹 Cambiar de carpeta

```bash
cd nombre-carpeta
```

### 🔹 Volver atrás

```bash
cd ..
```

👉 Subís un nivel en la estructura

### 🔹 Crear una carpeta

```bash
mkdir miCarpeta
```
---

### 🔹 Autocompletado (MUY importante)

```bash
cd docu + TAB
```

👉 La consola completa automáticamente.

Esto:

* evita errores
* acelera mucho el trabajo

---

### 🔹 Ir a una ruta específica

```bash
cd "C:\Users\Julio\Desktop\proyecto"
```

👉 Forma práctica:

* copiar la ruta desde la barra de direcciones
* pegarla en la terminal

---

## 4. Concepto clave: “Dónde estoy parado”

Este es EL concepto que define todo.

Cada comando se ejecuta en:

> 📍 la carpeta actual

Ejemplo:

* Si estás en `/backend` → corrés el servidor
* Si estás en `/frontend` → levantás React

👉 Error típico:

> ejecutar comandos en la carpeta equivocada

---

## 5. Terminal integrada de VS Code

### 🔹 Cómo abrirla

* `Terminal → New Terminal`
* o “Open Integrated Terminal”

---

## 6. Diferencia clave: terminal vs editor

Esto ayuda mucho a principiantes:

* **VS Code** → editar código
* **Terminal** → ejecutar cosas

👉 Aunque estén integradas, conceptualmente son distintas.

---

## 7. Resumen conceptual (muy útil para cerrar)

Podés cerrar con esto:

> * La terminal es una herramienta para interactuar con el sistema
> * Siempre estamos “parados” en una carpeta
> * Desde ahí ejecutamos comandos
> * Podemos abrirla de distintas formas
> * Y la usamos constantemente para trabajar en frontend y backend

---

## 8. Mejora puntual a tu explicación (feedback directo)

Dos ajustes que te van a hacer quedar más sólido:

### ❗ 1. “CD barra y tab”

Eso puede confundir.

Mejor decir:

> “Escribís `cd` y empezás a tipear el nombre de la carpeta, después usás TAB para autocompletar”

---

### ❗ 2. Rutas con espacios

Aclará esto (es clave en Windows):

```bash
cd "C:\Program Files\..."
```

👉 Sin comillas → puede romper

---
