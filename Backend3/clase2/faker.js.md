La librería **`faker.js`** (ahora conocida como **`@faker-js/faker`**) es una de las herramientas más usadas en Node.js para **generar datos falsos realistas** (mock data).

Se usa muchísimo en **testing**, **TDD**, **APIs de prueba**, **semillas de bases de datos (seeders)** o cuando necesitás **simular usuarios, productos, emails, etc.** sin depender de datos reales.

---

## 🧠 ¿Qué es Faker.js?

Es una librería que genera **datos aleatorios pero con formato realista**:

- nombres y apellidos
- direcciones
- correos
- empresas
- textos
- imágenes
- números
- fechas
- etc.

Por ejemplo, podés crear cientos de usuarios falsos con nombres reales, correos válidos y ubicaciones creíbles.

---

## ⚙️ Instalación

Hoy en día la versión mantenida es el **fork oficial de la comunidad**:

```bash
npm install @faker-js/faker
```

_(el proyecto original “faker.js” fue eliminado en 2022, y esta versión lo reemplaza con mantenimiento activo)._

---

## 🚀 Uso básico

```js
import { faker } from '@faker-js/faker';

// Usuario falso
const usuario = {
  id: faker.string.uuid(),
  nombre: faker.person.fullName(),
  email: faker.internet.email(),
  pais: faker.location.country(),
  avatar: faker.image.avatar(),
};

console.log(usuario);
```

Salida (ejemplo):

```js
{
  id: 'f2f0c1e0-55fa-4a7e-b418-cc6e45b7ff6a',
  nombre: 'Julieta Gómez',
  email: 'julieta.gomez72@example.com',
  pais: 'Argentina',
  avatar: 'https://cdn.fakerjs.dev/avatar/123.jpg'
}
```

---

## 💡 Categorías principales de datos

|Categoría|Ejemplo|
|---|---|
|`faker.person`|nombres, apellidos, género|
|`faker.internet`|emails, urls, contraseñas|
|`faker.location`|país, ciudad, dirección|
|`faker.phone`|números de teléfono|
|`faker.company`|nombres de empresa, cargos|
|`faker.commerce`|productos, precios, descripciones|
|`faker.image`|imágenes de productos o personas|
|`faker.date`|fechas y horarios aleatorios|
|`faker.string`|UUIDs, caracteres aleatorios|
|`faker.finance`|números de cuenta, montos, monedas|

---

## 🧩 Ejemplo: generar lista de productos falsos

```js
import { faker } from '@faker-js/faker';

const productos = Array.from({ length: 5 }).map(() => ({
  id: faker.string.uuid(),
  nombre: faker.commerce.productName(),
  descripcion: faker.commerce.productDescription(),
  precio: faker.commerce.price(),
  imagen: faker.image.urlPicsumPhotos(),
}));

console.log(productos);
```

Salida:

```js
[
  {
    id: '1b2d3e4f-5a6b-7c8d-9e0f-1a2b3c4d5e6f',
    nombre: 'Incredible Plastic Keyboard',
    descripcion: 'Ergonomic and stylish keyboard with RGB lighting.',
    precio: '49.99',
    imagen: 'https://picsum.photos/640/480'
  },
  ...
]
```

---

## 🧰 Uso con Express (API fake)

Podés montar una API de prueba fácilmente:

```js
import express from 'express';
import { faker } from '@faker-js/faker';

const app = express();

app.get('/api/users', (req, res) => {
  const users = Array.from({ length: 10 }).map(() => ({
    id: faker.string.uuid(),
    name: faker.person.fullName(),
    email: faker.internet.email(),
    country: faker.location.country(),
  }));

  res.json(users);
});

app.listen(3000, () => console.log('API fake corriendo en http://localhost:3000'));
```

👉 Ahora podés visitar `http://localhost:3000/api/users` y obtener usuarios falsos en JSON.

---

## 🧩 Integración con testing

Es muy útil en **TDD**:

```js
import { faker } from '@faker-js/faker';
import assert from 'node:assert/strict';
import test from 'node:test';

test('crear usuario con datos válidos', () => {
  const usuario = {
    nombre: faker.person.fullName(),
    email: faker.internet.email(),
  };

  assert.match(usuario.email, /@/); // Tiene un email válido
});
```

---

## 📦 Extras

- Se puede **configurar el idioma local**, por ejemplo en español:
   ```js
    import { fakerES as faker } from '@faker-js/faker';
    console.log(faker.person.fullName()); // "María Fernández"
    ```

- También podés **sembrar el generador** para repetir los mismos resultados:
   ```js
    faker.seed(123);
    ```


---

## 🚀 En resumen

|Concepto|Descripción|
|---|---|
|Nombre|`@faker-js/faker`|
|Tipo|Generador de datos falsos|
|Usos|Testing, desarrollo, seeders, demos|
|Ventajas|Rápido, realista, configurable por idioma|
|Alternativas|Chance.js, Casual, Mockaroo (online)|

---
