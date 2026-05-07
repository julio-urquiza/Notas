Muchas veces **QA (Quality Assurance)** y **QC (Quality Control)** se confunden porque ambos están relacionados con la calidad, pero en realidad apuntan a momentos y enfoques distintos dentro del ciclo de desarrollo.

---

### 🔹 **QA (Quality Assurance – Aseguramiento de la Calidad)**

- **Enfoque:** Preventivo. Busca **evitar defectos antes de que ocurran**.
- **Qué hace:** Define procesos, metodologías, estándares y buenas prácticas.
- **Responsable de:**
    - Establecer políticas de calidad.
    - Definir flujos de trabajo, documentación y métricas.
    - Asegurar que el equipo siga metodologías (Agile, Scrum, ISO, CMMI, etc.).
- **Ejemplo:**
    - Crear un checklist de code review.
    - Definir cómo se deben escribir los casos de prueba.
    - Establecer integraciones continuas (CI/CD) que verifiquen calidad del código.

👉 **QA = “Hacer las cosas bien desde el inicio”**.

---

### 🔹 **QC (Quality Control – Control de Calidad)**

- **Enfoque:** Correctivo. Busca **detectar defectos ya existentes** en el producto.
- **Qué hace:** Se centra en el producto final o intermedio.
- **Responsable de:**
    - Ejecutar pruebas (manuales o automáticas).
    - Detectar errores o inconsistencias.
    - Validar que el software cumpla con los requisitos funcionales y no funcionales.
- **Ejemplo:**
    - Probar que una API devuelve los datos correctos.
    - Detectar un bug en la interfaz de usuario.
    - Verificar tiempos de respuesta con JMeter.

👉 **QC = “Comprobar que lo que hicimos funciona como debe”**.

---

### ⚖️ Resumen de la diferencia

|Aspecto|QA (Aseguramiento)|QC (Control)|
|---|---|---|
|Enfoque|Preventivo (evita errores)|Correctivo (detecta errores)|
|Objetivo|Mejorar procesos|Validar producto|
|Cuándo actúa|Durante todo el ciclo de desarrollo|Después o durante entregables|
|Actividad típica|Definir estándares, metodologías, auditorías|Testing, validación, verificación|
|Resultado|Procesos de calidad|Producto de calidad|
