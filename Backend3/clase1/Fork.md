## 🧠 ¿Qué es `fork()`?

`fork()` es un método de Node.js que permite **crear un proceso hijo** que ejecuta **otro archivo JavaScript** separado del proceso principal.

Se usa para:

- **Trabajos pesados** que bloquearían el event loop
- **Procesar datos en paralelo**
- **Distribuir carga** (como un mini multihilo)

No confundir con `spawn()` o `exec()`.  
`fork()` está pensado **específicamente para ejecutar código Node.js**.

---

## 😎 Ejemplo básico

### `main.js` (proceso padre)

```js
const { fork } = require('child_process');

const child = fork('./child.js');

child.send({ message: 'Hola hijo' }); // Enviar mensaje al hijo

child.on('message', (msg) => {
  console.log('Mensaje del hijo:', msg);
});
```

### `child.js` (proceso hijo)

```js
process.on('message', (msg) => {
  console.log('Mensaje del padre:', msg);

  process.send({ message: 'Hola padre' }); // Responder al padre
});
```

> Ambos pueden comunicarse usando `send()` y `message` como si fuera un canal privado.

---

## 💡 ¿Por qué usar `fork()`?

Node.js tiene **un solo hilo** para ejecutar JS.  
Si tenés una función pesada (ej: procesamiento de imágenes, hashes, cálculos intensos), bloqueás el event loop → la API deja de responder.

Con `fork()`, delegás el trabajo a otro proceso:

```
Proceso principal ──> Maneja API / peticiones
Proceso hijo       ──> Realiza cálculos pesados
```

---

## 🚀 Ejemplo de uso real

### Simular una API que delega procesamiento pesado

#### `server.js`

```js
const http = require('http');
const { fork } = require('child_process');

http.createServer((req, res) => {
  if (req.url === '/calcular') {
    const child = fork('./heavy-task.js');
    
    child.send('start');

    child.on('message', result => {
      res.end(`Resultado: ${result}`);
    });

  } else {
    res.end('Servidor funcionando');
  }
}).listen(3000);

console.log('Servidor en http://localhost:3000');
```

#### `heavy-task.js`

```js
process.on('message', () => {
  let sum = 0;
  for (let i = 0; i < 1e9; i++) { // Tarea pesada
    sum += i;
  }
  process.send(sum);
});
```

✅ El servidor **no se bloquea** aunque la operación sea pesada.  
Sin `fork()`, el servidor hubiera quedado colgado hasta terminar ese `for`.

---

## 🆚 `fork()` vs `spawn()` vs `exec()`

|Método|Uso|Ejecuta|Comunicación|
|---|---|---|---|
|`fork()`|Procesos Node que cooperan|Archivos `.js`|Canal interno `.send()`|
|`spawn()`|Ejecutar comandos largos|Binarios/shell|Streams (stdout/stdin)|
|`exec()`|Ejecutar comandos y obtener resultado completo|Binarios/shell|Buffer (resultado completo)|

---

## 🏁 Resumen

- `fork()` crea un proceso hijo para ejecutar otro archivo Node.js
- Ideal para trabajo intensivo sin bloquear el event loop
- Comunicación padre ↔ hijo por `process.send()` y `message`
- Se usa en APIs, workers, clustering, balanceo de carga

---
