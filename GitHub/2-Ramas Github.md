# `.gitignore`

El archivo:

```txt
.gitignore
```

le dice a Git:

> “estos archivos NO quiero versionarlos”

---

# ¿Por qué existe?

Porque hay archivos que:

- son temporales
    
- se generan automáticamente
    
- contienen secretos
    
- pesan mucho
    
- dependen del entorno local
    

y no deberían subirse al repositorio.

---

# Ejemplos típicos

## Node.js

```txt
node_modules/
.env
logs/
```

---

## Logs

```txt
*.log
```

Ignora cualquier archivo `.log`.

---

## Variables de entorno

```txt
.env
```

Muy importante.

Ahí suelen guardarse:

- passwords
    
- tokens
    
- URLs privadas
    
- claves API
    

Nunca deberían subirse a Git.

---

# Dónde se crea

En la raíz del proyecto:

```txt
mi-proyecto/
 ├── .gitignore
 ├── app.js
 └── package.json
```

---

# Cómo funciona internamente

Git deja de rastrear esos archivos.

O sea:

```txt
git status
```

ya no los muestra.

---

# Importante

`.gitignore` NO elimina archivos ya versionados.

Si un archivo ya estaba en Git:

```bash
git add .env
git commit
```

después agregarlo al `.gitignore` no alcanza.

Primero habría que removerlo del índice:

```bash
git rm --cached .env
```

---

# `.gitkeep`

Git NO versiona carpetas vacías.

Porque Git realmente versiona archivos, no carpetas.

Entonces esto:

```txt
uploads/
```

si está vacío, Git lo ignora.

---

# ¿Para qué sirve `.gitkeep`?

Se agrega un archivo vacío:

```txt
uploads/.gitkeep
```

y así Git “detecta” la carpeta.

---

# Casos comunes

```txt
logs/
uploads/
temp/
cache/
```

Querés que existan en el proyecto aunque estén vacías.

---

# RAMAS (Branches)

Este es el concepto central del desarrollo colaborativo.

Una rama es:

> una línea paralela de desarrollo.

Permite trabajar sin afectar el código estable.

---

# Idea mental importante

Imaginá esto:

```txt
main
  |
  └── código estable
```

Ahora querés hacer login.

En vez de tocar `main` directamente:

```txt
main
  |
  └── feature/login
```

Trabajás aislado.

---

# ¿Por qué es importante?

Porque:

- varios desarrolladores pueden trabajar al mismo tiempo
    
- no rompés producción
    
- podés probar funcionalidades
    
- podés descartar trabajo fácilmente
    

---

# Ver ramas

## Locales

```bash
git branch
```

Ejemplo:

```txt
* main
  feature/login
```

`*` indica la rama actual.

---

## Remotas

```bash
git branch -r
```

Muestra ramas del servidor remoto.

Por ejemplo:

```txt
origin/main
origin/feature/login
```

---

## Todas

```bash
git branch -a
```

Locales + remotas.

---

# Commit sin `-m`

```bash
git commit
```

Abre un editor.

Ahí podés escribir mensajes más completos.

---

# Estructura profesional de commit

```txt
Agrega autenticación JWT

Se implementa middleware de autenticación
para proteger rutas privadas.

También se agrega validación
de expiración de token.
```

---

# ¿Por qué es útil?

Porque en equipos grandes:

- el historial importa mucho
    
- otros desarrolladores leen commits
    
- ayuda debugging
    
- ayuda auditoría
    

---

# Crear ramas

## Opción clásica

```bash
git branch feature/login
git switch feature/login
```

---

# Qué hace cada comando

## `git branch`

Crea la rama.

---

## `git switch`

Te mueve de rama.

---

# Opción moderna

```bash
git switch -c feature/login
```

Hace ambas cosas.

Muy usado hoy.

---

# Convención de nombres

Muy común:

```txt
feature/login
bugfix/header
hotfix/security
refactor/auth
```

Ayuda organización del equipo.

---

# Cómo funcionan las ramas internamente

Una rama realmente es:

> un puntero a commits.

Ejemplo:

```txt
A -- B -- C  ← main
          \
           D -- E ← feature/login
```

Las ramas comparten historial hasta que se bifurcan.

---

# `git diff <rama>`

```bash
git diff feature/login
```

Compara tu rama actual contra otra.

Sirve para ver:

- cambios pendientes
    
- diferencias de código
    
- qué se modificó
    

---

# `git merge`

Fusiona ramas.

---

# Regla importante

> Tenés que estar parado en la rama que RECIBE los cambios.

---

## Ejemplo

Querés traer:

```txt
feature/login → main
```

Entonces:

```bash
git switch main
git merge feature/login
```

---

# Tipos de merge

## Fast-forward

El mejor escenario.

```txt
A -- B -- C main
          \
           D feature
```

Git simplemente mueve el puntero.

No hay conflictos.

---

# Resultado

```txt
A -- B -- C -- D main
```

---

# Merge commit (tercera vía)

Sucede cuando ambas ramas avanzaron.

```txt
A -- B -- C main
      \
       D -- E feature
```

Git crea un commit especial de merge.

---

# Conflictos

El escenario más importante para entender.

---

# ¿Cuándo ocurre?

Cuando dos ramas modifican:

- el mismo archivo
    
- las mismas líneas
    

---

# Ejemplo

## Main

```js
const nombre = "Juan";
```

## Feature

```js
const nombre = "Pedro";
```

Git no sabe cuál conservar.

---

# Entonces aparece un conflicto

Git marca el archivo así:

```txt
<<<<<<< HEAD
const nombre = "Juan";
=======
const nombre = "Pedro";
>>>>>>> feature/login
```

---

# Qué significa

## HEAD

Tu rama actual.

---

## `=======`

Separador.

---

## Parte inferior

La otra rama.

---

# Resolver conflicto

El desarrollador decide:

```js
const nombre = "Pedro";
```

o:

```js
const nombre = "Juan";
```

o combinar ambos.

Después:

```bash
git add .
git commit
```

---

# Herramientas visuales

## [GitHub Desktop](https://desktop.github.com/?utm_source=chatgpt.com)

Cliente gráfico oficial de [GitHub](https://github.com/?utm_source=chatgpt.com).

Ideal principiantes.

Permite:

- commits
    
- ramas
    
- merges
    
- pull/push
    
- resolver conflictos visualmente
    

---

## [GitKraken](https://www.gitkraken.com/?utm_source=chatgpt.com)

Cliente Git mucho más profesional.

Muy usado para visualizar:

- ramas
    
- merges
    
- historial
    
- conflictos
    

Tiene una vista gráfica excelente del árbol de commits.

---

# Flujo colaborativo real

En equipos normalmente pasa esto:

```txt
main
 ├── feature/login
 ├── feature/cart
 ├── bugfix/header
 └── refactor/auth
```

Cada desarrollador trabaja en su rama.

Cuando termina:

```txt
branch → merge → main
```

---

# Idea clave de esta clase

Las ramas permiten:

- aislar trabajo
    
- experimentar
    
- trabajar en paralelo
    
- evitar romper código estable
    
- colaborar entre muchas personas
    

Son probablemente la funcionalidad más poderosa de Git.