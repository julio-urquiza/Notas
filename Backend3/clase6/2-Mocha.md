Mocha en **npm** es un **framework de testing para JavaScript** que se usa principalmente en aplicaciones Node.js, aunque también puede ejecutarse en el navegador.

Sirve para escribir y ejecutar **tests automatizados**, lo que te ayuda a verificar que tu código funciona como esperas.

### Características principales:

- **Soporta testing síncrono y asíncrono** (con `done()`, `async/await` o Promesas).
- **Compatible con múltiples librerías de aserciones** como Chai, Should.js o Node.js assert.
- **Organización con `describe` y `it`** para estructurar las pruebas de forma clara.
- **Hooks** (`before`, `after`, `beforeEach`, `afterEach`) para preparar y limpiar estados antes o después de los tests.
- Se puede integrar con **CI/CD**, **coverage tools** (como `nyc`/`istanbul`) y otros reporters.

### Ejemplo básico con Mocha y Chai:

```bash
npm install --save-dev mocha chai
```

Estructura de prueba (`test/example.test.js`):

```js
const { expect } = require("chai");

describe("Mi primera prueba", function() {
  it("suma básica", function() {
    const resultado = 2 + 3;
    expect(resultado).to.equal(5);
  });
});
```

En el `package.json`:

```json
"scripts": {
  "test": "mocha"
}
```

Ejecutar:

```bash
npm test
```

👉 Esto correrá todos los archivos dentro de la carpeta `test/` que terminen en `.test.js` o `.spec.js`.

---
### Ejemplo usando **solo Mocha + assert**

```bash
npm install --save-dev mocha
```

Archivo `test/example.test.js`:

```js
const assert = require("assert");

describe("Array", function() {
  it("debería devolver -1 cuando no encuentra el elemento", function() {
    assert.strictEqual([1, 2, 3].indexOf(4), -1);
  });
});
```

En `package.json`:

```json
"scripts": {
  "test": "mocha"
}
```

Ejecutás:

```bash
npm test
```

Y vas a ver la salida de Mocha con el reporter por defecto mostrando si pasó o falló.

---

En ese ejemplo:

```js
const assert = require("assert");

describe("Array", function() {
  it("debería devolver -1 cuando no encuentra el elemento", function() {
    assert.strictEqual([1, 2, 3].indexOf(4), -1);
  });
});

```

👉 **`describe` e `it` no los importaste vos en el archivo**, sino que te los da **Mocha automáticamente** cuando ejecutás el test.

---

### ¿Cómo funciona?

- Mocha cuando corre un archivo de test, lo envuelve en un **contexto de ejecución** donde define globalmente esas funciones (`describe`, `it`, `before`, `after`, etc.).
- Por eso no necesitás hacer `import { describe, it } from "mocha"` (aunque también se puede, como hiciste en tu otro código).

---
### Ejemplo visto en clase

```js
import Users from "../../src/dao/Users.dao.js";
import mongoose, { isValidObjectId } from "mongoose";
import { describe, it, before, after, beforeEach, afterEach } from "mocha";
import Assert from "assert";

const assert = Assert.strict;
const usersDao = new Users();

describe("Tests dao Users", function () {
  this.timeout(10_000);

  // Conexión a la DB antes de todos los tests
  before(async () => {
    await mongoose.connect(
      "mongodb+srv://coderhouse:codercoder2023@cluster0.wpxpupc.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0&dbName=comisPruebas"
    );
  });

  // Cierre de conexión después de todos los tests
  after(async () => {
    await mongoose.disconnect();
  });

  // Antes de cada test limpiamos el usuario de prueba (por si quedó algo)
  beforeEach(async () => {
    await mongoose.connection.collection("users").deleteMany({ email: "test@test.com" });
  });

  // Después de cada test limpiamos también
  afterEach(async () => {
    await mongoose.connection.collection("users").deleteMany({ email: "test@test.com" });
  });

  it("El dao con su método get, retorna un array", async () => {
    let resultado = await usersDao.get();
    assert.ok(Array.isArray(resultado));
  });

  it("El dao con su método get, retorna objetos con propiedad _id", async () => {
    let resultado = await usersDao.get();

    if (Array.isArray(resultado) && resultado.length > 0) {
      assert.ok(resultado[0]._id);
    }
  });

  it("El dao con su método get, retorna objetos con propiedad first_name", async () => {
    let resultado = await usersDao.get();

    if (Array.isArray(resultado) && resultado.length > 0) {
      assert.ok(resultado[0].first_name);
    }
  });

  it("El dao con su método save, graba un usuario en DB", async () => {
    let userMock = {
      first_name: "juan",
      last_name: "lopez",
      email: "test@test.com",
      password: "123",
    };

    let resultado = await usersDao.save(userMock);

    assert.ok(resultado._id);
    assert.equal(isValidObjectId(resultado._id), true);
    assert.equal(resultado.first_name, userMock.first_name);
  });

  it("No debería guardar un usuario sin email", async () => {
    try {
      await usersDao.save({
        first_name: "sinemail",
        last_name: "prueba",
        password: "123",
      });
      assert.fail("Debería haber lanzado un error al guardar sin email");
    } catch (error) {
      assert.ok(error);
    }
  });
});
```

