  
Cuando hablamos de **tipos de testing de software** nos referimos a las **diferentes formas de probar un sistema** según el objetivo, la técnica o el enfoque que se utilice.

---

## 🔹 **Principales tipos de testing**

### 1. **Según el objetivo**

- **Funcional** → Verifica que el sistema haga lo que debería hacer según los requisitos.
    - Ejemplo: si hago login con usuario y contraseña correctos, debo entrar.
- **No funcional** → Evalúa características de calidad que no están ligadas directamente a funciones específicas.
    - Ejemplo: rendimiento, seguridad, usabilidad, compatibilidad, etc.

---

### 2. **Según la forma de ejecución**

- **Manual** → El tester ejecuta los casos de prueba sin herramientas automáticas.
- **Automatizado** → Se usan scripts/herramientas (Selenium, Cypress, JMeter) para ejecutar pruebas automáticamente.

---

### 3. **Según el acceso al código**

- **Caja negra (Black Box)** → Se prueba desde la perspectiva del usuario, sin mirar el código.
    - Ejemplo: ingresar datos en un formulario y validar el resultado.
- **Caja blanca (White Box)** → Se prueba la lógica interna y flujos del código.
    - Ejemplo: validar todas las ramas de un `if/else`.
- **Caja gris (Gray Box)** → Combinación: se conocen algunos detalles internos del sistema.

---

### 4. **Algunos tipos comunes de testing**

- **Unit Testing** → Funciones/métodos individuales.
- **Integration Testing** → Comunicación entre módulos.
- **System Testing** → El sistema completo.
- **Acceptance Testing** → Validación por parte del cliente/usuario.
- **Regression Testing** → Asegurar que nuevas funcionalidades no rompen lo que ya funcionaba.
- **Smoke Testing** → Verificar que lo básico funciona tras un build.
- **Sanity Testing** → Validar rápidamente un cambio específico.
- **Performance Testing** → Velocidad y respuesta bajo carga.
- **Load/Stress Testing** → Cómo responde el sistema con muchos usuarios o en situaciones extremas.
- **Security Testing** → Verificar vulnerabilidades y accesos no autorizados.
- **Usability Testing** → Qué tan fácil es usar el sistema.
- **Compatibility Testing** → Probar en distintos navegadores, dispositivos, SO.
- **Exploratory Testing** → Sin guion fijo, investigando la app.
- **Alpha/Beta Testing** → Pruebas previas al lanzamiento con usuarios internos (alpha) o externos (beta).

---

📊 **Ejemplo de clasificación en tabla**

| Categoría    | Tipo de Testing    | Ejemplo                            |
| ------------ | ------------------ | ---------------------------------- |
| Funcional    | Pruebas de sistema | Flujo completo de compra online    |
| No funcional | Performance        | Simular 1000 usuarios concurrentes |
| Ejecución    | Manual             | QA probando la app en un celular   |
| Ejecución    | Automatizado       | Script Selenium validando login    |
| Caja negra   | Usabilidad         | Ver si el usuario entiende la UI   |
| Caja blanca  | Unit Testing       | Probar función `calcularIVA()`     |

---

👉 Como ves, los **niveles de testing** (unitario, integración, sistema, aceptación) son una cosa, y los **tipos de testing** son las distintas maneras de abordar esas pruebas.

---

Cuando hablamos de **todos los tipos de testing**, no hay un único listado universal porque cada organización o estándar los clasifica distinto. Pero sí podemos agruparlos en **grandes categorías** y detallar los más relevantes en la industria.

---

## 📌 **Clasificación de Tipos de Testing**

### 🔹 1. **Según el objetivo**

👉 Diferencian si probamos **qué hace el sistema** o **cómo lo hace**.

#### ✅ **Funcional**

- **Unit Testing** → Una función/método aislado.
    
- **Integration Testing** → Interacción entre módulos.
    
- **System Testing** → Todo el sistema como un conjunto.
    
- **Acceptance Testing** → Validación por el cliente.
    
- **Regression Testing** → Comprobar que algo nuevo no rompe lo viejo.
    
- **Smoke Testing** → Verificación rápida de lo básico (“¿el build está vivo?”).
    
- **Sanity Testing** → Validar un cambio específico antes de probar más.
    

#### ✅ **No Funcional**

- **Performance Testing** → Tiempo de respuesta, uso de recursos.
    
- **Load Testing** → Cómo funciona bajo carga normal o esperada.
    
- **Stress Testing** → Llevado al límite (más usuarios de los soportados).
    
- **Scalability Testing** → Qué tan bien escala el sistema si aumentan usuarios/datos.
    
- **Security Testing** → Vulnerabilidades, ataques, accesos no autorizados.
    
- **Usability Testing** → Qué tan fácil de usar es el sistema.
    
- **Compatibility Testing** → Navegadores, dispositivos, SO, versiones.
    
- **Reliability Testing** → Estabilidad a lo largo del tiempo.
    
- **Maintainability Testing** → Qué tan fácil es modificar el sistema.
    
- **Compliance Testing** → Cumplimiento de normativas (ej. PCI DSS, GDPR).
    

---

### 🔹 2. **Según la ejecución**

👉 Cómo se llevan a cabo.

- **Manual Testing** → El tester ejecuta los casos paso a paso.
    
- **Automated Testing** → Scripts y herramientas (Selenium, Cypress, JMeter).
    

---

### 🔹 3. **Según el conocimiento del código**

👉 Grado de visibilidad interna del sistema.

- **Black Box Testing (Caja negra)** → Sin ver código, como usuario.
    
- **White Box Testing (Caja blanca)** → Con conocimiento del código interno.
    
- **Gray Box Testing (Caja gris)** → Con algo de conocimiento del sistema.
    

---

### 🔹 4. **Según el momento del ciclo de vida**

- **Alpha Testing** → Prueba interna antes del release.
    
- **Beta Testing** → Usuarios reales externos prueban el sistema antes del lanzamiento.
    
- **Acceptance Testing** → Validación final con cliente/negocio.
    

---

### 🔹 5. **Tipos especializados**

- **Exploratory Testing** → Sin guion fijo, se explora la app con intuición.
    
- **Ad-hoc Testing** → Similar a exploratoria, pero sin documentación.
    
- **Monkey Testing** → Pruebas aleatorias sin lógica (ej. introducir datos absurdos).
    
- **Recovery Testing** → Qué pasa tras una caída del sistema.
    
- **Installation/Uninstallation Testing** → Validar que la instalación sea correcta.
    
- **Localization/Internationalization Testing** → Verificar traducciones, formatos de fecha/moneda.
    
- **A/B Testing** → Comparar 2 versiones del software para ver cuál funciona mejor.
    

---

📊 **Resumen en tabla**

|Categoría|Tipos|
|---|---|
|Funcional|Unit, Integration, System, Acceptance, Regression, Smoke, Sanity|
|No funcional|Performance, Load, Stress, Scalability, Security, Usability, Compatibility, Reliability, Maintainability, Compliance|
|Ejecución|Manual, Automatizado|
|Acceso al código|Caja negra, Caja blanca, Caja gris|
|Ciclo de vida|Alpha, Beta, Acceptance|
|Especiales|Exploratoria, Ad-hoc, Monkey, Recovery, Installation, Localization, A/B|

---

👉 En un proyecto real, no se aplican **todos**, sino que se seleccionan según **riesgo, criticidad, presupuesto y tiempo**.

¿Querés que te prepare un **mapa visual más completo** con _todos estos tipos de testing organizados como un árbol_ para que lo tengas de referencia?