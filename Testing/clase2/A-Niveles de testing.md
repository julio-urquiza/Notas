Los **niveles de testing** son las **etapas en las que se realizan las pruebas dentro del ciclo de vida del desarrollo de software**. Cada nivel tiene un objetivo y un alcance distinto, y juntos garantizan que tanto las partes individuales como el sistema completo funcionen bien.

---

## 🔹 **Los 4 niveles clásicos de testing**

### 1. **Pruebas unitarias (Unit Testing)**

- **Qué se prueba:** La unidad más pequeña del software (una función, un método, una clase).
    
- **Quién las hace:** Principalmente los desarrolladores.
    
- **Objetivo:** Verificar que cada unidad de código funciona de manera aislada.
    
- **Ejemplo:** Probar que la función `calcularIVA(100)` devuelva `21`.
    

---

### 2. **Pruebas de integración (Integration Testing)**

- **Qué se prueba:** La interacción entre varios módulos o servicios.
    
- **Quién las hace:** Devs o testers.
    
- **Objetivo:** Detectar problemas en la comunicación entre componentes.
    
- **Ejemplo:** Probar que el módulo de pagos se integre correctamente con el módulo de carrito.
    

---

### 3. **Pruebas de sistema (System Testing)**

- **Qué se prueba:** El sistema completo como un todo.
    
- **Quién las hace:** Equipo de QA.
    
- **Objetivo:** Validar que el software cumple con los requisitos funcionales y no funcionales.
    
- **Ejemplo:** Simular el proceso completo de compra en un e-commerce (buscar producto → agregar al carrito → pagar → recibir confirmación).
    

---

### 4. **Pruebas de aceptación (Acceptance Testing)**

- **Qué se prueba:** El sistema desde la perspectiva del **cliente o usuario final**.
    
- **Quién las hace:** Cliente, usuario clave o QA en representación.
    
- **Objetivo:** Asegurar que el producto satisface las necesidades de negocio.
    
- **Ejemplo:** El cliente verifica que en su app bancaria puede transferir dinero correctamente y recibir notificaciones.
    

---

📊 **Resumen en tabla**

|Nivel|Enfoque|Responsable|Ejemplo|
|---|---|---|---|
|Unitario|Una función o clase|Dev|`calcularIVA(100)` devuelve 21|
|Integración|Módulos entre sí|Dev/QA|Carrito ↔ Módulo de pagos|
|Sistema|Todo el sistema|QA|Flujo completo de compra online|
|Aceptación|Necesidades de negocio|Cliente/QA|Transferencia en app bancaria|

---

👉 A veces, en proyectos grandes también se habla de **otros niveles adicionales**, como:

- **Pruebas de regresión** (asegurar que algo nuevo no rompe lo viejo).
    
- **Pruebas alfa y beta** (antes del lanzamiento oficial, con usuarios reales).
    

---

¿Querés que te arme un **ejemplo de flujo real con todos los niveles aplicados** (por ejemplo, en un sistema de login y gestión de usuarios) para que lo veas más claro?