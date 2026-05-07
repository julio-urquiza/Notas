# Introducción a las pruebas no funcionales

Las pruebas no funcionales son una pieza clave en el aseguramiento de la calidad, ya que se enfocan en aspectos críticos del sistema que trascienden la simple funcionalidad. Su propósito es evaluar factores como la estabilidad, seguridad, rendimiento, y la capacidad de respuesta del sistema ante diferentes condiciones. A diferencia de las pruebas funcionales, que verifican si el sistema realiza las acciones esperadas, las pruebas no funcionales buscan asegurar que el sistema pueda sostener un rendimiento óptimo y seguro en entornos de uso real y bajo circunstancias de estrés.

#### Rol en la Estabilidad y Seguridad del Sistema

Estas pruebas son esenciales para garantizar que el sistema no solo funcione bien, sino que también sea confiable y robusto. Las pruebas de rendimiento, por ejemplo, evalúan la capacidad del sistema para gestionar grandes volúmenes de datos o conexiones simultáneas sin degradarse. Las pruebas de seguridad, por otro lado, ayudan a identificar y mitigar vulnerabilidades, previniendo posibles ataques que podrían comprometer los datos y la privacidad de los usuarios.

Al implementar pruebas no funcionales, se contribuye a desarrollar un sistema que no solo cumpla con sus funciones, sino que también sea capaz de mantenerse operativo y seguro en el tiempo. Esto es especialmente importante en aplicaciones de alta disponibilidad, donde el objetivo es minimizar fallos y asegurar una experiencia de usuario de calidad, incluso en momentos de máxima demanda. En suma, las pruebas no funcionales refuerzan la calidad del sistema en sus dimensiones de confiabilidad, escalabilidad, y seguridad, asegurando así una base sólida para el funcionamiento efectivo del software.

# Tipos de pruebas no funcionales

### Pruebas de Estrés

Las pruebas de estrés se aplican para evaluar la estabilidad de un sistema bajo condiciones extremas. Estas pruebas ayudan a identificar el punto de fallo del sistema al sobrecargarlo con solicitudes más allá de su capacidad habitual. Se realizan en momentos de alta demanda o en eventos especiales, como el Black Friday o transmisiones masivas, para garantizar que el sistema pueda manejar picos sin fallar. Esto permite ajustar la infraestructura y prever posibles mejoras en la capacidad del sistema.

### Pruebas de Seguridad

Estas pruebas buscan detectar vulnerabilidades que podrían comprometer la integridad del sistema y la confidencialidad de los datos. Se centran en aspectos como autenticación, gestión de sesiones y validación de entradas para prevenir ataques, como la inyección SQL y el Cross Site Scripting. Las pruebas de seguridad son esenciales durante el desarrollo para reducir el riesgo de ataques y proteger la información sensible del sistema​.

### Pruebas de Carga

Las pruebas de carga miden el rendimiento del sistema bajo un número elevado de usuarios concurrentes, verificando si las funciones y respuestas siguen siendo óptimas. Este tipo de prueba se utiliza cuando se necesita asegurar que el sistema puede manejar un flujo constante de solicitudes sin afectar su tiempo de respuesta. Es ideal para evaluar si el sistema puede mantenerse operativo durante el uso intensivo​.

### Pruebas de Resistencia

Estas pruebas son similares a las de carga, pero se enfocan en verificar la estabilidad del sistema bajo un uso prolongado y continuo. La prueba de resistencia se utiliza para identificar posibles degradaciones en el rendimiento o fallos que podrían surgir debido al tiempo de exposición a una alta carga. Estas pruebas son útiles para determinar si el sistema puede soportar una carga constante durante períodos largos sin afectarse.

  

# Conceptos básicos de agilidad

Las metodologías ágiles surgen como una respuesta a los desafíos en el desarrollo de software, priorizando la flexibilidad, la colaboración y la capacidad de adaptarse al cambio constante. En 2001, un grupo de profesionales de la industria de sistemas creó el Manifiesto Ágil, estableciendo cuatro valores esenciales:

1. Individuos e Interacciones sobre Procesos y Herramientas: Las personas y su comunicación efectiva son el núcleo del desarrollo ágil. Se enfatiza la importancia de la colaboración continua y fluida entre los miembros del equipo, favoreciendo la eficiencia y el entendimiento mutuo por encima de los procesos rígidos o el uso exclusivo de herramientas.
    
