`exec()` es una función del módulo **`child_process`** de Node.js que permite **ejecutar comandos del sistema (shell)** desde tu programa.  
Es decir, con `exec()` podés correr cosas como:

- `ls`, `mkdir`, `cat` (Linux/Mac)
- `dir`, `copy` (Windows)
- o cualquier comando externo (ej: `git`, `ffmpeg`, `python`, etc.)

---

## 📦 Cómo se importa

```js
const { exec } = require('child_process');
```

---

## 🚀 Ejemplo básico

```js
const { exec } = require('child_process');

exec('ls -la', (error, stdout, stderr) => {
  if (error) {
    console.error('Error ejecutando comando:', error);
    return;
  }

  console.log('Salida:', stdout);
});
```

### ¿Qué pasa acá?

- `stdout` = lo que el comando imprimió correctamente
- `stderr` = errores impresos por el comando
- `error` = problema de ejecución (ej: comando inexistente)

---

## 🧠 Importante

`exec()` **devuelve todo el resultado en un solo buffer**.  
Por eso se recomienda para **comandos que no generan mucha salida**.

Si ejecutás algo que imprime demasiado (por ej. 3 GB de logs), el buffer se llena y falla.

---

## 🆚 Comparación rápida (`exec` vs `spawn` vs `fork`)

|Método|Para qué sirve|Ejecuta|Salida|
|---|---|---|---|
|**exec()**|Ejecutar comandos y obtener el **resultado completo**|Binarios / shell|**Buffer completo (stdout)**|
|**spawn()**|Ejecutar comandos **de larga duración** o con mucha salida|Binarios / shell|**Streams (chunk por chunk)**|
|**fork()**|Ejecutar **otro archivo Node.js** como proceso hijo|Código JS|Comunicación mediante `send()`|

---

## 🧯 Ejemplo útil: ejecutar un comando `git`

```js
exec('git status', (err, stdout) => {
  if (err) return console.error(err);
  console.log(stdout);
});
```

---

## ⚙️ Ejemplo ejecutando Python desde Node

```js
exec('python script.py', (err, stdout) => {
  if (err) return console.error(err);
  console.log(stdout);
});
```

---

## 🏁 Resumen

- `exec()` ejecuta **comandos del sistema** desde Node.js.
- Devuelve **toda la salida en un buffer**.
- Es ideal para **comandos cortos**.
- Para comandos grandes → usar `spawn()`.
- Para procesos Node → usar `fork()`.

---
