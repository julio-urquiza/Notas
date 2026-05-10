# Instalar y conectar MongoDB en un proyecto Express

## 1. ¿Qué es MongoDB?

Antes de instalar nada:

* MongoDB es una base de datos NoSQL.
* Guarda información en documentos JSON/BSON.
* En Express se usa para persistir datos:

  * usuarios
  * productos
  * preguntas
  * sesiones
  * etc.

Se puede guardar:

```json
{
  "name": "Julio",
  "email": "julio@gmail.com"
}
```

---

# 2. Crear el proyecto Express

Si todavía no existe:

```bash
mkdir backend
cd backend

npm init -y
```

Instalar Express:

```bash
npm install express
```

Crear `app.js`:

```js
const express = require('express');

const app = express();

app.listen(3000, () => {
  console.log('Servidor corriendo');
});
```

---

# 3. Instalar MongoDB Driver o Mongoose

Acá tenés dos caminos.

## Opción recomendada: Mongoose

Como funciona:

* MongoDB es la base de datos
* Mongoose es una librería que facilita trabajar con MongoDB desde Node.js

Instalación:

```bash
npm install mongoose
```

---

# 4. Tener MongoDB funcionando

## Opción A — MongoDB local

Instalar MongoDB Community Server.

* Se instala el servidor de MongoDB
* Corre normalmente en:

```txt
mongodb://localhost:27017
```

---

## Opción B — MongoDB Atlas (más simple para equipos)

Atlas es MongoDB en la nube.

Pasos:

1. Crear cuenta
2. Crear cluster
3. Obtener connection string

Ejemplo:

```txt
mongodb+srv://usuario:password@cluster.mongodb.net/test
```

---

# 5. Conectar Express con MongoDB

Crear:

```txt
src/config/db.js
```

```js
import mongoose from 'mongoose'

const connectDB = async () => {
  try {
    await mongoose.connect('mongodb://localhost:27017/miapp');

    console.log('MongoDB conectado');
  } catch (error) {
    console.log(error);
    process.exit(1);
  }
};

export default connectDB
```

---

# 6. Usar la conexión en la app

En `app.js`:

```js
import express from 'express'
import connectDB from './src/config/db'

const app = express();

connectDB();

app.listen(3000, () => {
  console.log('Servidor corriendo');
});
```

---

# 7. Qué está pasando?

La funcion :
## `mongoose.connect(...)`

Abre una conexión entre:

```txt
Express <-> MongoDB
```

---
La direccion de la base de datos:
## `"mongodb://localhost:27017/miapp"`

Tiene:

| Parte      | Significado       |
| ---------- | ----------------- |
| mongodb:// | protocolo         |
| localhost  | servidor          |
| 27017      | puerto de MongoDB |
| miapp      | nombre de la base |

---

# 8. Variables de entorno (MUY importante)

Instalar dotenv:

```bash
npm install dotenv
```

Crear `.env`

```env
MONGO_URI=mongodb://localhost:27017/miapp
PORT=3000
```

Usarlo:

```js
import dotenv from 'dotenv'
```

```js
await mongoose.connect(process.env.MONGO_URI);
```

Esto evita hardcodear credenciales.

---

# 9. Crear un modelo simple

Por ejemplo:

```txt
src/models/User.js
```

```js
import mongoose from 'mongoose'

const userSchema = new mongoose.Schema({
  name: String,
  email: String
});

export default mongoose.model('User', userSchema); //'User' es como se llamara nuestra tabla en MongoDB
```

---

# 10. Probar guardar datos
La entidad User, al ser un model generado por Mongoose, tiene definidos una seria de metodos para poder acceder a los datos.
```js
import User from './models/User'

const createUser = async () => {
  const user = await User.create({  // crea un objeto con estos datos
    name: 'Julio',
    email: 'julio@gmail.com'
  });

  console.log(user); //{name: 'Julio',email: 'julio@gmail.com'}
};

createUser();
```

---

# 11. Estructura recomendada

```txt
src/
│
├── config/
│   └── db.js
│
├── models/
│   └── User.js
│
├── controllers/
├── services/
├── routes/
│
└── app.js
```

---

# 12. Conceptos importantes

## MongoDB

Base de datos.

---

## Mongoose

ODM (Object Document Mapper).

Transforma:

```js
{ name: 'Julio' }
```

en documentos MongoDB.

---

## Schema

Define la estructura del documento.

---

## Model

Permite operar sobre la colección:

```js
User.find()         // busca y trae un registro de la DB
User.create()       // crea un nuevo registo en la DB
User.deleteOne()    // elimina un registro en la db
```

---

# 13. Diferencia con SQL

Muy común que pregunten esto.

| SQL        | MongoDB               |
| ---------- | --------------------- |
| tablas     | colecciones           |
| filas      | documentos            |
| columnas   | campos                |
| relaciones | referencias/embebidos |

---

# 14. Explicación conceptual

Una buena síntesis sería:

> Express maneja las peticiones HTTP y MongoDB persiste la información.
> Mongoose actúa como capa intermedia para modelar y consultar los datos de forma más simple desde JavaScript.
