## Objetivos del Ciclo de Pruebas

**Procesos Clave:**

**1- Diseño de Pruebas**

- Planificación: Definir los objetivos de las pruebas, incluyendo el diseño de casos y conjuntos de prueba, la creación del entorno de pruebas, y la captura de trazabilidad entre condiciones y casos.
    
- Implementación: Preparar todos los elementos necesarios para la ejecución (entornos, datos y procedimientos de prueba).
    

**2- Ejecución de Pruebas**

- Realización de pruebas: Ejecutar los casos diseñados, registrar resultados y documentar defectos.
    
- Trazabilidad: Asegurar el seguimiento de los elementos probados y su relación con los requisitos para un control efectivo del avance de pruebas.
    

**3- Presentación de Resultados**

- Informe de resultados: Al concluir las pruebas, se generan reportes detallados que incluyen casos resueltos, defectos encontrados y métricas de desempeño.
    
- Criterios de lanzamiento: El QA evalúa si el sistema cumple los requisitos mínimos para su despliegue en producción, en base a la severidad y cantidad de defectos.
    

**4- Monitoreo en Producción**

- Pruebas en producción: Validar el funcionamiento del sistema en el entorno final, incluyendo la implementación de hotfixes si se encuentran fallos críticos.
    
- Automatización: Programar pruebas automáticas para monitorear la estabilidad del sistema en producción.
    

## Introducción a las Pruebas de API

Las APIs (Application Programming Interfaces) permiten la comunicación entre diferentes sistemas o componentes dentro del backend. Actúan como un puente entre aplicaciones, facilitando la interacción y el intercambio de datos a través de un conjunto de reglas, conocidas como endpoints. Los endpoints son URLs en la API que, al ser invocadas, ejecutan acciones específicas como consultar bases de datos o acceder a otros servicios.

**Protocolos y Arquitecturas: SOAP y REST**.

Existen dos enfoques comunes para la transmisión de datos a través de APIs:

- SOAP (Simple Object Access Protocol): Es un protocolo que define un estándar estricto para la comunicación, asegurando transacciones seguras y confiables. Utiliza exclusivamente XML para estructurar los datos y es ideal para aplicaciones donde la seguridad y la consistencia son cruciales. Su implementación es robusta, pero suele ser más lenta y compleja.
    
- REST (Representational State Transfer): Es una arquitectura más ligera y flexible, que permite varios formatos de respuesta como JSON, XML o texto plano. REST utiliza HTTP y es ampliamente adoptado por su simplicidad y velocidad. No impone reglas estrictas, lo que lo hace ideal para aplicaciones web y móviles de rápida implementación.
    

**CRUD en APIs**

Las APIs suelen soportar el modelo CRUD, que representa las operaciones principales que se pueden realizar en un sistema:

- Create (POST): Agrega nuevos datos al sistema.
    
- Read (GET): Consulta y obtiene datos.
    
- Update (PUT): Modifica datos existentes.
    
- Delete (DELETE): Elimina datos.
    

Cada operación CRUD se realiza a través de llamados a los endpoints correspondientes, asegurando que cada acción se registre y devuelva el estado de éxito o fallo de la solicitud.