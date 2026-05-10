# ¿Qué es Git?

Git es un sistema de control de versiones distribuido.

Sirve para:

- guardar historial de cambios
    
- trabajar en equipo
    
- volver atrás si algo se rompe
    
- crear ramas para desarrollar funcionalidades
    
- fusionar cambios
    

Git no guarda simplemente archivos: guarda snapshots del proyecto en distintos momentos llamados **commits**.

---

# Flujo básico de Git

Git trabaja principalmente con 3 áreas:

```txt
Working Directory -> Staging Area -> Local Repository
```

## 1. Working Directory

Es tu carpeta de trabajo actual.

Ahí editás archivos normalmente:

```txt
index.js
app.js
styles.css
```

Todavía Git no tiene esos cambios guardados oficialmente.

---

## 2. Staging Area (Index)

Es una zona intermedia.

Acá elegís QUÉ cambios querés guardar en el próximo commit.

---

## 3. Local Repository

Es donde Git guarda el historial completo de commits.

---

# `git init`

```bash
git init
```

Inicializa un repositorio Git en la carpeta actual.

Git crea internamente una carpeta oculta:

```txt
.git
```

Ahí guarda:

- commits
    
- ramas
    
- configuraciones
    
- historial
    
- referencias
    

Después de esto la carpeta ya es un repositorio Git.

---

# Configuración inicial de Git

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@gmail.com"
```

Esto configura quién hace los commits.

Cada commit guarda metadata:

- autor
    
- email
    
- fecha
    
- mensaje
    

Por eso cuando hacés:

```bash
git log
```

Git puede mostrar quién hizo cada cambio.

---

# `--global`

Significa:

> aplicar esta configuración para TODOS los repositorios del sistema.

Sin `--global`, la configuración sería solo para el proyecto actual.

---

# Ver configuraciones

```bash
git config --list
```

Muestra todas las configuraciones activas.

Por ejemplo:

```txt
user.name=Julio
user.email=julio@gmail.com
init.defaultbranch=main
```

---

# Cambiar rama principal por defecto

```bash
git config --global init.defaultBranch main
```

Antes Git creaba la rama principal como:

```txt
master
```

Ahora normalmente se usa:

```txt
main
```

Esto hace que TODOS los futuros repositorios arranquen con `main`.

---

# `git add`

```bash
git add README.md
```

Mueve archivos desde:

```txt
Working Directory -> Staging Area
```

Es decir:

> “quiero incluir este archivo en el próximo commit”

---

## `git add .`

Agrega TODOS los cambios.

```bash
git add .
```

---

# `git status`

```bash
git status
```

Muestra:

- archivos modificados
    
- archivos staged
    
- archivos sin seguimiento
    
- rama actual
    

Ejemplo:

```txt
modified: app.js
new file: styles.css
```

Es probablemente el comando más usado de Git.

---

# `git commit`

```bash
git commit -m "Agrega login"
```

Crea un snapshot del proyecto.

El commit contiene:

- cambios
    
- autor
    
- fecha
    
- mensaje
    
- hash único
    

---

# Importancia del mensaje del commit

Un buen commit explica:

- QUÉ cambió
    
- no necesariamente CÓMO
    

Mal:

```txt
cambios
```

Bien:

```txt
Agrega validación de contraseña
```

---

# Hash del commit

Cada commit tiene un identificador único:

```txt
8f2a1b9
```

Git usa hashes SHA.

Eso permite:

- identificar commits
    
- comparar versiones
    
- volver atrás
    
- fusionar cambios
    

---

# `git log`

```bash
git log
```

Muestra historial completo.

Ejemplo:

```txt
commit 8f2a1b9...
Author: Julio
Date: ...
```

---

## `git log --oneline`

Versión resumida:

```txt
8f2a1b9 Agrega login
4ac912f Corrige estilos
```

Mucho más usada en el día a día.

---

# `git diff`

```bash
git diff
```

Muestra diferencias entre:

```txt
Working Directory vs Staging Area
```

O sea:

> cambios todavía NO agregados con `git add`

---

## Qué muestra

```diff
- const nombre = ""
+ const nombre = "Julio"
```

- `-` línea eliminada
    
- `+` línea agregada
    

---

# `git show`

```bash
git show 8f2a
```

Muestra información detallada de un commit:

- autor
    
- fecha
    
- mensaje
    
- diferencias exactas
    

Sirve para inspeccionar cambios específicos.

---

# Cómo se conecta todo el flujo

## Ejemplo completo

### 1. Crear repo

```bash
git init
```

---

### 2. Crear archivo

```txt
app.js
```

---

### 3. Ver estado

```bash
git status
```

Git dice:

```txt
untracked file: app.js
```

---

### 4. Agregar al staging

```bash
git add app.js
```

---

### 5. Crear commit

```bash
git commit -m "Crea app inicial"
```

---

### 6. Ver historial

```bash
git log --oneline
```

---

# Concepto importante: Git NO guarda automáticamente

Muchos principiantes creen que guardar el archivo ya guarda en Git.

No.

Primero:

```txt
guardar archivo
```

Después:

```txt
git add
```

Después:

```txt
git commit
```

Git solo versiona lo que entra en commits.

---

# Desarrollo colaborativo

En equipos normalmente se trabaja con:

- ramas (`git branch`)
    
- cambios remotos (`git push`)
    
- traer cambios (`git pull`)
    
- fusionar (`git merge`)
    
- plataformas como GitHub
    

El flujo básico suele ser:

```txt
clonar repo
→ crear rama
→ desarrollar
→ commit
→ push
→ pull request
→ merge
```

---

# Idea mental importante

Git no es “guardar archivos”.

Git es:

> construir una línea temporal del proyecto.

Cada commit es un punto en la historia del código.