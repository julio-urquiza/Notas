En una arquitectura Express bien armada el controller normalmente captura las excepciones del service y las delega al middleware de errores.

La idea es:

* el **service** lanza errores de negocio
* el **controller** captura errores async
* el **middleware de errores** decide la respuesta HTTP final

El patrón típico es este:

---

# Service

El service NO responde HTTP.

Solo lanza errores.

```js
async function create(data) {
  const user = await userRepository.findByEmail(data.email);

  if (user) {
    throw new Error("Email already exists");
  }

  return userRepository.create(data);
}
```

---

# Controller

El controller captura errores y llama a `next(error)`.

```js
async function create(req, res, next) {
  try {
    const user = await userService.create(req.body);

    res.status(201).json(user);

  } catch (error) {
    next(error);
  }
}
```

---

# Middleware de errores

```js
function errorHandler(error, req, res, next) {
  return res.status(500).json({
    message: error.message
  });
}
```

---

# Registro del middleware

```js
app.use(errorHandler);
```

MUY importante:
el middleware de errores va al final de todo.

---

# ¿Por qué no responder directamente desde el service?

Porque rompería la separación de capas.

Esto estaría mal:

```js
// ❌ MAL
res.status(400).json(...)
```

El service no debería saber:

* HTTP
* Express
* req/res
* status codes

El service debería ser reutilizable incluso fuera de Express.

---

# Entonces, ¿qué responsabilidad tiene cada capa con los errores?

| Capa             | Responsabilidad                        |
| ---------------- | -------------------------------------- |
| Service          | Detectar problemas y lanzar errores    |
| Controller       | Capturar errores async y delegarlos    |
| Error Middleware | Transformar errores en respuestas HTTP |

---

# Ejemplo más profesional

## Error personalizado

```js
class AppError extends Error {
  constructor(message, statusCode) {
    super(message);

    this.statusCode = statusCode;
  }
}
```

---

## Service

```js
throw new AppError("User not found", 404);
```

---

## Controller

```js
try {
  ...
} catch (error) {
  next(error);
}
```

---

## Error middleware

```js
function errorHandler(error, req, res, next) {
  return res.status(error.statusCode || 500).json({
    message: error.message
  });
}
```

---

# Problema típico en Express

Mucha gente hace esto:

```js
try {
  ...
} catch (error) {
  res.status(500).json(...)
}
```

en TODOS los controllers.

Eso termina duplicando lógica.

Por eso normalmente se usa:

```js
next(error)
```

y un middleware global.

---

# Incluso más limpio: asyncHandler

Para evitar escribir try/catch en todos lados.

## Helper

```js
function asyncHandler(fn) {
  return function(req, res, next) {
    Promise.resolve(fn(req, res, next))
      .catch(next);
  };
}
```

---

## Uso

```js
router.post(
  "/users",
  asyncHandler(userController.create)
);
```

Entonces el controller queda:

```js
async function create(req, res) {
  const user = await userService.create(req.body);

  res.status(201).json(user);
}
```

Mucho más limpio.

---

# Arquitectura correcta mentalmente

```txt
Controller
   ↓
Service
   ↓
Repository
```

Y cuando hay error:

```txt
Repository
   ↑
Service throws
   ↑
Controller catch
   ↑
Error Middleware responde HTTP
```

---

# Regla importante

## Controllers

Manejan HTTP.

## Services

Manejan lógica de negocio.

## Middlewares de error

Manejan errores HTTP globales.
