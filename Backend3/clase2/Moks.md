Los **mocks** (o **objetos simulados**) son una herramienta fundamental cuando hacés **testing en Node.js** — especialmente si aplicás **TDD** o probás funciones que dependen de otras partes del sistema (bases de datos, APIs, archivos, etc.).

---

## 🧠 ¿Qué es un _mock_?

Un **mock** es un **objeto falso o simulado** que **imita el comportamiento** de una dependencia real (una función, módulo o API) para que puedas probar tu código **sin ejecutarla realmente**.

En otras palabras:

> Un mock reemplaza una parte externa o costosa del sistema (por ejemplo una base de datos, una API externa, o un módulo complejo) con una versión controlada y predecible.

---

## 🎯 ¿Para qué sirve un mock?

Sirve para:

- Evitar llamadas reales a **servicios externos** (por ejemplo, evitar que un test llame a una API o base de datos).
- **Controlar los datos de entrada y salida**, garantizando resultados reproducibles.
- **Aislar el código** que estás testeando (solo probás tu lógica, no la de otros módulos).
- **Simular errores** (por ejemplo, una API que responde con 500 o una base de datos caída).

---

## 🔧 Tipos de mocks

|Tipo|Qué hace|
|---|---|
|**Mock function**|Reemplaza una función real y registra si fue llamada, cuántas veces, con qué argumentos, etc.|
|**Stub**|Similar a un mock, pero define un valor de retorno fijo o un comportamiento determinado.|
|**Spy**|Observa una función real sin reemplazarla. Permite saber si fue llamada y con qué datos.|
|**Fake**|Una versión simplificada de algo real (por ejemplo, una base de datos en memoria).|

---

## 💻 Ejemplo con Node.js (`node:test` + `sinon`)

```js
import test from 'node:test';
import assert from 'node:assert/strict';
import sinon from 'sinon';

// Módulo que queremos probar
import { getUserData } from './userService.js';
import * as db from './db.js';

// getUserData usa db.findUser internamente
test('getUserData devuelve los datos del usuario', async () => {
  // Creamos un mock de la función db.findUser
  const mock = sinon.stub(db, 'findUser').resolves({ id: 1, name: 'Julio' });

  const result = await getUserData(1);

  assert.deepStrictEqual(result, { id: 1, name: 'Julio' });
  assert.strictEqual(mock.calledOnce, true);
  assert.strictEqual(mock.calledWith(1), true);

  // Restauramos el original
  mock.restore();
});
```

➡️ En este ejemplo, **no se consulta una base de datos real**, sino que se **simula la respuesta** con un mock.

---

## 🧰 Librerías populares para mocks en Node.js

- **Sinon.js** → la más usada para mocks, spies y stubs.
- **Jest** → tiene mocks integrados (`jest.fn()`, `jest.mock()`).
- **node:test** → soporta funciones simuladas desde Node.js 20 con `mock.fn()`.

---

## 🧩 Ejemplo con el mock nativo de Node.js 20+

```js
import test, { mock } from 'node:test';
import assert from 'node:assert/strict';

test('mock.fn ejemplo', () => {
  const fn = mock.fn((x) => x * 2);

  const result = fn(5);
  assert.strictEqual(result, 10);
  assert.strictEqual(fn.mock.callCount(), 1);
});
```

---

```js
const mock = sinon.stub(db, 'findUser').resolves({ id: 1, name: 'Julio' });
```

---

### 🔍 Contexto

- Tenés un módulo llamado `db` (por ejemplo `db.js`),  
    que tiene una función **`findUser`** que normalmente haría algo como:    
   ```js
    export async function findUser(id) {
      return await database.query('SELECT * FROM users WHERE id = ?', [id]);
    }
    ```
    
- Pero durante un **test**, **no querés conectar a una base de datos real**,  
    porque sería lento, incierto o podría fallar.

Entonces usás **`sinon.stub()`** para **reemplazar temporalmente** esa función real con una versión **falsa (mockeada)** controlada por vos.

---

### ⚙️ Qué hace cada parte

#### 1️⃣ `sinon.stub(db, 'findUser')`

👉 Reemplaza la función `db.findUser` por un **stub** (una función falsa controlada por Sinon).  
Esto quiere decir que, desde este momento, **si el código llama a `db.findUser()`**, **ya no ejecuta la versión original**, sino la simulada.

---

#### 2️⃣ `.resolves({ id: 1, name: 'Julio' })`

👉 Le decís al stub que **devuelva una promesa resuelta** con ese valor.  
Es decir, cuando alguien llame a `db.findUser(1)`, el mock va a devolver:

```js
Promise.resolve({ id: 1, name: 'Julio' });
```

(Como si la base de datos realmente hubiera devuelto ese usuario.)

---

#### 3️⃣ `const mock = ...`

👉 Guardás el stub en la variable `mock` para poder:

- Verificar si fue llamado (`mock.calledOnce`, `mock.calledWith(...)`)
- Restaurar la función original después (`mock.restore()`)

---

### 🧠 En resumen

|Parte|Qué hace|
|---|---|
|`sinon.stub(db, 'findUser')`|Reemplaza la función real por una falsa controlable|
|`.resolves({ id: 1, name: 'Julio' })`|Hace que la función simulada devuelva una promesa con ese valor|
|`mock`|Te permite inspeccionar y restaurar el stub más tarde|

---

### 🧩 Ejemplo simplificado visual

Antes:

```js
await db.findUser(1);
// → consulta real a la base de datos
```

Durante el test (con el stub):

```js
await db.findUser(1);
// → devuelve { id: 1, name: 'Julio' } inmediatamente
// sin tocar la base de datos
```

---