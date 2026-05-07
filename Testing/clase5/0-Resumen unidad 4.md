Objetivos del Ciclo de Pruebas

### Procesos Clave:

1. Diseño de Pruebas
    

- Planificación: Definir los objetivos de las pruebas, incluyendo el diseño de casos y conjuntos de prueba, la creación del entorno de pruebas, y la captura de trazabilidad entre condiciones y casos.
    
- Implementación: Preparar todos los elementos necesarios para la ejecución (entornos, datos y procedimientos de prueba).
    

3. Ejecución de Pruebas
    

- Realización de pruebas: Ejecutar los casos diseñados, registrar resultados y documentar defectos.
    
- Trazabilidad: Asegurar el seguimiento de los elementos probados y su relación con los requisitos para un control efectivo del avance de pruebas.
    

5. Presentación de Resultados
    

- Informe de resultados: Al concluir las pruebas, se generan reportes detallados que incluyen casos resueltos, defectos encontrados y métricas de desempeño.
    
- Criterios de lanzamiento: El QA evalúa si el sistema cumple los requisitos mínimos para su despliegue en producción, en base a la severidad y cantidad de defectos.
    

7. Monitoreo en Producción
    

- Pruebas en producción: Validar el funcionamiento del sistema en el entorno final, incluyendo la implementación de hotfixes si se encuentran fallos críticos.
    
- Automatización: Programar pruebas automáticas para monitorear la estabilidad del sistema en producción.
    

Ciclo de Prueba Manual: Desde Planificación hasta Ejecución

El ciclo de pruebas manual se compone de varias etapas, cada una fundamental para asegurar la calidad del producto final. A continuación, se describe el proceso completo, desde la planificación hasta el monitoreo de los resultados, haciendo énfasis en la trazabilidad y en reportes efectivos.

---

#### 1. Planificación de Pruebas

- Objetivo: Definir el enfoque y los objetivos de las pruebas.
    
- Tareas: Crear un plan de pruebas que incluya los casos a evaluar, el alcance, recursos y cronograma, asegurando alineación con los requerimientos del proyecto.
    

#### 2. Diseño de Casos de Prueba

- Objetivo: Desarrollar casos de prueba detallados y específicos.
    
- Tareas: Transformar los requisitos en escenarios de prueba claros y reproducibles, priorizando aquellos que cubran funcionalidades críticas. Se identifican también los datos de prueba y el entorno requerido.
    

#### 3. Implementación de la Prueba

- Objetivo: Preparar todo lo necesario para la ejecución.
    
- Tareas: Configurar entornos de prueba, crear scripts o procedimientos, y organizar los casos en secuencias que faciliten la evaluación del sistema bajo condiciones reales.
    

#### 4. Ejecución de Pruebas

- Objetivo: Realizar las pruebas y capturar los resultados.
    
- Tareas: Ejecutar cada caso de prueba, documentar los defectos, analizar las diferencias entre los resultados esperados y los obtenidos. La trazabilidad es clave para vincular resultados con los requisitos originales y validar la cobertura.
    

#### 5. Monitoreo y Reporte de Resultados

- Objetivo: Comunicar los hallazgos de manera comprensible y útil para la toma de decisiones.
    
- Tareas: Generar informes que incluyan métricas como la cantidad de pruebas pasadas y fallidas, defectos encontrados y su criticidad. Es fundamental que los reportes sean claros y estén bien organizados para facilitar la resolución de problemas y el seguimiento.
    

#### 6. Trazabilidad y Control de Cambios

- Objetivo: Mantener el control sobre cada etapa de prueba y garantizar que se cubran todos los requisitos.
    
- Importancia: La trazabilidad permite un monitoreo preciso del estado de cada requisito y facilita la identificación de áreas de mejora, asegurando que cualquier cambio en el proyecto esté correctamente reflejado en los resultados de prueba.
    

Entornos de prueba

Entorno local: Es la máquina donde se desarrolla el código, es decir, tiene acceso solamente el desarrollador.

Entorno desarrollo: Aquí es donde los desarrolladores pueden unir su código y realizar sus propias pruebas a rasgos generales para ver que funciona correctamente.

Entorno testing/staging: Es donde los testers realizan todas las pruebas necesarias a fin de determinar si el software construido funciona correctamente o no. Es importante tener entornos separados de los desarrolladores para evitar cruzamiento de pruebas y datos. Se trata de simular un entorno productivo.

UAT: Este ambiente es lo más similar al entorno real de producción, aquí suelen destinarse pruebas con usuarios y cliente. Se puede realizar un smoke test final para asegurarse de que todo funciona como se debe y también pruebas en vivo al cliente para que observe como responde el software.

Entorno productivo: Este es el ambiente final el cual tendrán acceso los usuarios finales.

  
  

Introducción a las Pruebas de API

Las APIs (Application Programming Interfaces) permiten la comunicación entre diferentes sistemas o componentes dentro del backend. Actúan como un puente entre aplicaciones, facilitando la interacción y el intercambio de datos a través de un conjunto de reglas, conocidas como endpoints. Los endpoints son URLs en la API que, al ser invocadas, ejecutan acciones específicas como consultar bases de datos o acceder a otros servicios.

---

### Protocolos y Arquitecturas: SOAP y REST

