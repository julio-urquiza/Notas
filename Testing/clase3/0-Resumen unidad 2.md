# Introducción a los Niveles y Tipos de Testing  

Los niveles y tipos de testing son fundamentales en el proceso de pruebas de software. Cada uno permite estructurar y gestionar las actividades de prueba para asegurar que el sistema cumple con los estándares de calidad esperados. Es importante entender cómo se aplican estos niveles y tipos para evaluar y optimizar el rendimiento y funcionalidad del software en diferentes etapas.

#### Niveles de Testing

1. Prueba de Componente (Unitarias): Se enfoca en los componentes individuales de software. Su objetivo es verificar que cada componente funcione como se espera, asegurando calidad y detectando defectos antes de avanzar a niveles superiores.
    
2. Prueba de Integración: Evalúa la interacción entre componentes. Es crucial para detectar problemas en las interfaces que no se manifiestan en las pruebas unitarias.
    
3. Prueba de Sistema: Valida el comportamiento de todo el sistema. Aquí se comprueba si el software responde correctamente a requerimientos funcionales y no funcionales, acercándose al entorno de producción.
    
4. Prueba de Aceptación: Su propósito es validar que el sistema cumpla con las expectativas del usuario y se ajuste a sus necesidades. Esto suele involucrar al usuario final y otras partes interesadas.
    

#### Tipos de Testing

- Funcional: Verifica que cada función del software opera conforme a los requisitos, evaluando "qué" hace el sistema.
    
- No Funcional: Examina otros atributos como rendimiento, seguridad y usabilidad, analizando "cómo" el sistema realiza las funciones.
    
- Caja Blanca: Se enfoca en la estructura interna del código, ideal para testers con conocimientos en desarrollo.
    
- Asociada al Cambio: Se utiliza para asegurar que los cambios introducidos no afecten el resto del sistema, especialmente en metodologías ágiles.
    

Ambos niveles y tipos de testing se aplican en conjunto, permitiendo una visión integral que mejora la calidad del producto en cada etapa del desarrollo.

  

# Prueba de Componente 

La prueba de componente, también conocida como prueba unitaria o de módulo, se centra en evaluar cada componente de software de manera aislada. Este tipo de prueba permite verificar el correcto funcionamiento de componentes específicos, asegurando que cumplan con los comportamientos esperados antes de ser integrados al sistema completo. Por lo general este tipo de pruebas lo realizan los desarrolladores o los testers de caja blanca.

#### Objetivos

- Reducir el riesgo: Detectar defectos en una fase temprana para evitar su propagación.
    
- Verificación funcional y no funcional: Comprobar que el componente responde a los requerimientos.
    
- Asegurar calidad: Construir confianza en la calidad del componente.
    
- Evitar defectos en niveles superiores: Detectar y corregir problemas antes de la integración.
    

#### Aplicación

Las pruebas de componente se realizan de manera independiente al resto del sistema, utilizando objetos simulados o "stubs" cuando es necesario. Este enfoque es especialmente útil en el desarrollo de pruebas para diseños detallados, código específico y modelos de datos de componentes individuales.

# Prueba de Sistema  

La prueba de sistema es una evaluación integral enfocada en el comportamiento y capacidades de todo un sistema. Su objetivo es asegurar que el sistema funcione correctamente como un conjunto, validando tanto los requerimientos funcionales como los no funcionales.

#### Objetivos

- Reducir el riesgo: Identificar defectos que puedan afectar el desempeño del sistema en su totalidad.
    
- Verificación integral: Confirmar que todas las funcionalidades del sistema y sus características de rendimiento, seguridad y usabilidad cumplen con los requisitos establecidos.
    
- Asegurar calidad global: Construir confianza en la operatividad del sistema completo antes de su implementación.
    
- Prevenir problemas en producción: Detectar y corregir fallas antes de que el sistema llegue a los usuarios finales.
    

#### Enfoque

La prueba de sistema se realiza en un entorno similar al de producción para simular escenarios de uso reales. Durante esta etapa, se evalúan tanto los aspectos funcionales (qué hace el sistema) como los no funcionales (cómo lo hace), asegurando un análisis completo del sistema en situaciones de extremo a extremo.

# Prueba de Aceptación 

La prueba de aceptación es la fase final en el proceso de pruebas de software, enfocada en evaluar si el sistema cumple con las expectativas y requisitos del usuario final. Su principal objetivo es verificar que el sistema está listo para ser desplegado y utilizado en un entorno de producción, asegurando así la satisfacción del usuario. En este tipo de pruebas puede participar el cliente o usuarios finales de la aplicación.

#### Objetivos

- Validar requerimientos funcionales y no funcionales: Confirmar que el sistema cumple con todos los requisitos especificados por el usuario.
    
- Asegurar la calidad general: Proporcionar confianza en que el sistema funcionará como se espera en un entorno real.
    
