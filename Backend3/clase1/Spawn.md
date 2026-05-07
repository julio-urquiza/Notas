`spawn()` es una función del módulo **`child_process`** de Node.js que permite **ejecutar comandos del sistema**, pero **a diferencia de `exec()`**, no guarda toda la salida en un buffer:  
en su lugar, **trabaja con streams** (datos por partes).

Esto lo vuelve ideal para **procesos largos** o que generan **mucha salida**, como:

- `ffmpeg` para procesar videos
- `ping` o `tail -f` que nunca terminan
- comandos que imprimen mucho texto

---

## 📦 Importación

```js
const { spawn } = require('child_process');
```

---

## 🧪 Ejemplo básico

```js
const { spawn } = require('child_process');

const ls = spawn('ls', ['-la']); // Comando y argumentos

ls.stdout.on('data', (data) => {
  console.log(`Salida: ${data}`);
});

ls.stderr.on('data', (data) => {
  console.error(`Error: ${data}`);
});

ls.on('close', (code) => {
  console.log(`Proceso terminó con código ${code}`);
});
```

---

## 🔥 ¿Qué pasa aquí?

- `spawn('ls', ['-la'])` ejecuta `ls -la`
- `stdout` y `stderr` son **streams**
- `close` se ejecuta cuando el proceso termina

---

## 🆚 `spawn()` vs `exec()` vs `fork()`

|Método|Uso recomendado|Ejecuta|Manejo de salida|
|---|---|---|---|
|**spawn()**|Procesos **grandes o largos**|Cualquier comando|**Streams (tramo por tramo)**|
|**exec()**|Procesos **cortos** con poca salida|Cualquier comando|**Buffer (todo junto)**|
|**fork()**|Ejecutar **otro archivo Node.js**|Código JS|Comunicación con `send()`|

---

## 🎯 Ejemplo real: ejecutar `ping`

```js
const { spawn } = require('child_process');

const ping = spawn('ping', ['google.com']);

ping.stdout.on('data', (data) => {
  console.log(`PING: ${data}`);
});
```

Este comando **no termina** hasta que lo detengas.  
Esto sólo es posible gracias a que **spawn trabaja con streams** 👍

---

## 🧠 Resumen

- `spawn()` ejecuta comandos del sistema **sin bloquear memoria**
- Ideal para procesos **continuos o con mucha salida**
- Se comunica mediante **streams (`stdout`, `stderr`)**
- Es más eficiente que `exec()` para tareas largas

---