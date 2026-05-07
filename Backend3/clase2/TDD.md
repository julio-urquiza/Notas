**TDD (Test Driven Development)** o **Desarrollo Guiado por Pruebas** es una **metodología de desarrollo** que se usa en Node.js (y en cualquier lenguaje o entorno) para escribir código de manera más **segura, predecible y mantenible**.

### 🧠 En qué consiste

TDD se basa en un **ciclo corto y repetitivo** de tres pasos conocidos como **Red → Green → Refactor**:

1. **🟥 Red (Fallar):**  
    Escribís una **prueba (test)** que define una nueva funcionalidad o mejora que todavía no existe.  
    → La prueba falla porque la funcionalidad aún no está implementada.
    
2. **🟩 Green (Pasar):**  
    Escribís el **mínimo código necesario** para que la prueba pase (sin preocuparte aún por la calidad del código).
    
3. **🟦 Refactor (Refactorizar):**  
    Mejorás el código (lo limpiás, lo optimizás, lo hacés más legible) **sin cambiar su comportamiento**, asegurándote de que las pruebas sigan pasando.
    

---

### 🧩 Ejemplo simple con Node.js + Jest

Supongamos que querés crear una función que **suma dos números**.

**1️⃣ Escribís el test primero (`sum.test.js`):**

```js
const sum = require('./sum');

test('suma 1 + 2 y da 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

**2️⃣ Ejecutás el test → falla**  
Porque `sum.js` todavía no existe o no devuelve lo esperado.

**3️⃣ Escribís el código mínimo (`sum.js`):**

```js
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```

**4️⃣ Corrés los tests → pasa ✅**

**5️⃣ Refactorizás si hace falta**, manteniendo las pruebas pasando.

---

### 🧰 Herramientas comunes en Node.js para TDD

- **Jest** → muy usado por su facilidad y rapidez.
- **Mocha** + **Chai** → combinación clásica y flexible.
- **Supertest** → para probar APIs Express o HTTP.
- **Sinon** → para mocks, spies y stubs (simular funciones o dependencias).

---

### 🚀 Beneficios de usar TDD

- Evitás errores antes de llegar a producción.
- El código queda más modular y testeable.
- Te da confianza al refactorizar.
- Documenta el comportamiento esperado del sistema.

---