- Identificar posibles mejoras: Obtener retroalimentación directa de los usuarios para realizar ajustes antes del lanzamiento final.
    

#### Tipos de Pruebas de Aceptación

1. Pruebas de Usuario (User Acceptance Testing - UAT): Se realizan en un entorno simulado o real, donde los usuarios finales validan que el sistema cumple con sus necesidades operativas y de negocio.
    
2. Pruebas Alfa: Llevadas a cabo en las instalaciones del desarrollador, estas pruebas permiten a usuarios potenciales o un equipo de QA validar las funcionalidades principales antes del lanzamiento público.
    
3. Pruebas Beta: Realizadas por usuarios finales en sus propios entornos, proporcionan retroalimentación sobre el uso y posibles problemas en condiciones reales.
    

  

# Diferencias entre Error, Defecto y Fallo  

En el proceso de desarrollo y pruebas de software, es fundamental entender la diferencia entre error, defecto y fallo, ya que estos conceptos ayudan a identificar, clasificar y corregir problemas en el sistema.

- Error: Es una equivocación humana, normalmente en el análisis o desarrollo del software. Por ejemplo, un programador comete un error al escribir una fórmula incorrecta para calcular un descuento. Este error puede derivar en un problema en el código.
    
- Defecto: Es la manifestación del error en el software. Si el error no se detecta y corrige en la fase de desarrollo, se convierte en un defecto. Por ejemplo, debido al error en la fórmula, la aplicación calcula mal el descuento, provocando una diferencia en los precios finales.
    
- Fallo: Es la manifestación visible del defecto cuando el software se ejecuta, afectando la experiencia del usuario. Por ejemplo, cuando el usuario intenta aplicar el descuento, observa que el monto es incorrecto debido a la fórmula mal programada.
    

En resumen, un error humano en el código lleva a un defecto en el sistema, que se convierte en un fallo visible cuando el software es ejecutado

  

# Clasificación de Defectos y Criticidad  

### Clasificación de Defectos y su Reporte

Los defectos en software pueden clasificarse en distintas categorías según su naturaleza y el impacto en el sistema. Además, la criticidad y urgencia de cada defecto son elementos clave en su clasificación y resolución, ya que determinan la prioridad de atención en el reporte.

#### Tipos de Defectos

1. Defectos Visuales:
    

- Afectan la apariencia o usabilidad del sistema, como diferencias entre el diseño planificado y el implementado.
    
- Ejemplo: Un botón de "Enviar" aparece desalineado o con un color incorrecto.
    

3. Defectos en Componentes:
    

- Relacionados con el mal funcionamiento de elementos específicos del sistema, que no cumplen con la funcionalidad esperada.
    
- Ejemplo: Al ingresar un nombre en el campo "Usuario", el sistema no lo registra correctamente.
    

5. Defectos de Contenido:
    

- Son errores en la información mostrada que no están relacionados con la funcionalidad o el diseño, sino con el contenido.
    
- Ejemplo: La sección de "Política de Privacidad" contiene fechas o referencias incorrectas.
    

7. Defectos Disruptivos:
    

- Los más graves, ya que afectan la funcionalidad general, impidiendo que el sistema opere correctamente.
    
- Ejemplo: Un cambio en el sistema provoca que la pantalla principal no cargue, dejando al usuario sin acceso.
    

#### Importancia de la Criticidad y Urgencia

- Criticidad: Indica el impacto potencial del defecto en el sistema, ayudando a identificar la gravedad del daño.
    

- Ejemplo: Un defecto crítico puede bloquear el acceso de los usuarios a funciones clave.
    

- Urgencia: Define la rapidez con la que debe solucionarse el defecto para evitar problemas mayores.
    

- Ejemplo: Un defecto de alta urgencia puede ser un error en el login que afecta a todos los usuarios del sistema y requiere resolución inmediata.
    

El equilibrio entre criticidad y urgencia permite priorizar defectos de forma eficaz en el proceso de pruebas​. Teniendo en cuenta las definiciones, no hay un estándar que indique cuando un defecto va a ser crítico o urgente sino que va a depender del tipo de software que se esté probando, por ejemplo, si la aplicación es un e-commerce y lo que no funciona es el carrito de compras seguramente sea crítico y urgente corregirlo ya que los usuarios finales no podrán realizar compras; por otra parte, si el defecto es una palabra mal escrita posiblemente no se define como algo crítico o urgente de corregir. Si estamos hablando en cambio de la web de la real academia española, una palabra mal escrita podría considerarse como algo crítico y urgente de corregir ya que la propia web tiene como objetivo mostrar correctamente las palabras y sus definiciones. En conclusión, el análisis de la criticidad y urgencia de una web/aplicación dependerá del objetivo que tiene y de las reglas de negocio.

  
  
**