Existen dos enfoques comunes para la transmisión de datos a través de APIs:

- SOAP (Simple Object Access Protocol): Es un protocolo que define un estándar estricto para la comunicación, asegurando transacciones seguras y confiables. Utiliza exclusivamente XML para estructurar los datos y es ideal para aplicaciones donde la seguridad y la consistencia son cruciales. Su implementación es robusta, pero suele ser más lenta y compleja.
    
- REST (Representational State Transfer): Es una arquitectura más ligera y flexible, que permite varios formatos de respuesta como JSON, XML o texto plano. REST utiliza HTTP y es ampliamente adoptado por su simplicidad y velocidad. No impone reglas estrictas, lo que lo hace ideal para aplicaciones web y móviles de rápida implementación.
    

---

### CRUD en APIs

Las APIs suelen soportar el modelo CRUD, que representa las operaciones principales que se pueden realizar en un sistema:

- Create (POST): Agrega nuevos datos al sistema.
    
- Read (GET): Consulta y obtiene datos.
    
- Update (PUT): Modifica datos existentes.
    
- Delete (DELETE): Elimina datos.
    

Cada operación CRUD se realiza a través de llamados a los endpoints correspondientes, asegurando que cada acción se registre y devuelva el estado de éxito o fallo de la solicitud.

  

Tipos de Pruebas y Herramientas de API

Las pruebas de API requieren herramientas especializadas para enviar solicitudes, ver respuestas y verificar el correcto funcionamiento de los servicios. A continuación, se describen algunas de las herramientas más usadas en el ámbito de Testing QA Manual:

#### Postman

Postman es una de las herramientas más populares para realizar pruebas de API debido a su facilidad de uso y funcionalidad completa. Permite realizar solicitudes HTTP (GET, POST, PUT, DELETE), visualizar respuestas y analizar datos en formato JSON. Además, se puede automatizar pruebas y organizar en colecciones para gestionar pruebas complejas en equipo.

- Funcionalidades destacadas: Historial de solicitudes, colecciones de pruebas, generación de scripts para automatización y manejo de variables de entorno.
    
- Interfaz: Una interfaz intuitiva donde se pueden ingresar URLs, seleccionar métodos HTTP y analizar las respuestas en JSON u otros formatos.
    

#### Insomnia REST Client

Insomnia es otra opción preferida por su interfaz amigable y opciones de personalización. Ideal para desarrollar y probar servicios REST, facilita el manejo de datos sensibles al permitir configurar variables y entornos de prueba.

- Funcionalidades destacadas: Interfaz visual atractiva, capacidad para administrar múltiples entornos y generación de reportes de pruebas. Además, permite autenticación fácil para pruebas de APIs seguras.
    
- Interfaz: Sencilla y organizada, donde se configuran solicitudes y se observan respuestas detalladas, facilitando el trabajo en entornos de desarrollo y QA.
    

#### Swagger UI

Swagger facilita la documentación y prueba de APIs, permitiendo a los equipos crear documentación interactiva y ejecutable. Además de definir y probar cada endpoint, ofrece un acceso fácil para conocer y verificar el comportamiento de cada función de la API.

- Funcionalidades destacadas: Generación automática de documentación API, definición de endpoints y especificación de tipos de datos. Swagger UI permite "probar en vivo" las APIs, ayudando en el control y la documentación en tiempo real.
    
- Interfaz: Visualización de la API en formato de documentación interactiva, con opciones para probar y ver los resultados de los endpoints documentados.
    

  

SOAP vs. REST: Comparación

En el desarrollo de APIs, SOAP (Simple Object Access Protocol) y REST (Representational State Transfer) son los enfoques más comunes para la transmisión de datos. Ambos permiten la comunicación entre aplicaciones, pero se diferencian en su estructura y usos.

---

#### SOAP

SOAP es un protocolo estándar que sigue reglas estrictas para garantizar transacciones seguras y confiables. Utiliza XML exclusivamente para estructurar los datos, lo que lo convierte en una opción sólida para aplicaciones que requieren seguridad y consistencia.

- Rapidez: SOAP es más lento debido a su estructura compleja y a la carga de información que maneja.
    
- Complejidad: Requiere más configuraciones, ya que debe cumplir con un conjunto de reglas estrictas.
    
- Seguridad: Ofrece mayor seguridad nativa gracias a sus estándares integrados, como WS-Security, que protege la integridad de los datos.
    
- Popularidad: Menos popular para aplicaciones web modernas, aunque sigue siendo utilizado en entornos empresariales que requieren alta seguridad, como banca y finanzas.
    

#### REST

REST es una arquitectura más flexible y ligera que permite varios formatos de respuesta, incluyendo JSON, XML o texto plano. Su simplicidad y velocidad lo han convertido en la opción más popular para aplicaciones web y móviles.

- Rapidez: REST es más rápido, gracias a su estructura simple y al uso de JSON, que reduce el tiempo de procesamiento.
    
- Complejidad: Su diseño es menos complejo, permitiendo una implementación más rápida y flexible.
    
- Seguridad: Aunque REST no incluye mecanismos de seguridad nativos, se puede combinar con HTTPS para proteger la comunicación.
    
- Popularidad: Muy popular en aplicaciones web y móviles, especialmente donde la velocidad y flexibilidad son prioritarias.
    

  
**