UNIDAD 5

# Web Testing

Alcance del Web Testing:  
El Web Testing es una actividad esencial en el QA Manual que cubre todos los componentes de una plataforma que opera sobre un navegador web. Esto incluye evaluar páginas dinámicas y estáticas, revisando que cada elemento funcione correctamente en diversos dispositivos y sistemas operativos, y asegurando que todos los componentes, como tipografía, resolución, y enlaces, operen de manera óptima. En algunas pruebas, el Web Testing puede solaparse con el mobile testing, ya que los dispositivos móviles también cuentan con navegadores; sin embargo, el enfoque sigue centrado en los exploradores web.

Importancia del Web Testing:  
El Web Testing tiene una relevancia crítica en la experiencia de usuario (UX) y en la calidad de la plataforma. Los usuarios esperan que el sitio web funcione correctamente en cualquier navegador (Chrome, Firefox, Safari, Edge, etc.) y en múltiples dispositivos, lo que obliga a los testers a realizar pruebas de compatibilidad exhaustivas. Además, las pruebas de usabilidad y rendimiento son fundamentales para asegurar que el sitio responda adecuadamente a los comandos del usuario, que cargue rápido y que no presente errores que afecten la interacción.

Cobertura de los Componentes en una Plataforma Web:  
Las pruebas abarcan una variedad de componentes clave:

1. Tipografía y Corrección Ortográfica: Se verifica que la tipografía y los textos cumplan con las especificaciones del equipo de diseño y redacción, respetando tanto el estilo como la ortografía.
    
2. Resolución y Responsividad: La plataforma debe verse bien y mantenerse funcional tanto en pantallas grandes como en dispositivos más pequeños. La adaptabilidad del sitio, o responsividad, garantiza que el contenido se ajuste automáticamente según el tamaño de la pantalla.
    
3. Compatibilidad y Enlaces: Cada navegador debe mostrar la plataforma de manera uniforme y funcional. Los enlaces se revisan para asegurarse de que estén correctamente direccionados y operativos.
    
4. Colores y Servicios Web: Se valida que los colores sean los especificados en el diseño y que los servicios web (API, conexiones a bases de datos, etc.) funcionen correctamente.
    

# Secciones a Probar

Tipografía  
La tipografía en un sitio web forma parte del marco de UX/UI y es fundamental para mantener la consistencia visual. Es importante verificar que las fuentes utilizadas sean correctas y cumplan con los estándares predefinidos, como el tamaño, estilo y color especificados. También es clave verificar que no existan variaciones o errores en diferentes navegadores.

Corrección Ortográfica  
La ortografía y gramática deben revisarse exhaustivamente. Muchas veces, el contenido es creado por equipos de UX Writers o legales, y su correcta redacción contribuye a la profesionalidad y credibilidad del sitio. La tarea del tester es asegurarse de que no haya errores que afecten la experiencia del usuario.

Resolución  
La resolución garantiza que el diseño y los elementos visuales del sitio se adapten correctamente a diferentes tamaños de pantalla, desde monitores grandes hasta dispositivos móviles. Las pruebas se realizan ajustando manualmente la resolución para detectar problemas como imágenes deformadas o elementos fuera de lugar.

Compatibilidad  
La compatibilidad implica que el sitio debe verse y funcionar de la misma manera en todos los navegadores populares (Chrome, Firefox, Edge, Safari, etc.). Los testers deben probar en múltiples navegadores para identificar diferencias en el comportamiento o apariencia que puedan impactar la experiencia del usuario.

Links  
Los links son críticos para la navegación y funcionalidad del sitio. Es esencial verificar que todos los enlaces lleven al lugar correcto y no den errores, además de asegurarse de que no existan enlaces rotos o que lleven a páginas no deseadas.

