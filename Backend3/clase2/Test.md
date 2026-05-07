## 🧪 ¿Qué es `node:test`?

`node:test` es un **módulo incorporado** desde **Node.js v18** (y estable a partir de la v20) que te permite escribir y ejecutar **tests automatizados** directamente con Node.

Es ideal para TDD o para validar tus funciones, APIs o módulos sin instalar librerías adicionales.

---

## ⚙️ Cómo usarlo

### 1️⃣ Crear un archivo de prueba

Por convención se usa el sufijo `.test.js` o `.spec.js`.  
Por ejemplo: `suma.test.js`

```js
import test from 'node:test';
import assert from 'node:assert/strict';
import { suma } from './suma.js';

test('suma 1 + 2 debe dar 3', () => {
  const resultado = suma(1, 2);
  assert.strictEqual(resultado, 3);
});
```

---

### 2️⃣ Crear el archivo que vas a probar

`suma.js`

```js
export function suma(a, b) {
  return a + b;
}
```

---

### 3️⃣ Ejecutar los tests

En la terminal, corrés:

```bash
node --test
```

Esto busca automáticamente todos los archivos que terminan en `.test.js` o `.spec.js` y los ejecuta.

---

## ✅ Funcionalidades útiles

### Agrupar pruebas con subtests

Podés anidar tests:

```js
test('Operaciones matemáticas', async (t) => {
  await t.test('suma', () => {
    assert.strictEqual(2 + 2, 4);
  });

  await t.test('resta', () => {
    assert.strictEqual(5 - 3, 2);
  });
});
```

### Tests asíncronos

Soporta `async/await` sin problemas:

```js
test('ejemplo async', async () => {
  const data = await Promise.resolve(42);
  assert.strictEqual(data, 42);
});
```

### Hooks (setup y teardown)

Podés usar `before`, `after`, `beforeEach`, `afterEach`:

```js
import { beforeEach, afterEach, test } from 'node:test';

beforeEach(() => console.log('Antes de cada test'));
afterEach(() => console.log('Después de cada test'));

test('test 1', () => {});
test('test 2', () => {});
```

---

## 💡 Comparación rápida

|Herramienta|Ventajas|Desventajas|
|---|---|---|
|**node:test**|Nativo, sin dependencias, rápido|Menos funcionalidades “de lujo” que Jest|
|**Jest**|Completo, mocks, snapshots, cobertura|Más lento, necesita instalación|
|**Mocha + Chai**|Muy personalizable|Más configuración manual|

---
