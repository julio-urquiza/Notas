La planificación de pruebas en QA incluye varios elementos clave que organizan y estructuran el proceso de validación del software, asegurando que se cumplan los objetivos de calidad.

**Plan de Pruebas**

El Plan de Pruebas es un documento que establece el alcance, enfoque y criterios de aceptación de las pruebas. Define los recursos, cronograma, objetivos y riesgos asociados al proceso de QA. Este plan guía al equipo en la ejecución de pruebas, alineando las actividades con los requerimientos del proyecto​.

**Historias de usuario, criterios de aceptación y requerimientos**

Las historias de usuario son un documento en donde se detalla al equipo completo encargado de la construcción y testing del software que es lo que se va a construir, prototipos de cómo se debe ver, características a tener en cuenta, criterios de aceptación y requerimientos. Cuando se va a construir una nueva funcionalidad si no es muy grande se puede realizar una sola historia, si la funcionalidad a construir es muy grande o abarca muchas funcionalidades entonces se recomienda separar en varias historias más chicas para que se pueda trabajar ordenadamente.

Los requerimientos definen técnicamente la funcionalidad a construir pero sin entrar en detalles.

Los criterios de aceptación especifican el comportamiento mínimo esperado para que una funcionalidad se considere correcta. Es escrito en colaboración con los Product Owners y suele seguir un formato como "Dado, Cuando, Entonces" para detallar las condiciones en que el software debería operar correctamente.

**Casos de Prueba**

Los casos de prueba son documentos que detallan pasos específicos para verificar si una funcionalidad cumple con los criterios definidos.

**Existen dos tipos principales:**

- Casos de Prueba Positivos: Diseñados para asegurar que el sistema funcione correctamente con datos válidos, siguiendo el flujo esperado del usuario.
    
- Casos de Prueba Negativos: Valoran cómo responde el sistema a datos incorrectos o fuera de lo común, ayudando a identificar y prevenir errores.
    

Estos casos son esenciales en el proceso de QA, pues ofrecen una guía clara de validación de funcionalidades, permitiendo detectar fallos en fases tempranas y garantizar que el producto cumpla con los estándares de calidad.

Para la construcción de casos de prueba los testers se deben basar en la documentación (Historias de usuario, requerimientos y criterios de aceptación), en base al análisis que se realice de estos documentos es que surgirán tantos casos de prueba como sean necesarios para que se pueda confirmar que el software cumple o no con los requerimientos y criterios de aceptación definidos.

Es muy importante el paso del análisis y escritura de casos de prueba ya que es el respaldo que tendremos de nuestro trabajo.

Por lo general el caso de prueba tendrá información basica: Nombre adecuado y representativo de lo que se quiere validar, un código unico de identificación, pasos a seguir para ejecutarlo, resultado esperado y resultado obtenido. Cuando el resultado esperado y el obtenido no son iguales es que podriamos decir que estamos en presencia de un defecto

----
# Glosario

**Backend**: El backend es la parte del desarrollo web que se encarga de que toda la lógica de una página web funcione. Se trata del conjunto de acciones que pasan en una web pero que no vemos como, por ejemplo, la comunicación con el servidor

**Casos de Prueba:** Set de condiciones o variables bajo las cuales un tester determina si el software funciona correctamente o no.

**Casos de Prueba Positivos**: La prueba positiva implica ejecutar un escenario de prueba con solo datos correctos y válidos.

**Casos de Prueba Negativos**: La prueba negativa implica ejecutar un escenario de prueba con solo datos incorrectos, no válidos y nulos.

**Ciclo de vida**: es una secuencia estructurada y bien definida de las etapas en ingeniería de software para desarrollar el software deseado.

**Gherkin**: es un lenguaje diseñado para resolver un problema muy específico. Este problema se basa en la comunicación entre los perfiles de negocio y los perfiles técnicos a la hora de trabajar bajo un enfoque BDD.

**Historias de Usuario/User Story**: las historias de usuario, son pequeñas descripciones de los requerimientos de un cliente.

**Interfaz de usuario**: La interfaz de usuario (UI) es el conjunto de los controles y canales sensoriales mediante los cuales un usuario puede comunicarse con una máquina

**Jira**: es una herramienta de gestión de proyectos que sirve para gestionar tareas

**Product Owner**: Dueño de Producto. Rol de Scrum. Responsable de maximizar el valor del producto y el trabajo del Equipo de Desarrollo.

**Requerimientos Funcionales**: descripciones generales de partes de un sistema