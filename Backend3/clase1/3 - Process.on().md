## Descripción de cómo usar `process.on()` en Node.js

En Node.js, el objeto global `process` es un EventEmitter que permite gestionar eventos específicos del proceso. Mediante el método `process.on()`, se pueden establecer listeners (escuchas) para capturar y manejar estos eventos. Esto es útil para realizar acciones cuando ocurren ciertos eventos, como cuando el proceso está a punto de finalizar, cuando se produce una excepción no capturada, o cuando se reciben mensajes en procesos secundarios.

### Eventos Comunes para `process.on()`
1. **Evento** **`exit`** **:**
    - El evento `exit` se emite cuando el proceso está a punto de finalizar. Es un evento útil para realizar tareas de limpieza, como cerrar conexiones a bases de datos o escribir datos finales en un archivo.
    
    - Este evento recibe un código de salida que indica si el proceso terminó exitosamente o con un error.    
    
2. **Evento** **`uncaughtException`** **:**
    - El evento  `uncaughtException` se dispara cuando se produce una excepción que no ha sido manejada en ninguna parte del código. Capturar este evento es crucial para evitar que la aplicación se cierre inesperadamente.

    - Aunque es útil para registrar errores y realizar acciones de emergencia, se recomienda no confiar completamente en este evento para el manejo de errores, ya que el estado de la aplicación puede ser inconsistente.

3. **Evento** **`message`** **:**
    - El evento `message` es relevante cuando se trabaja con procesos secundarios (`child processes`). Este evento se utiliza para recibir mensajes enviados desde el proceso secundario al proceso principal.

    - Es fundamental para la comunicación entre procesos, permitiendo la coordinación y el intercambio de datos entre ellos.        


### Códigos de Salida Comunes en `process.exit()`

El método `process.exit()` finaliza el proceso Node.js, y se puede pasar un código de salida para indicar el motivo de la finalización. Algunos de los códigos de salida más comunes son:

1. **Código**  **`0`** **:**
    - Indica que el proceso terminó exitosamente sin errores. Este es el código por defecto si no se especifica otro código.       
2. **Código** **`1`** **:**
    - Indica que ocurrió un error general y el proceso finalizó sin éxito. Este código se utiliza comúnmente cuando hay un error sin manejar o una condición inesperada.
3. **Códigos** **`>1`**  **:**
    - Otros códigos de salida pueden indicar diferentes tipos de errores o estados específicos definidos por la aplicación. Por ejemplo, un código `2` podría indicar un error de sintaxis, o un código `3` podría referirse a un fallo en la inicialización.

### Conclusión

El uso de `process.on()` permite manejar eventos importantes del ciclo de vida del proceso en Node.js, ofreciendo la posibilidad de realizar tareas de limpieza, manejar excepciones inesperadas, y gestionar la comunicación entre procesos. Además, comprender los códigos de salida en `process.exit()` ayuda a identificar cómo y por qué finalizó un proceso, lo que es esencial para el monitoreo y depuración de aplicaciones en producción.