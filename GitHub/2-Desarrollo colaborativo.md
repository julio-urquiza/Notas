# Borrar ramas

## `git branch -d`

```bash
git branch -d feature/login
```

Borra una rama SOLO si Git detecta que sus cambios ya fueron fusionados.

Es una medida de seguridad.

---

# ¿Por qué?

Porque Git intenta evitar esto:

```txt
crear rama
→ hacer commits
→ borrar rama
→ perder trabajo
```

---

# `-d` significa

```txt
delete safely
```

---

# `git branch -D`

```bash
git branch -D feature/login
```

Fuerza el borrado.

Ignora la seguridad.

---

# Cuándo se usa

Por ejemplo:

- hiciste pruebas
    
- la rama quedó inútil
    
- querés descartarla completamente
    

---

# Riesgo

Podés perder commits que no existen en otro lado.

Por eso:

```txt
-D = destructivo potencialmente
```

---

# Clonar repositorios

## `git clone`

```bash
git clone https://github.com/usuario/proyecto.git
```

Descarga:

- archivos
    
- commits
    
- ramas
    
- historial
    
- configuración Git
    

---

# Muy importante

`clone` copia también:

```txt
.git
```

O sea:

> el repositorio completo.

---

# Diferencia con descargar ZIP

## ZIP

Solo baja archivos.

NO incluye:

- historial
    
- ramas
    
- commits
    
- remote origin
    

---

## Clone

Obtiene TODO el repositorio Git.

---

# `./`

```bash
git clone repo.git ./
```

Significa:

```txt
clonar en el directorio actual
```

Sin crear otra carpeta.

---

# `git commit --amend`

Uno de los comandos más importantes.

---

# Para qué sirve

Permite:

- corregir el mensaje del último commit
    
- agregar archivos olvidados
    
- modificar el último commit
    

---

# Ejemplo clásico

Hiciste:

```bash
git commit -m "Agrega login"
```

Pero olvidaste:

```txt
validator.js
```

---

# Entonces

```bash
git add validator.js
git commit --amend
```

Git reescribe el último commit incluyendo el archivo.

---

# Importante

`amend` NO crea otro commit.

Modifica el anterior.

---

# Concepto importante

Git realmente:

```txt
destruye el commit anterior
y crea uno nuevo
```

Por eso cambia el hash.

---

# Riesgo colaborativo

No deberías usar `--amend` sobre commits ya enviados al remoto.

Porque reescribís historial compartido.

---

# Trabajo colaborativo real

---

# Repositorio remoto

Normalmente el proyecto vive en:

- [GitHub](https://github.com/?utm_source=chatgpt.com)
    
- [GitLab](https://gitlab.com/?utm_source=chatgpt.com)
    
- [Bitbucket](https://bitbucket.org/?utm_source=chatgpt.com)
    

---

# Colaboradores

Una persona:

- crea repo
    
- administra permisos
    
- agrega colaboradores
    

---

# `git fetch`

```bash
git fetch
```

Descarga metadata remota.

---

# Qué trae

- nuevas ramas
    
- commits remotos
    
- referencias actualizadas
    

---

# Importante

NO modifica tus archivos locales.

Solo actualiza:

```txt
.git
```

---

# Idea mental

```txt
fetch = "mirar qué cambió"
```

---

# `git pull`

```bash
git pull
```

Hace 2 cosas:

```txt
git fetch + git merge
```

---

# Entonces

1. descarga cambios
    
2. los fusiona automáticamente
    

---

# `git pull origin maxi`

```bash
git pull origin maxi
```

Significa:

```txt
traer rama "maxi"
desde el remoto "origin"
```

---

# Qué es `origin`

Es el alias del repositorio remoto.

Generalmente:

```txt
origin → GitHub
```

---

# Ver ramas locales y remotas

```bash
git branch -av
```

Muestra:

- ramas locales
    
- remotas
    
- último commit
    
- tracking
    

---

# Alias en Git

Muy usado profesionalmente.

---

# ¿Qué es?

Atajos personalizados.

---

# Ejemplo

```bash
git config --global alias.l "log --oneline"
```

Ahora podés hacer:

```bash
git l
```

en vez de:

```bash
git log --oneline
```

---

# Alias comunes

## Estado corto

```bash
git config --global alias.s "status --short"
```

---

## Commit rápido

```bash
git config --global alias.c "commit -m"
```

---

## Historial gráfico

```bash
git config --global alias.ll "log --oneline --decorate --all --graph"
```

Muy importante.

---

# Qué muestra `--graph`

Ejemplo:

```txt
* commit A
|\
| * commit feature
|/
* commit main
```

Visualiza ramas y merges.

Muy útil para entender historia Git.

---

# Git Reset

Acá entramos en uno de los temas más delicados.

---

# Qué hace reset

Mueve el puntero HEAD.

O sea:

> “volver el proyecto a otro commit”

---

# HEAD

HEAD representa:

```txt
dónde estoy parado
```

generalmente:

```txt
HEAD → main
```

---

# Diferencia clave

Reset puede afectar:

- commits
    
- staging
    
- working directory
    

Dependiendo del tipo.

---

# Reset Soft

```bash
git reset --soft HASH
```

---

# Qué pasa

Los commits desaparecen PERO:

```txt
los cambios quedan staged
```

---

# Flujo mental

```txt
commit → staging
```

---

# Uso típico

Querés rehacer commits.

---

# Reset Mixed (default)

```bash
git reset HASH
```

o:

```bash
git reset --mixed HASH
```

---

# Qué pasa

Los commits desaparecen y:

```txt
los cambios vuelven al working directory
```

---

# Flujo mental

```txt
commit → working directory
```

---

# Los archivos siguen modificados

Pero ya no están staged.

---

# Reset Hard

```bash
git reset --hard HASH
```

---

# Qué hace

Elimina:

- commits
    
- staging
    
- working directory
    

---

# Flujo mental

```txt
commit → destrucción
```

---

# Muy peligroso

Perdés cambios definitivamente.

---

# Ejemplo visual de resets

Supongamos:

```txt
A -- B -- C -- D ← HEAD
```

---

# Soft hacia B

```txt
A -- B ← HEAD
```

Pero cambios de `C` y `D` quedan staged.

---

# Mixed hacia B

```txt
A -- B ← HEAD
```

Cambios vuelven al working directory.

---

# Hard hacia B

```txt
A -- B ← HEAD
```

Todo lo demás desaparece.

---

# Regla profesional importante

## Nunca usar:

```bash
git reset --hard
```

sin entender exactamente qué estás borrando.

---

# Diferencia conceptual importante

## `reset`

Reescribe historial.

---

## `revert` (tema futuro)

Crea commits inversos sin borrar historia.

Mucho más seguro colaborativamente.

---

# Idea principal de esta clase

Git tiene dos grandes responsabilidades:

1. administrar versiones
    
2. administrar historia
    

Y comandos como:

- `amend`
    
- `reset`
    
- `merge`
    

modifican directamente esa historia.