# Web Testing

## Alcance del Web Testing:

El Web Testing es una actividad esencial en el QA Manual que cubre todos los componentes de una plataforma que opera sobre un navegador web.

Esto incluye evaluar páginas dinámicas y estáticas, revisando que cada elemento funcione correctamente en diversos dispositivos y sistemas operativos, y asegurando que todos los componentes, como tipografía, resolución, y enlaces, operen de manera óptima. En algunas pruebas, el Web Testing puede solaparse con el mobile testing, ya que los dispositivos móviles también cuentan con navegadores; sin embargo, el enfoque sigue centrado en los exploradores web.

### Importancia del Web Testing:

El Web Testing tiene una relevancia crítica en la experiencia de usuario (UX) y en la calidad de la plataforma. Los usuarios esperan que el sitio web funcione correctamente en cualquier navegador (Chrome, Firefox, Safari, Edge, etc.) y en múltiples dispositivos, lo que obliga a los testers a realizar pruebas de compatibilidad exhaustivas. Además, las pruebas de usabilidad y rendimiento son fundamentales para asegurar que el sitio responda adecuadamente a los comandos del usuario, que cargue rápido y que no presente errores que afecten la interacción.

### Cobertura de los Componentes en una Plataforma Web:

Las pruebas abarcan una variedad de componentes clave:

**Tipografía y Corrección Ortográfica**: Se verifica que la tipografía y los textos cumplan con las especificaciones del equipo de diseño y redacción, respetando tanto el estilo como la ortografía.

**Resolución y Responsividad**: La plataforma debe verse bien y mantenerse funcional tanto en pantallas grandes como en dispositivos más pequeños. La adaptabilidad del sitio, o responsividad, garantiza que el contenido se ajuste automáticamente según el tamaño de la pantalla.

**Compatibilidad y Enlaces**: Cada navegador debe mostrar la plataforma de manera uniforme y funcional. Los enlaces se revisan para asegurarse de que estén correctamente direccionados y operativos.

**Colores y Servicios Web**: Se valida que los colores sean los especificados en el diseño y que los servicios web (API, conexiones a bases de datos, etc.) funcionen correctamente.

---

# Secciones a Probar

**Tipografía**

La tipografía en un sitio web forma parte del marco de UX/UI y es fundamental para mantener la consistencia visual. Es importante verificar que las fuentes utilizadas sean correctas y cumplan con los estándares predefinidos, como el tamaño, estilo y color especificados. También es clave verificar que no existan variaciones o errores en diferentes navegadores.

**Corrección Ortográfica**

La ortografía y gramática deben revisarse exhaustivamente. Muchas veces, el contenido es creado por equipos de UX Writers o legales, y su correcta redacción contribuye a la profesionalidad y credibilidad del sitio. La tarea del tester es asegurarse de que no haya errores que afecten la experiencia del usuario.

**Resolución**

La resolución garantiza que el diseño y los elementos visuales del sitio se adapten correctamente a diferentes tamaños de pantalla, desde monitores grandes hasta dispositivos móviles. Las pruebas se realizan ajustando manualmente la resolución para detectar problemas como imágenes deformadas o elementos fuera de lugar.

**Compatibilidad**

La compatibilidad implica que el sitio debe verse y funcionar de la misma manera en todos los navegadores populares (Chrome, Firefox, Edge, Safari, etc.). Los testers deben probar en múltiples navegadores para identificar diferencias en el comportamiento o apariencia que puedan impactar la experiencia del usuario.

**Links**

Los links son críticos para la navegación y funcionalidad del sitio. Es esencial verificar que todos los enlaces lleven al lugar correcto y no den errores, además de asegurarse de que no existan enlaces rotos o que lleven a páginas no deseadas.

**Colores**

El color de los elementos debe cumplir con las especificaciones del diseño. El equipo de testing debe asegurarse de que los colores sean consistentes y de que respeten los códigos especificados (#000000 para negro, #FFFFFF para blanco, etc.), ya que esto afecta tanto la estética como la accesibilidad del sitio.

---

# Herramientas de Web Testing

Para realizar pruebas web de manera efectiva, se pueden utilizar diversas herramientas especializadas que ayudan a identificar problemas y asegurar que una aplicación web funcione correctamente en diferentes entornos y dispositivos. Las herramientas más recomendadas incluyen la consola de desarrolladores, validadores HTML/CSS y verificadores de links.

**Consola de Desarrolladores**

La consola de desarrolladores, accesible generalmente mediante la tecla F12 en navegadores modernos, es una herramienta fundamental en el testing web. A través de ella, los testers pueden inspeccionar y modificar elementos en la página, ver el código HTML y CSS, así como rastrear las peticiones de red y los web services en tiempo real. La sección de “Elementos” permite verificar aspectos visuales como tipografía, colores y tamaños. Además, se puede simular la responsividad en diferentes dispositivos, asegurando que el diseño de la página se adapte adecuadamente.

**Validadores HTML/CSS**

Los validadores de HTML y CSS son herramientas en línea que revisan el código fuente de una página web, indicando posibles errores o problemas de cumplimiento con los estándares web. Estas herramientas son útiles para detectar errores de sintaxis, etiquetas mal colocadas o problemas de compatibilidad, lo cual contribuye a mejorar la accesibilidad y el rendimiento de la web. Al validar el HTML y CSS, el tester garantiza que la página será más compatible y estable en diferentes navegadores.

**Verificadores de Links**

Los verificadores de links son herramientas que rastrean y verifican los enlaces dentro de una página web, informando sobre cualquier enlace roto o mal direccionado. Esta funcionalidad es vital en el testing web, ya que los enlaces defectuosos pueden afectar la experiencia del usuario y la navegabilidad de la página. Mediante estas herramientas, el tester recibe una lista de links problemáticos junto con su ubicación y detalles, facilitando la corrección. Cada una de estas herramientas cumple un rol esencial para asegurar que una página web sea funcional, accesible y esté libre de errores, mejorando así su calidad y usabilidad.