2. Software Funcionando sobre Documentación Extensiva: El enfoque ágil se centra en ofrecer al cliente un producto funcional lo más pronto posible. La entrega temprana de un software operativo permite obtener retroalimentación rápida y, a su vez, ajustar el desarrollo a las necesidades reales del cliente, acelerando la llegada al mercado.
    
3. Colaboración con el Cliente sobre Negociación Contractual: La comunicación constante con el cliente es esencial para alinear expectativas y evitar malentendidos o entregas incorrectas. Esta colaboración continua permite adaptarse mejor a las necesidades reales del usuario y evita pérdidas de tiempo y recursos en desarrollos equivocados.
    
4. Respuesta ante el Cambio sobre Seguir un Plan: La adaptabilidad es clave en entornos ágiles. En lugar de seguir estrictamente un plan, el desarrollo ágil favorece la flexibilidad, permitiendo modificaciones en los requisitos incluso en etapas avanzadas del proyecto. Esto asegura que el producto final se ajuste a las demandas cambiantes del mercado o del cliente.
    

Los principios ágiles promueven, además, un entorno de trabajo sostenible y constante, donde la comunicación cara a cara es el medio más eficiente para la transmisión de información. La simplicidad, la mejora continua y el diseño de sistemas auto-organizados son elementos fundamentales que permiten a los equipos de desarrollo ágil responder rápidamente a los cambios, manteniendo la calidad y el valor del software entregado.

# Roles y enfoques en agilidad

### Roles en Equipos Ágiles

En los equipos ágiles, existen varios roles clave que facilitan la entrega continua y eficiente de valor al cliente. Estos roles pueden variar ligeramente según el enfoque o metodología ágil aplicada, pero comúnmente incluyen:

  

- Product Owner: Responsable de definir y priorizar las características y funcionalidades del producto, asegurando que el equipo trabaje en lo más valioso para el negocio.
    
- Scrum Master: Facilita el proceso ágil, eliminando obstáculos y asegurando que las prácticas ágiles se mantengan.
    
- Equipo de Desarrollo: Un grupo multidisciplinario que trabaja colaborativamente para desarrollar, probar y entregar incrementos del producto. Suelen ser auto-organizados y están comprometidos con la calidad.
    

### Enfoques Populares en Agilidad

En agilidad, existen diversos enfoques o frameworks que guían el proceso de desarrollo. Entre los más destacados están:

  

- SCRUM: Un marco de trabajo que organiza el trabajo en iteraciones llamadas “sprints”, donde el equipo busca entregar un incremento de producto funcional. Incluye elementos como backlog de producto, backlog de sprint, sprints, definición de "hecho" y eventos de revisión.
    
- Kanban: Una metodología centrada en la visualización y optimización del flujo de trabajo, utilizando un tablero Kanban para gestionar las tareas y limitar el trabajo en curso (WIP) para mejorar la eficiencia.
    
- Programación Extrema (XP): Fomenta la calidad del software mediante prácticas como desarrollo en parejas, retroalimentación constante, pruebas automatizadas y la entrega continua. Sus valores incluyen simplicidad, comunicación y respeto.
    

### Ceremonias Clave en Equipos Ágiles

Las ceremonias ágiles son momentos estructurados para promover la colaboración y la mejora continua dentro del equipo. Entre las principales ceremonias, se encuentran:

  

- Daily (Reunión Diaria): Una reunión breve en la que cada miembro comparte sus progresos, obstáculos y próximos pasos, manteniendo al equipo alineado y comunicativo.
    
- Sprint Planning (Planificación del Sprint): Espacio donde el equipo planifica las tareas a realizar en el sprint, basándose en las prioridades del Product Owner y la capacidad del equipo.
    
- Sprint Review (Revisión del Sprint): También conocida como "demo", es el momento en el que se muestra el progreso al Product Owner y otros interesados, recibiendo retroalimentación valiosa.
    
- Sprint Retrospective (Retrospectiva del Sprint): Al finalizar el sprint, el equipo reflexiona sobre lo que funcionó bien y qué puede mejorarse, fomentando un ciclo de mejora continua.
    

  

Este enfoque ágil y colaborativo busca que los equipos sean más adaptables y orientados a la calidad, asegurando que el producto se ajuste a las necesidades cambiantes del negocio y de los usuarios.

  

# Responsabilidades del Tester Ágil

### Rol del Tester en un Equipo Ágil

