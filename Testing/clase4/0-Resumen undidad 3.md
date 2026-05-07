Introducción al Ciclo de Desarrollo de Software

El ciclo de vida en el desarrollo de software es un proceso estructurado que guía el avance de un proyecto desde la identificación de necesidades hasta su entrega final. Este ciclo abarca fases fundamentales como análisis, diseño, desarrollo y pruebas, y cada una está influenciada por la metodología elegida, lo que impacta el rol de Testing QA en cada etapa.

### Modelos Secuenciales

Modelo en Cascada: Este es un modelo lineal donde cada fase se completa antes de iniciar la siguiente. Es útil para proyectos con requerimientos claros y estables. Las pruebas en este modelo se realizan al finalizar el desarrollo, lo que puede dificultar la detección temprana de errores.

Modelo en V: Similar al cascada, el modelo en V vincula cada fase de desarrollo con una fase de pruebas específica. Por ejemplo, los requisitos tienen pruebas de aceptación asociadas, y el diseño tiene pruebas de integración. Esta estructura permite identificar y corregir defectos antes de que se acumulen en fases posteriores, aunque es menos flexible ante cambios.

### Modelos Iterativos e Incrementales

Modelo Iterativo: En este enfoque, se desarrolla una versión inicial básica del producto que se va mejorando en ciclos (iteraciones) sucesivos. Cada ciclo incluye desarrollo, pruebas y entrega de una versión funcional, lo que permite ajustes constantes y retroalimentación continua.

Agile-Scrum: Agile es una metodología incremental y flexible, ideal para proyectos en constante evolución. En Scrum, el desarrollo se organiza en sprints (ciclos cortos de trabajo). Cada sprint resulta en una versión funcional del producto que incluye nuevas funcionalidades o mejoras. Este enfoque facilita el testing temprano y frecuente, permitiendo identificar errores en fases iniciales.

  
  

Comparativa entre Metodologías Ágiles y Tradicionales

Las metodologías ágiles y las metodologías tradicionales representan dos enfoques diferentes para gestionar el desarrollo de software, cada uno con características y ventajas específicas.

### Metodologías Tradicionales

Las metodologías tradicionales, como el modelo en cascada, son secuenciales y siguen una estructura rígida. En estas metodologías:

- Cada fase (análisis, diseño, desarrollo, pruebas) se completa antes de iniciar la siguiente, lo que dificulta realizar cambios durante el proyecto.
    
- Las pruebas suelen ser más manuales y se ejecutan principalmente al final del desarrollo, lo que puede aumentar el costo de corregir errores detectados en etapas tardías.
    

### Metodologías Ágiles

En contraste, las metodologías ágiles, como Agile-Scrum, se basan en ciclos iterativos e incrementales:

- Son flexibles, permitiendo adaptaciones constantes según las necesidades del cliente o del proyecto.
    
- Las pruebas son parte integral de cada ciclo (sprint), priorizando la automatización y las pruebas unitarias para mejorar la eficiencia y detectar errores tempranamente. Esto permite liberar versiones funcionales al final de cada iteración.
    

Este enfoque ágil reduce la dependencia de pruebas funcionales manuales, enfocándose en la calidad desde las primeras etapas y facilitando el desarrollo de software adaptable y enfocado en el usuario.

  

Herramienta de Gestión JIRA

JIRA es una herramienta de gestión de proyectos ampliamente utilizada en el ámbito de QA y desarrollo de software. Facilita la coordinación y seguimiento de tareas, organización del backlog, y el control de sprints, permitiendo una gestión estructurada del proceso de pruebas. A continuación, se describen los elementos clave en JIRA y cómo benefician al equipo de QA:

1. Backlog: Es una lista priorizada de tareas, historias de usuario, bugs y mejoras. En el backlog, el equipo QA puede visualizar todos los elementos pendientes de pruebas y priorizar el trabajo según los objetivos del proyecto.
    
2. Sprints: Los sprints son períodos de trabajo donde se agrupan tareas para completarlas en un tiempo específico. JIRA permite planificar y asignar tareas para cada sprint, ayudando al equipo QA a enfocarse en entregas iterativas y mejorando el seguimiento de cada fase del desarrollo.
    
