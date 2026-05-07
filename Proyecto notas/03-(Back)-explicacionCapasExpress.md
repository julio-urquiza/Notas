Podés explicarlo como una separación de responsabilidades.
Cada capa tiene un trabajo específico para que el proyecto sea más ordenado, mantenible y escalable.

En una arquitectura típica de Express (especialmente estilo “production-ready”), normalmente vas a tener algo así:

```txt
src/
 ├── controllers/
 ├── services/
 ├── repositories/
 ├── models/
 ├── routes/
 ├── middlewares/
 ├── config/
 ├── utils/
 ├── app.js
 └── server.js
```

---

# Flujo general

Cuando llega una request:

```txt
Cliente
   ↓
Route
   ↓
Middleware
   ↓
Controller
   ↓
Service
   ↓
Repository
   ↓
Database
```

Después la respuesta vuelve hacia arriba.

---

# 1. Routes (Rutas)

## ¿Para qué sirven?

Definen las URLs de la API y a qué controlador llamar.

Son el “mapa” de endpoints.

## Responsabilidad

* Recibir requests HTTP
* Asociar endpoint → controller
* Aplicar middlewares

## Ejemplo

```js
router.post("/users", userController.create);
```

## Qué NO deberían hacer

* Lógica de negocio
* Consultas a DB
* Validaciones complejas

---

# 2. Controllers

## ¿Para qué sirven?

Son la capa que maneja la request y la response.

El controller actúa como intermediario entre HTTP y la lógica de negocio.

## Responsabilidad

* Leer req.params, req.body, req.query
* Llamar servicios
* Devolver res.json()

## Ejemplo

```js
async function create(req, res) {
  const user = await userService.create(req.body);

  res.status(201).json(user);
}
```

## Qué NO deberían hacer

* Consultas directas a DB
* Reglas de negocio complejas

Porque si no el controller termina gigante.

---

# 3. Services

## ¿Para qué sirven?

Acá vive la lógica de negocio.

Es la capa más importante conceptualmente.

## Responsabilidad

* Validaciones de negocio
* Reglas del sistema
* Coordinación entre repositorios
* Procesos complejos

## Ejemplo

```js
async function create(data) {
  const existingUser = await userRepository.findByEmail(data.email);

  if (existingUser) {
    throw new Error("Email already exists");
  }

  return userRepository.create(data);
}
```

## Ejemplos reales de lógica de negocio

* “No se puede comprar sin stock”
* “El email debe ser único”
* “Solo admins pueden borrar usuarios”
* “Calcular descuentos”

---

# 4. Repositories/Daos

## ¿Para qué sirven?

Son la capa que habla con la base de datos.

Abstraen el acceso a datos.

## Responsabilidad

* Queries
* CRUD
* Comunicación con MongoDB/PostgreSQL/etc

## Ejemplo

```js
async function findByEmail(email) {
  return UserModel.findOne({ email });
}
```

## Ventaja

Si mañana cambiás MongoDB por PostgreSQL, la mayor parte del cambio queda acá.

---

# 5. Models

En algunos proyectos esta incluido dentro del repository/daos 

## ¿Para qué sirven?

Representan las entidades/datos de la aplicación.

En MongoDB con Mongoose suelen ser schemas.

## Ejemplo

```js
const UserSchema = new Schema({
  name: String,
  email: String,
});
```

## Responsabilidad

* Definir estructura de datos
* Tipos
* Restricciones básicas

---

# 6. Middlewares

## ¿Para qué sirven?

Son funciones que se ejecutan antes del controller.

## Responsabilidad

* Autenticación
* Autorización
* Logs
* Validaciones
* Manejo de errores

## Ejemplo

```js
router.post(
  "/users",
  validateUser,
  userController.create
);
```

---

# 7. Config

## ¿Para qué sirve?

Centraliza configuración de la aplicación.

## Ejemplos

* Variables de entorno
* JWT secret
* Config DB
* Puertos

---

# 8. Utils

## ¿Para qué sirven?

Funciones reutilizables genéricas.

## Ejemplos

* Formatear fechas
* Hash de passwords
* Generar tokens
* Helpers

---

# Ejemplo completo del flujo

## Endpoint

```http
POST /users
```

---

## Route

```js
router.post("/", userController.create);
```

---

## Controller

```js
async function create(req, res) {
  const user = await userService.create(req.body);

  res.status(201).json(user);
}
```

---

## Service

```js
async function create(data) {
  const exists = await userRepository.findByEmail(data.email);

  if (exists) {
    throw new Error("User already exists");
  }

  return userRepository.create(data);
}
```

---

## Repository

```js
async function create(data) {
  return UserModel.create(data);
}
```

---

# Analogía clara

Podés usar esta analogía:

| Capa       | Analogía restaurante      |
| ---------- | ------------------------- |
| Route      | La puerta y el menú       |
| Controller | El mozo                   |
| Service    | El cocinero               |
| Repository | El encargado del depósito |
| Database   | El almacén                |

El cliente hace un pedido:

* el mozo recibe,
* el cocinero decide cómo prepararlo,
* el depósito trae ingredientes,
* el almacén guarda todo.

---

# Idea clave

La arquitectura por capas busca:

* Separar responsabilidades
* Evitar código desordenado
* Facilitar testing
* Facilitar mantenimiento
* Facilitar escalabilidad
* Permitir trabajar en equipo

Porque cada capa tiene un rol claro.
