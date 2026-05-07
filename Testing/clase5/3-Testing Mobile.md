# ¿Qué es Mobile Testing?

El testing mobile se ha vuelto esencial en un mundo donde el uso de dispositivos móviles supera al de computadoras de escritorio. Con millones de usuarios accediendo a contenido y aplicaciones principalmente desde sus teléfonos, es vital asegurar que las aplicaciones móviles funcionen correctamente en diversos dispositivos y sistemas operativos, especialmente Android e iOS, los dos sistemas más predominantes. Aunque existen otros sistemas operativos, el mercado está dominado por estos dos, lo que permite enfocar los esfuerzos de testing en garantizar la calidad en cada uno de ellos.

Una diferencia clave con respecto al testing web es que las aplicaciones móviles pueden ser nativas o web. Las aplicaciones nativas están diseñadas para un sistema operativo específico, lo cual permite un mejor rendimiento y mayor integración con los recursos del dispositivo, pero exige pruebas específicas para cada plataforma. Las aplicaciones web, por otro lado, se ejecutan en navegadores, permitiendo una mayor portabilidad entre dispositivos, aunque pueden tener limitaciones de rendimiento y funcionalidad sin conexión.

Las pruebas en dispositivos móviles abarcan tanto el hardware como el software. En el caso del hardware, es importante probar en diferentes modelos de dispositivos para identificar posibles variaciones en rendimiento, respuesta de botones y funcionalidades físicas. Por el lado del software, las pruebas deben abarcar versiones activas de los sistemas operativos, ya que los sistemas obsoletos pueden introducir problemas de compatibilidad y elevar los costos de mantenimiento.

Además, las tablets también entran en el espectro de pruebas, pues los sistemas operativos móviles se extienden a estos dispositivos. Incluirlas permite ofrecer una cobertura más completa, adaptando las pruebas para asegurar una experiencia consistente sin importar el tipo de dispositivo móvil en uso.

En conclusión, el testing mobile requiere un enfoque detallado en la calidad y usabilidad, considerando las particularidades de los sistemas operativos, el tipo de aplicación y la amplia variedad de dispositivos.

---

# Aplicaciones Nativas vs Web

## Aplicaciones Web

Las aplicaciones web funcionan sobre navegadores y se destacan por su compatibilidad universal. Su principal ventaja es que pueden ser utilizadas en cualquier dispositivo con acceso a un navegador compatible. Este tipo de aplicaciones es sencillo de desarrollar y permite una mayor flexibilidad, ya que no dependen del sistema operativo del dispositivo.

**Características de aplicaciones web:**

- Compatibilidad entre navegadores.
    
- Desarrollo más rápido y sencillo.
    
- Necesitan conexión a internet para funcionar.
    
- Limitaciones en el acceso a funciones del sistema operativo.
    

**Ejemplo**: Google Drive es un ejemplo claro de aplicación web, ya que permite acceso desde cualquier navegador sin importar el dispositivo.

**Desventajas:**

- Su rendimiento y respuesta pueden variar según el navegador.
    
- Requiere conexión a internet para funcionar.
    
- No puede emular completamente una aplicación nativa.
    

**Aplicaciones Nativas**

Las aplicaciones nativas están diseñadas específicamente para un sistema operativo, como Android o iOS. Estas aplicaciones aprovechan al máximo las capacidades del sistema y el hardware, lo que permite un mejor rendimiento y una experiencia de usuario optimizada.

**Características de aplicaciones nativas:**

- Mayor rendimiento y velocidad.
    
- Acceso directo a los recursos del sistema (cámara, GPS, almacenamiento).
    
- Requiere un desarrollo separado para cada sistema operativo.
    
- Suelen ser más pesadas y requieren mantenimiento constante.
    

**Ejemplo:** Candy Crush es una aplicación nativa que puede ejecutarse sin conexión a internet y aprovecha los recursos gráficos y de almacenamiento del dispositivo.

**Desventajas:**

- Mayor costo y tiempo de desarrollo al necesitar una versión para cada sistema operativo. Necesidad de actualizaciones y mantenimiento regulares.
    
- Ocupan más espacio en el dispositivo en comparación con aplicaciones web.
    

**Ejemplo de herramientas para probar aplicaciones nativas:** emulador Android Studio y simulador Xcode.Los emuladores y simuladores ayudan a los testers a probar en diferentes tipos de celulares cuando no se cuenta con uno físico, cambiando las resoluciones y modelos según sea necesario.

---
## Glosario

**Página estática**: sirven para mostrar principalmente información permanente, para que un usuario al navegar por la plataforma, pueda obtener información sobre el dueño de la página.

**Página dinámica**: son aquellas que permiten crear aplicaciones dentro de la propia web, otorgando una mayor interactividad con el usuario

**Sitio Responsivo**: capacidad de que un sitio o diseño web se adapte al tamaño de cualquier dispositivo (smartphone, tablet, laptop o computadora de escritorio)

**Cookies**: es un archivo creado por un sitio web que contiene pequeñas cantidades de datos y que se envían entre un emisor y un receptor.

**Cache**: es una capa de almacenamiento de datos de alta velocidad que almacena un subconjunto de datos, normalmente transitorios, de modo que las solicitudes futuras de dichos datos se atienden con mayor rapidez que si se debe acceder a los datos desde la ubicación de almacenamiento principal.

**Simuladores**: Es una aplicación que se ejecuta en una Mac, y permite usar aplicaciones de celular desde la computadora.

**Emulador**: Un emulador es un programa capaz de actuar como si fuese un equipo móvil en nuestra PC o en una Mac para probar software originalmente para celulares.

**Build**: Versión operativa de un producto de software que incorpora un subconjunto de las funciones que se incluirán en el producto final. Generalmente se identifica por un número de compilación, en lugar de por un número de versión.

**Aplicaciones Nativas**: Son las que se desarrollan de forma específica para un sistema operativo determinado al que se conoce como software development kit o SDK. Cada plataforma tiene un sistema operativo diferente. Los más conocidos son iOS y Android.

**Aplicaciones Web**: El desarrollo de la aplicación está pensado para poder ejecutarla en cualquier dispositivo o navegador. Por tanto, la aplicación estará programada con independencia del sistema operativo.