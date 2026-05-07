# Introducción a las pruebas no funcionales

Las pruebas no funcionales son una pieza clave en el aseguramiento de la calidad, ya que se enfocan en aspectos críticos del sistema que trascienden la simple funcionalidad. Su propósito es evaluar factores como la estabilidad, seguridad, rendimiento, y la capacidad de respuesta del sistema ante diferentes condiciones. A diferencia de las pruebas funcionales, que verifican si el sistema realiza las acciones esperadas, las pruebas no funcionales buscan asegurar que el sistema pueda sostener un rendimiento óptimo y seguro en entornos de uso real y bajo circunstancias de estrés.

**Rol en la Estabilidad y Seguridad del Sistema**

Estas pruebas son esenciales para garantizar que el sistema no solo funcione bien, sino que también sea confiable y robusto. Las pruebas de rendimiento, por ejemplo, evalúan la capacidad del sistema para gestionar grandes volúmenes de datos o conexiones simultáneas sin degradarse. Las pruebas de seguridad, por otro lado, ayudan a identificar y mitigar vulnerabilidades, previniendo posibles ataques que podrían comprometer los datos y la privacidad de los usuarios.

Al implementar pruebas no funcionales, se contribuye a desarrollar un sistema que no solo cumpla con sus funciones, sino que también sea capaz de mantenerse operativo y seguro en el tiempo. Esto es especialmente importante en aplicaciones de alta disponibilidad, donde el objetivo es minimizar fallos y asegurar una experiencia de usuario de calidad, incluso en momentos de máxima demanda. En suma, las pruebas no funcionales refuerzan la calidad del sistema en sus dimensiones de confiabilidad, escalabilidad, y seguridad, asegurando así una base sólida para el funcionamiento efectivo del software.

---

# Tipos de pruebas no funcionales

**Pruebas de Estrés**

Las pruebas de estrés se aplican para evaluar la estabilidad de un sistema bajo condiciones extremas. Estas pruebas ayudan a identificar el punto de fallo del sistema al sobrecargarlo con solicitudes más allá de su capacidad habitual. Se realizan en momentos de alta demanda o en eventos especiales, como el Black Friday o transmisiones masivas, para garantizar que el sistema pueda manejar picos sin fallar. Esto permite ajustar la infraestructura y prever posibles mejoras en la capacidad del sistema.

**Pruebas de Seguridad**

Estas pruebas buscan detectar vulnerabilidades que podrían comprometer la integridad del sistema y la confidencialidad de los datos. Se centran en aspectos como autenticación, gestión de sesiones y validación de entradas para prevenir ataques, como la inyección SQL y el Cross Site Scripting. Las pruebas de seguridad son esenciales durante el desarrollo para reducir el riesgo de ataques y proteger la información sensible del sistema​.

**Pruebas de Carga**

Las pruebas de carga miden el rendimiento del sistema bajo un número elevado de usuarios concurrentes, verificando si las funciones y respuestas siguen siendo óptimas. Este tipo de prueba se utiliza cuando se necesita asegurar que el sistema puede manejar un flujo constante de solicitudes sin afectar su tiempo de respuesta. Es ideal para evaluar si el sistema puede mantenerse operativo durante el uso intensivo​.

**Pruebas de Resistencia**

Estas pruebas son similares a las de carga, pero se enfocan en verificar la estabilidad del sistema bajo un uso prolongado y continuo. La prueba de resistencia se utiliza para identificar posibles degradaciones en el rendimiento o fallos que podrían surgir debido al tiempo de exposición a una alta carga. Estas pruebas son útiles para determinar si el sistema puede soportar una carga constante durante períodos largos sin afectarse.