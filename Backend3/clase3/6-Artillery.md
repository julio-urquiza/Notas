 **Artillery** es una herramienta de **pruebas de carga y rendimiento** para aplicaciones web, APIs y servicios backend.  
Sirve para simular múltiples usuarios o peticiones concurrentes y así medir cómo responde tu aplicación bajo diferentes niveles de tráfico.

👉 En otras palabras: con Artillery puedes comprobar si tu API o servidor soporta, por ejemplo, 100, 1.000 o 10.000 usuarios al mismo tiempo, cuánto tarda en responder y si se mantiene estable.

---
### Características principales:

- Es **open source** (aunque tiene versión Pro con más funcionalidades).
- Está escrita en **Node.js**, por lo que se instala fácilmente con `npm`.
- Soporta:
    - **HTTP/HTTPS**
    - **WebSockets**
    - **Socket.io**
    - **Lambda (AWS)**
- Permite definir **escenarios realistas**: no solo hacer requests, sino también flujos completos (login → consulta → logout).
- Genera reportes con métricas como:
    - Tiempo de respuesta (latencia).
    - Cantidad de requests por segundo.
    - Errores y timeouts.

---

### Ejemplo básico

1. Instalarlo globalmente:

```bash
npm install -g artillery
```

2. Crear un archivo de configuración (`test.yml`):

```yaml
config:
  target: "http://localhost:3000"
  phases:
    - duration: 60
      arrivalRate: 10  # 10 usuarios nuevos por segundo durante 60s

scenarios:
  - flow:
      - get:
          url: "/api/users"
```

3. Ejecutar la prueba:

```bash
artillery run test.yml
```

Esto simulará **10 usuarios por segundo** durante **1 minuto** haciendo peticiones a `/api/users`.

4. Ver resultados en consola o generar un **reporte HTML**:

```bash
artillery run --output report.json test.yml
artillery report report.json
```

---