3. Tickets:
    

- Bugs/Defectos: Permiten reportar y rastrear errores encontrados. Cada bug incluye una descripción del problema, pasos para reproducirlo y la prioridad, lo que facilita la corrección.
    
- Historias de Usuario: Estas son descripciones de funcionalidades desde la perspectiva del usuario final. QA usa estas historias para entender el propósito de cada característica y definir los criterios de aceptación en las pruebas.
    
- Tareas: Son acciones específicas que el equipo debe realizar para cumplir con los requisitos de un proyecto. Las tareas pueden incluir actividades de configuración, revisión de documentos o análisis de calidad.
    
- Épicas: Son proyectos grandes que agrupan varias historias de usuario y tareas relacionadas. Las épicas ayudan a organizar el trabajo en grandes secciones funcionales, facilitando el seguimiento de avances en características complejas.
    

JIRA permite centralizar toda esta información, mejorando la comunicación y transparencia entre los equipos de QA y desarrollo. La herramienta agiliza el proceso de pruebas y asegura que todos los elementos necesarios estén documentados y priorizados de acuerdo con el plan del proyecto.

Otras herramientas que vale la pena destacar con Azure DevOps y TestLink que también son conocidas y muy utilizadas.

  

Planificación de Pruebas y Creación de Casos de Prueba

La planificación de pruebas en QA incluye varios elementos clave que organizan y estructuran el proceso de validación del software, asegurando que se cumplan los objetivos de calidad.

### Plan de Pruebas

El Plan de Pruebas es un documento que establece el alcance, enfoque y criterios de aceptación de las pruebas. Define los recursos, cronograma, objetivos y riesgos asociados al proceso de QA. Este plan guía al equipo en la ejecución de pruebas, alineando las actividades con los requerimientos del proyecto​.

### Historias de usuario, criterios de aceptación y requerimientos

  

Las historias de usuario son un documento en donde se detalla al equipo completo encargado de la construcción y testing del software que es lo que se va a construir, prototipos de cómo se debe ver, características a tener en cuenta, criterios de aceptación y requerimientos. Cuando se va a construir una nueva funcionalidad si no es muy grande se puede realizar una sola historia, si la funcionalidad a construir es muy grande o abarca muchas funcionalidades entonces se recomienda separar en varias historias más chicas para que se pueda trabajar ordenadamente.

Los requerimientos definen técnicamente la funcionalidad a construir pero sin entrar en detalles.

Los criterios de aceptación especifican el comportamiento mínimo esperado para que una funcionalidad se considere correcta. Es escrito en colaboración con los Product Owners y suele seguir un formato como "Dado, Cuando, Entonces" para detallar las condiciones en que el software debería operar correctamente​(Copia de Clase 5 - Plan…)

### Casos de Prueba

Los casos de prueba son documentos que detallan pasos específicos para verificar si una funcionalidad cumple con los criterios definidos. Existen dos tipos principales:

- Casos de Prueba Positivos: Diseñados para asegurar que el sistema funcione correctamente con datos válidos, siguiendo el flujo esperado del usuario.
    
- Casos de Prueba Negativos: Valoran cómo responde el sistema a datos incorrectos o fuera de lo común, ayudando a identificar y prevenir errores.
    

Estos casos son esenciales en el proceso de QA, pues ofrecen una guía clara de validación de funcionalidades, permitiendo detectar fallos en fases tempranas y garantizar que el producto cumpla con los estándares de calidad.

Para la construcción de casos de prueba los testers se deben basar en la documentación (Historias de usuario, requerimientos y criterios de aceptación), en base al análisis que se realice de estos documentos es que surgirán tantos casos de prueba como sean necesarios para que se pueda confirmar que el software cumple o no con los requerimientos y criterios de aceptación definidos. Es muy importante el paso del análisis y escritura de casos de prueba ya que es el respaldo que tendremos de nuestro trabajo.

Por lo general el caso de prueba tendrá información basica: Nombre adecuado y representativo de lo que se quiere validar, un código unico de identificación, pasos a seguir para ejecutarlo, resultado esperado y resultado obtenido. Cuando el resultado esperado y el obtenido no son iguales es que podriamos decir que estamos en presencia de un defecto.

  
  
**