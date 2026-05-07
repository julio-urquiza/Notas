En **Node.js**, un **cluster** es un módulo incorporado (`cluster`) que permite crear múltiples procesos hijos (**workers**) que comparten el mismo servidor y puerto.

Esto es útil porque:

- Node.js corre en **un solo hilo** (single-threaded), y aunque maneja muy bien la concurrencia gracias a su event loop, no aprovecha todos los núcleos del procesador.
- Con **cluster**, puedes lanzar varios procesos hijos que se ejecutan en paralelo y así distribuir la carga entre los distintos núcleos de la CPU.
- Cada worker es un proceso independiente, pero el **master** (proceso principal) se encarga de balancear las peticiones entrantes.

---

### Ejemplo de uso con **Express**

```js
const cluster = require("cluster");
const os = require("os");
const express = require("express");

if (cluster.isMaster) {
  // Número de CPUs disponibles
  const numCPUs = os.cpus().length;

  console.log(`Master ${process.pid} corriendo`);
  console.log(`Creando ${numCPUs} workers...`);

  // Crear un worker por cada CPU
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }

  // Reiniciar un worker si muere
  cluster.on("exit", (worker, code, signal) => {
    console.log(`Worker ${worker.process.pid} murió, creando uno nuevo...`);
    cluster.fork();
  });

} else {
  // Código que corre en cada worker
  const app = express();

  app.get("/", (req, res) => {
    res.send(`Hola desde worker ${process.pid}`);
  });

  app.listen(3000, () => {
    console.log(`Worker ${process.pid} escuchando en puerto 3000`);
  });
}
```

---

### ¿Qué pasa acá?

- El proceso **master** (principal) crea varios procesos **workers**.
- Todos los workers escuchan en el mismo puerto (`3000`).
- Node.js se encarga de repartir las conexiones entre los workers automáticamente.
- Si un worker falla, el master puede crear uno nuevo para mantener la disponibilidad.

---

👉 En resumen:  
Un **cluster en Node.js con Express** permite escalar tu aplicación para usar **todos los núcleos del CPU**, mejorando el rendimiento y la capacidad de manejar muchas peticiones concurrentes.