## Diferencias entre Error, Defecto y Fallo

En el proceso de desarrollo y pruebas de software, es fundamental entender la diferencia entre error, defecto y fallo, ya que estos conceptos ayudan a identificar, clasificar y corregir problemas en el sistema.

**Error**: Es una equivocación humana, normalmente en el análisis o desarrollo del software. Por ejemplo, un programador comete un error al escribir una fórmula incorrecta para calcular un descuento. Este error puede derivar en un problema en el código.

**Defecto**: Es la manifestación del error en el software. Si el error no se detecta y corrige en la fase de desarrollo, se convierte en un defecto. Por ejemplo, debido al error en la fórmula, la aplicación calcula mal el descuento, provocando una diferencia en los precios finales.

**Fallo**: Es la manifestación visible del defecto cuando el software se ejecuta, afectando la experiencia del usuario. Por ejemplo, cuando el usuario intenta aplicar el descuento, observa que el monto es incorrecto debido a la fórmula mal programada.

En resumen, un error humano en el código lleva a un defecto en el sistema, que se convierte en un fallo visible cuando el software es ejecutado

## Clasificación de Defectos y Criticidad

Los defectos en software pueden clasificarse en distintas categorías según su naturaleza y el impacto en el sistema. Además, la criticidad y urgencia de cada defecto son elementos clave en su clasificación y resolución, ya que determinan la prioridad de atención en el reporte.

**Tipos de Defectos**

**1. Defectos Visuales:**

Afectan la apariencia o usabilidad del sistema, como diferencias entre el diseño planificado y el implementado.

**Ejemplo**: Un botón de "Enviar" aparece desalineado o con un color incorrecto.

**2. Defectos en Componentes:**

Relacionados con el mal funcionamiento de elementos específicos del sistema, que no cumplen con la funcionalidad esperada.

**Ejemplo**: Al ingresar un nombre en el campo "Usuario", el sistema no lo registra correctamente.

**3. Defectos de Contenido:**

Son errores en la información mostrada que no están relacionados con la funcionalidad o el diseño, sino con el contenido.

**Ejemplo**: La sección de "Política de Privacidad" contiene fechas o referencias incorrectas.

**4. Defectos Disruptivos:**

Los más graves, ya que afectan la funcionalidad general, impidiendo que el sistema opere correctamente.

**Ejemplo**: Un cambio en el sistema provoca que la pantalla principal no cargue, dejando al usuario sin acceso.

**Importancia de la Criticidad y Urgencia**

- Criticidad: Indica el impacto potencial del defecto en el sistema, ayudando a identificar la gravedad del daño.
    

Ejemplo: Un defecto crítico puede bloquear el acceso de los usuarios a funciones clave.

- Urgencia: Define la rapidez con la que debe solucionarse el defecto para evitar problemas mayores.
    

Ejemplo: Un defecto de alta urgencia puede ser un error en el login que afecta a todos los usuarios del sistema y requiere resolución inmediata.

El equilibrio entre criticidad y urgencia permite priorizar defectos de forma eficaz en el proceso de pruebas​. Teniendo en cuenta las definiciones, no hay un estándar que indique cuando un defecto va a ser crítico o urgente sino que va a depender del tipo de software que se esté probando, por ejemplo, si la aplicación es un e-commerce y lo que no funciona es el carrito de compras seguramente sea crítico y urgente corregirlo ya que los usuarios finales no podrán realizar compras; por otra parte, si el defecto es una palabra mal escrita posiblemente no se define como algo crítico o urgente de corregir. Si estamos hablando en cambio de la web de la real academia española, una palabra mal escrita podría considerarse como algo crítico y urgente de corregir ya que la propia web tiene como objetivo mostrar correctamente las palabras y sus definiciones. En conclusión, el análisis de la criticidad y urgencia de una web/aplicación dependerá del objetivo que tiene y de las reglas de negocio.

# Glosario

**Criticidad**: es la medida del alcance del daño potencial que el incidente puede causar

**Defecto**: Es lo que posee un componente como consecuencia de un error.

**Error**: Una acción humana que genera un mal ingreso de información o datos.

**Falla**: Es la ejecución propia del defecto. Lo que podemos ver que anda mal.

**Pruebas** Funcionales: pruebas que evalúan las funciones que el sistema debe realizar.

**Pruebas No Funcionales**: la prueba no-funcional prueba que tan bien se comporta un sistema. Se basan en las pruebas de rendimiento y desempeño de un sistema.

**Pruebas de Regresión**: La prueba de regresión consiste en probar un sistema que ha sido analizado previamente para asegurar que no se haya introducido algún tipo de defecto como resultado de cambios realizados

**Prueba Beta**: las pruebas realizadas por usuarios reales en un entorno real.

**Prueba Alfa**: prueba de aceptación interna realizada principalmente por los equipos internos de control de calidad y pruebas del software. La prueba alfa es la última prueba realizada por los equipos de prueba en el sitio de desarrollo después de la prueba de aceptación y antes de lanzar el software para la prueba beta.

**Urgencia**: la urgencia mide que tan inmediata es la necesidad de corregir un defecto en el sistema.