## Introducción a los Niveles y Tipos de Testing

Los niveles y tipos de testing son fundamentales en el proceso de pruebas de software. Cada uno permite estructurar y gestionar las actividades de prueba para asegurar que el sistema cumple con los estándares de calidad esperados. Es importante entender cómo se aplican estos niveles y tipos para evaluar y optimizar el rendimiento y funcionalidad del software en diferentes etapas.

**Niveles de Testing**

- Prueba de Componente (Unitarias): Se enfoca en los componentes individuales de software. Su objetivo es verificar que cada componente funcione como se espera, asegurando calidad y detectando defectos antes de avanzar a niveles superiores.
- Prueba de Integración: Evalúa la interacción entre componentes. Es crucial para detectar problemas en las interfaces que no se manifiestan en las pruebas unitarias.
- Prueba de Sistema: Valida el comportamiento de todo el sistema. Aquí se comprueba si el software responde correctamente a requerimientos funcionales y no funcionales, acercándose al entorno de producción.
- Prueba de Aceptación: Su propósito es validar que el sistema cumpla con las expectativas del usuario y se ajuste a sus necesidades. Esto suele involucrar al usuario final y otras partes interesadas.

**Tipos de Testing**

- Funcional: Verifica que cada función del software opera conforme a los requisitos, evaluando "qué" hace el sistema.
- No Funcional: Examina otros atributos como rendimiento, seguridad y usabilidad, analizando "cómo" el sistema realiza las funciones.
- Caja Blanca: Se enfoca en la estructura interna del código, ideal para testers con conocimientos en desarrollo.
- Asociada al Cambio: Se utiliza para asegurar que los cambios introducidos no afecten el resto del sistema, especialmente en metodologías ágiles.

Ambos niveles y tipos de testing se aplican en conjunto, permitiendo una visión integral que mejora la calidad del producto en cada etapa del desarrollo.

## Prueba de Componente

La prueba de componente, también conocida como prueba unitaria o de módulo, se centra en evaluar cada componente de software de manera aislada. Este tipo de prueba permite verificar el correcto funcionamiento de componentes específicos, asegurando que cumplan con los comportamientos esperados antes de ser integrados al sistema completo. Por lo general este tipo de pruebas lo realizan los desarrolladores o los testers de caja blanca.

**Objetivos**

- Reducir el riesgo: Detectar defectos en una fase temprana para evitar su propagación.
- Verificación funcional y no funcional: Comprobar que el componente responde a los requerimientos.
- Asegurar calidad: Construir confianza en la calidad del componente.
- Evitar defectos en niveles superiores: Detectar y corregir problemas antes de la integración.

**Aplicación**

Las pruebas de componente se realizan de manera independiente al resto del sistema, utilizando objetos simulados o "stubs" cuando es necesario. Este enfoque es especialmente útil en el desarrollo de pruebas para diseños detallados, código específico y modelos de datos de componentes individuales.