Colores  
El color de los elementos debe cumplir con las especificaciones del diseño. El equipo de testing debe asegurarse de que los colores sean consistentes y de que respeten los códigos especificados (#000000 para negro, #FFFFFF para blanco, etc.), ya que esto afecta tanto la estética como la accesibilidad del sitio.

# Herramientas de Web Testing

Para realizar pruebas web de manera efectiva, se pueden utilizar diversas herramientas especializadas que ayudan a identificar problemas y asegurar que una aplicación web funcione correctamente en diferentes entornos y dispositivos. Las herramientas más recomendadas incluyen la consola de desarrolladores, validadores HTML/CSS y verificadores de links.

#### Consola de Desarrolladores

La consola de desarrolladores, accesible generalmente mediante la tecla F12 en navegadores modernos, es una herramienta fundamental en el testing web. A través de ella, los testers pueden inspeccionar y modificar elementos en la página, ver el código HTML y CSS, así como rastrear las peticiones de red y los web services en tiempo real. La sección de “Elementos” permite verificar aspectos visuales como tipografía, colores y tamaños. Además, se puede simular la responsividad en diferentes dispositivos, asegurando que el diseño de la página se adapte adecuadamente.

#### Validadores HTML/CSS

Los validadores de HTML y CSS son herramientas en línea que revisan el código fuente de una página web, indicando posibles errores o problemas de cumplimiento con los estándares web. Estas herramientas son útiles para detectar errores de sintaxis, etiquetas mal colocadas o problemas de compatibilidad, lo cual contribuye a mejorar la accesibilidad y el rendimiento de la web. Al validar el HTML y CSS, el tester garantiza que la página será más compatible y estable en diferentes navegadores.

#### Verificadores de Links

Los verificadores de links son herramientas que rastrean y verifican los enlaces dentro de una página web, informando sobre cualquier enlace roto o mal direccionado. Esta funcionalidad es vital en el testing web, ya que los enlaces defectuosos pueden afectar la experiencia del usuario y la navegabilidad de la página. Mediante estas herramientas, el tester recibe una lista de links problemáticos junto con su ubicación y detalles, facilitando la corrección.

Cada una de estas herramientas cumple un rol esencial para asegurar que una página web sea funcional, accesible y esté libre de errores, mejorando así su calidad y usabilidad.

# Páginas Dinámicas vs Estáticas

Páginas Estáticas Las páginas estáticas presentan contenido fijo, sin interacción directa con el usuario, y están diseñadas principalmente para proporcionar información de forma rápida y sencilla. Estas páginas están codificadas en HTML o XHTML, lo que las hace fáciles de cargar desde un servidor, pero su actualización requiere acceder al código fuente y realizar modificaciones manuales. Esto implica que el proceso de mantenimiento y actualización puede ser más lento y menos flexible.

Características de las Páginas Estáticas:

- No incluyen movimiento ni interactividad.
    
- Están diseñadas en HTML o XHTML.
    
- Su actualización es lenta y manual, requiriendo acceso directo al servidor.
    
- Ejemplo típico: páginas corporativas o de presentación de productos con contenido estable y pocos cambios.
    

Páginas Dinámicas Las páginas dinámicas, por otro lado, ofrecen interactividad y permiten al usuario interactuar con el contenido. Esto se logra mediante scripts que se ejecutan en el servidor, proporcionando respuestas personalizadas basadas en la acción del usuario. Al actualizarse automáticamente, son ideales para aplicaciones que requieren datos en tiempo real y un entorno adaptable. Generalmente están vinculadas a bases de datos y otras herramientas externas.

Características de las Páginas Dinámicas:

- Ofrecen diseño y funcionalidad sin límites, permitiendo alternar contenido.
    
- Pueden utilizar varios lenguajes de programación y se actualizan automáticamente.
    
- Integran herramientas externas como bases de datos y servidores.
    
- Ejemplo típico: redes sociales o plataformas de comercio electrónico que dependen de información en constante cambio.
    

Diferencias Clave: Mientras que las páginas estáticas se centran en la simplicidad y la rapidez de carga, siendo ideales para contenidos fijos, las páginas dinámicas están orientadas a la interacción y flexibilidad, permitiendo una experiencia de usuario mucho más personalizada y rica en funcionalidades. Ambas pueden coexistir en un mismo sistema, permitiendo que una página estática dirija a una página dinámica según la necesidad de la funcionalidad.

# Responsividad en Web

Un sitio responsivo es aquel diseñado para ajustarse automáticamente al tamaño y resolución de diferentes dispositivos, ya sea un smartphone, tablet, laptop o computadora de escritorio. Este tipo de diseño permite que el contenido se muestre de forma óptima en cualquier pantalla, ofreciendo una experiencia de usuario consistente y accesible.

La adaptabilidad del contenido es esencial en un entorno donde los usuarios acceden a los sitios web desde múltiples dispositivos, cada uno con sus propias características. Esto implica que, además del ajuste en tamaño de texto e imágenes, los elementos de navegación, menús y botones también se adapten para facilitar la interacción en pantallas más pequeñas.

Una estrategia efectiva para construir sitios responsivos es el enfoque mobile-first (móviles primero), que consiste en diseñar primero para dispositivos móviles y luego adaptar el diseño para pantallas más grandes. Esto no solo optimiza la experiencia móvil, sino que también mejora la velocidad de carga y el rendimiento en todos los dispositivos.

En el contexto de Testing QA Manual, es crucial realizar pruebas en varios dispositivos y navegadores para asegurar que el diseño responsivo funcione adecuadamente en todos ellos. Esto abarca verificar que:

- Las imágenes y el texto se ajusten correctamente sin romper el diseño.
    
- Los menús y botones sean accesibles y fáciles de usar en pantallas táctiles.
    
- La visualización en diferentes navegadores sea uniforme para mantener la calidad de la plataforma.
    

# ¿Qué es Mobile Testing?  
  

El testing mobile se ha vuelto esencial en un mundo donde el uso de dispositivos móviles supera al de computadoras de escritorio. Con millones de usuarios accediendo a contenido y aplicaciones principalmente desde sus teléfonos, es vital asegurar que las aplicaciones móviles funcionen correctamente en diversos dispositivos y sistemas operativos, especialmente Android e iOS, los dos sistemas más predominantes. Aunque existen otros sistemas operativos, el mercado está dominado por estos dos, lo que permite enfocar los esfuerzos de testing en garantizar la calidad en cada uno de ellos.

Una diferencia clave con respecto al testing web es que las aplicaciones móviles pueden ser nativas o web. Las aplicaciones nativas están diseñadas para un sistema operativo específico, lo cual permite un mejor rendimiento y mayor integración con los recursos del dispositivo, pero exige pruebas específicas para cada plataforma. Las aplicaciones web, por otro lado, se ejecutan en navegadores, permitiendo una mayor portabilidad entre dispositivos, aunque pueden tener limitaciones de rendimiento y funcionalidad sin conexión.

Las pruebas en dispositivos móviles abarcan tanto el hardware como el software. En el caso del hardware, es importante probar en diferentes modelos de dispositivos para identificar posibles variaciones en rendimiento, respuesta de botones y funcionalidades físicas. Por el lado del software, las pruebas deben abarcar versiones activas de los sistemas operativos, ya que los sistemas obsoletos pueden introducir problemas de compatibilidad y elevar los costos de mantenimiento.

Además, las tablets también entran en el espectro de pruebas, pues los sistemas operativos móviles se extienden a estos dispositivos. Incluirlas permite ofrecer una cobertura más completa, adaptando las pruebas para asegurar una experiencia consistente sin importar el tipo de dispositivo móvil en uso.

En conclusión, el testing mobile requiere un enfoque detallado en la calidad y usabilidad, considerando las particularidades de los sistemas operativos, el tipo de aplicación y la amplia variedad de dispositivos.

# Aplicaciones Nativas vs Web

#### Aplicaciones Web

Las aplicaciones web funcionan sobre navegadores y se destacan por su compatibilidad universal. Su principal ventaja es que pueden ser utilizadas en cualquier dispositivo con acceso a un navegador compatible. Este tipo de aplicaciones es sencillo de desarrollar y permite una mayor flexibilidad, ya que no dependen del sistema operativo del dispositivo.

Características de aplicaciones web:

- Compatibilidad entre navegadores.
    
- Desarrollo más rápido y sencillo.
    
- Necesitan conexión a internet para funcionar.
    
- Limitaciones en el acceso a funciones del sistema operativo.
    

Ejemplo: Google Drive es un ejemplo claro de aplicación web, ya que permite acceso desde cualquier navegador sin importar el dispositivo.

Desventajas:

- Su rendimiento y respuesta pueden variar según el navegador.
    
- Requiere conexión a internet para funcionar.
    
- No puede emular completamente una aplicación nativa.
    

#### Aplicaciones Nativas

Las aplicaciones nativas están diseñadas específicamente para un sistema operativo, como Android o iOS. Estas aplicaciones aprovechan al máximo las capacidades del sistema y el hardware, lo que permite un mejor rendimiento y una experiencia de usuario optimizada.

Características de aplicaciones nativas:

- Mayor rendimiento y velocidad.
    
- Acceso directo a los recursos del sistema (cámara, GPS, almacenamiento).
    
- Requiere un desarrollo separado para cada sistema operativo.
    
- Suelen ser más pesadas y requieren mantenimiento constante.
    

Ejemplo: Candy Crush es una aplicación nativa que puede ejecutarse sin conexión a internet y aprovecha los recursos gráficos y de almacenamiento del dispositivo.

Desventajas:

- Mayor costo y tiempo de desarrollo al necesitar una versión para cada sistema operativo.
    
- Necesidad de actualizaciones y mantenimiento regulares.
    
- Ocupan más espacio en el dispositivo en comparación con aplicaciones web.
    

Ejemplo de herramientas para probar aplicaciones nativas: emulador Android Studio y simulador Xcode.

Los emuladores y simuladores ayudan a los testers a probar en diferentes tipos de celulares cuando no se cuenta con uno físico, cambiando las resoluciones y modelos según sea necesario.
