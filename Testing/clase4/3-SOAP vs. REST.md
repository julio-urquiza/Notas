## SOAP vs. REST: Comparación

En el desarrollo de APIs, SOAP (Simple Object Access Protocol) y REST (Representational State Transfer) son los enfoques más comunes para la transmisión de datos. Ambos permiten la comunicación entre aplicaciones, pero se diferencian en su estructura y usos.

### SOAP

SOAP es un protocolo estándar que sigue reglas estrictas para garantizar transacciones seguras y confiables. Utiliza XML exclusivamente para estructurar los datos, lo que lo convierte en una opción sólida para aplicaciones que requieren seguridad y consistencia.

- Rapidez: SOAP es más lento debido a su estructura compleja y a la carga de información que maneja.
    
- Complejidad: Requiere más configuraciones, ya que debe cumplir con un conjunto de reglas estrictas.
    
- Seguridad: Ofrece mayor seguridad nativa gracias a sus estándares integrados, como WS-Security, que protege la integridad de los datos.
    
- Popularidad: Menos popular para aplicaciones web modernas, aunque sigue siendo utilizado en entornos empresariales que requieren alta seguridad, como banca y finanzas.
    

### REST

REST es una arquitectura más flexible y ligera que permite varios formatos de respuesta, incluyendo JSON, XML o texto plano. Su simplicidad y velocidad lo han convertido en la opción más popular para aplicaciones web y móviles.

- Rapidez: REST es más rápido, gracias a su estructura simple y al uso de JSON, que reduce el tiempo de procesamiento.
    
- Complejidad: Su diseño es menos complejo, permitiendo una implementación más rápida y flexible.
    
- Seguridad: Aunque REST no incluye mecanismos de seguridad nativos, se puede combinar con HTTPS para proteger la comunicación.
    
- Popularidad: Muy popular en aplicaciones web y móviles, especialmente donde la velocidad y flexibilidad son prioritarias.
---

# Glosario

**API**: Interfaz de Programación de Aplicaciones.

**Endpoint**: los endpoints son las URLs de un API o un backend que responden a una petición.

**Hotfix**: Parche rápido. Cuando se implementa un cambio en el ambiente de producción, por un defecto encontrado.

**JSON**: JavaScript Object Notation. El formato JSON se utiliza para estructurar datos en forma de texto y permite el intercambio de información entre aplicaciones de manera sencilla, liviana y rápida

**Microservicios**: conjunto de pequeños servicios en donde cada uno va a ejecutar su propio proceso y se va a comunicar con una API.

**Mock**: prototipo de pantalla de un sistema

**REST**: La transferencia de estado representacional (REST) es un conjunto de principios arquitectónicos.

**Rollback**: volver a la versión anterior de software

**Sesgo de confirmación**: elemento de la psicología humana que puede dificultar la aceptación de información.

**SOAP**: el protocolo simple de acceso a objetos (SOAP) es un protocolo oficial, cuyo mantenimiento está a cargo del Consorcio World Wide Web.

**UAT**: Testing de Aceptación de Usuario.