El tester en un equipo ágil cumple un papel esencial en la garantía de calidad continua y en la colaboración directa con el equipo de desarrollo, el negocio, y otros actores clave. Este profesional no solo verifica el producto en desarrollo, sino que también facilita una retroalimentación constante sobre el avance de las pruebas y la calidad general del proyecto.

#### Principales Tareas del Tester en un Equipo Ágil

1. Implementación de Estrategias de Prueba: El tester participa activamente en la planificación de pruebas durante las reuniones de sprint. Se asegura de que las pruebas adecuadas estén programadas y que respondan a los objetivos del sprint y las expectativas del negocio.
    

  

2. Colaboración en Reuniones: Es común que el tester participe en reuniones de planificación, retros, y en las dailies (reuniones diarias), donde aporta ideas de mejora y discute el estado de las pruebas, retos y requerimientos específicos.
    

  

3. Gestión de Entornos de Prueba: Es responsable de configurar y mantener los entornos y datos necesarios para las pruebas, lo que garantiza que las pruebas sean precisas y reproducibles.
    

  

4. Entrenamiento y Asesoramiento: Parte de su rol incluye educar al equipo en los aspectos clave de la prueba de software, fomentando una cultura de calidad y mejorando la comprensión de los criterios de aceptación de las historias de usuario.
    

  

5. Adaptación y Flexibilidad: El tester ágil responde de manera proactiva a los cambios en los requisitos y ajusta sus casos de prueba según sea necesario, asegurando que el producto continúe alineado con las expectativas del cliente.
    

#### Contribución a la Calidad Continua

El tester ágil se asegura de que la calidad sea un objetivo compartido por todo el equipo. Trabaja en la implementación de prácticas como el Desarrollo Guiado por Pruebas (TDD), el Desarrollo Guiado por Pruebas de Aceptación (ATDD) y el Desarrollo Guiado por Comportamiento (BDD), que ayudan a integrar los criterios de prueba desde la creación de las historias de usuario. Estas metodologías permiten a todos los miembros del equipo comprender las expectativas de calidad y asegurar que el software se construya de acuerdo a ellas.

  

En un equipo ágil, la contribución del tester es clave para lograr una entrega continua de valor y mantener la calidad de manera sostenible en cada iteración.

  

# Pruebas exploratorias

Las pruebas exploratorias son una estrategia esencial en proyectos ágiles, utilizada para identificar comportamientos inesperados en el software de manera rápida y efectiva. Este enfoque permite que los testers exploren el sistema sin un guion rígido, adaptándose en tiempo real a lo que observan y ajustando sus pruebas a medida que encuentran áreas problemáticas o inesperadas. Este tipo de pruebas se basa en la experiencia, curiosidad y juicio crítico del tester para descubrir fallos o comportamientos imprevistos que no siempre son detectados en pruebas planificadas.

Dentro del contexto ágil, donde la adaptabilidad y la velocidad son fundamentales, las pruebas exploratorias complementan las pruebas automatizadas y tradicionales al centrarse en aspectos que no siempre están cubiertos por casos de prueba predefinidos. Permiten detectar defectos en etapas tempranas, favoreciendo el ciclo de retroalimentación continua. Esta práctica es especialmente útil en metodologías ágiles como Scrum, donde la entrega de incrementos funcionales es frecuente y se espera que los testers interactúen con nuevas versiones de software en cada sprint.

# Pruebas de regresión

Cuando se va a deployar en un ambiente productivo una nueva versión o funcionalidades (sea página web o aplicación), se realizan las llamadas “regresiones” que consta de volver a ejecutar los casos de prueba de funcionalidades criticas o importantes sumadas a los casos de prueba de la nueva funcionalidad que será vista por los usuarios, esto se realiza con el fin de verificar que lo que funcionaba siga funcionando y no se haya “roto” algo que pueda ocasionar inconvenientes productivos. Cuando no se dispone de mucho tiempo para realizar estas pruebas entonces se trata de priorizar al menos los “casos felices” para verificar que al menos funcionen correctamente las funcionalidades viejas.

Si el tiempo es muy acotado y no se llega a ejecutar una regresión entonces se pueden hacer las llamadas “pruebas de humo” o “smoke test” que son pruebas mucho mas rápidas que la regresión porque no re-ejecutamos casos de prueba sino que rápidamente navegamos por el software a fin de ver que este funcione correctamente.

El optar por regresión o prueba de humo dependerá de lo que se decida en el equipo y tiempo/costo de realizar una u otra.
