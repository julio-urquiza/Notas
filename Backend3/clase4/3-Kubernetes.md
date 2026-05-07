Kubernetes (muchas veces abreviado como **K8s**) es una **plataforma de orquestación de contenedores**.  
Su función principal es ayudarte a **automatizar** el despliegue, la gestión y la escalabilidad de aplicaciones que se ejecutan dentro de **contenedores** (por ejemplo, creados con **Docker**).

Imagina que tienes varios microservicios (API, frontend, base de datos, workers) corriendo en contenedores. Si los ejecutás manualmente, se vuelve complicado: ¿cómo balanceás la carga?, ¿qué pasa si un contenedor se cae?, ¿cómo lo reemplazás?, ¿cómo escalar de 3 a 300 instancias?  
Ahí es donde entra Kubernetes.

### Principales características:

- **Automatización**: despliega y gestiona contenedores automáticamente.
    
- **Escalabilidad**: puede aumentar o reducir la cantidad de contenedores según la carga.
    
- **Alta disponibilidad**: si un contenedor falla, Kubernetes lo reinicia o crea otro en otro servidor.
    
- **Balanceo de carga**: distribuye el tráfico entre los distintos contenedores.
    
- **Gestión de configuración y secretos**: guarda claves, contraseñas y configuraciones de forma segura.
    
- **Portabilidad**: funciona en tu PC, en servidores físicos, en la nube (Google Cloud, AWS, Azure, etc.).
    

### Conceptos básicos de Kubernetes:

- **Cluster**: conjunto de máquinas (físicas o virtuales) donde corre Kubernetes.
    
- **Node**: cada máquina dentro del cluster.
    
- **Pod**: la unidad mínima, que puede contener uno o más contenedores.
    
- **Deployment**: define cómo se despliegan y actualizan los pods.
    
- **Service**: expone un conjunto de pods para que puedan recibir tráfico.
    

👉 En pocas palabras: **Kubernetes es el "sistema operativo de la nube" para aplicaciones en contenedores**.
