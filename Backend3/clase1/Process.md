## 🧠 ¿Qué es `process`?

`process` es un **objeto global** disponible en cualquier script de Node.js. Representa el **proceso en ejecución** (o sea, tu programa corriendo) y te permite:

- Acceder a variables de entorno
- Leer argumentos pasados por consola
- Conocer información del sistema
- Escuchar eventos del proceso
- Finalizar la ejecución

No hace falta importarlo:

```js
console.log(process);
```

---

## 📍 Propiedades y usos más comunes

### 1. **Variables de entorno**

Normalmente usadas para API keys, configuraciones según ambiente, etc.

```js
console.log(process.env.NODE_ENV);
console.log(process.env.PORT);
```

Ejemplo:

```bash
PORT=3000 node server.js
```

```js
console.log(process.env.PORT); // 3000
```

---

### 2. **Argumentos desde la terminal**

Se encuentran en `process.argv`.

```bash
node app.js hola mundo
```

```js
console.log(process.argv);
```

Salida:

```js
[
  '/usr/local/bin/node',
  '/path/app.js',
  'hola',
  'mundo'
]
```

---

### 3. **Terminar el proceso**

```js
process.exit(); // sale inmediatamente
```

O con código:

```js
process.exit(1); // 1 indica error, 0 éxito
```

---

### 4. **Información del proceso**

|Propiedad|Significa|
|---|---|
|`process.pid`|ID del proceso en el sistema|
|`process.cwd()`|Directorio actual de ejecución|
|`process.platform`|Sistema operativo (`win32`, `linux`, `darwin`)|
|`process.memoryUsage()`|Uso de memoria|

Ejemplo:

```js
console.log(process.pid);
console.log(process.cwd());
console.log(process.platform);
console.log(process.memoryUsage());
```

---

### 5. **Eventos del proceso**

Por ejemplo, capturar errores globales:

```js
process.on('uncaughtException', (err) => {
  console.error('Error no controlado:', err);
});
```

O salir elegantemente:

```js
process.on('exit', () => {
  console.log('El proceso está terminando...');
});
```

---

## 🧪 Ejemplo práctico

```js
console.log('App iniciada');

process.on('exit', () => {
  console.log('App finalizando...');
});

setTimeout(() => {
  console.log('Terminando...');
  process.exit(0);
}, 2000);
```

---

## 🏁 Resumen

|Función|Para qué sirve|
|---|---|
|`process.env`|Leer variables de entorno|
|`process.argv`|Leer argumentos desde terminal|
|`process.exit()`|Finalizar la ejecución|
|`process.on()`|Escuchar eventos del proceso|
|`process.platform`, `process.pid`|Info del sistema/proceso|

---
