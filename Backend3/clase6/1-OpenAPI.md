OpenAPI es **una especificación estándar para describir APIs REST**.  
Antes se llamaba **Swagger** (quizás te suene ese nombre).

Básicamente, es un formato (generalmente en **JSON o YAML**) que permite definir de forma clara:

- **Qué endpoints** tiene una API (`/users`, `/products`, etc.).
- **Qué métodos HTTP** acepta (GET, POST, PUT, DELETE...).
- **Qué parámetros** recibe (query params, headers, body...).
- **Qué respuestas** devuelve (códigos de estado, esquemas de datos, ejemplos).
- **Seguridad** (autenticación con tokens, OAuth2, API keys...).

### ¿Por qué es útil?

- 📖 **Documentación automática**: puedes generar documentación visual y navegable (como Swagger UI).
- 🤝 **Comunicación clara**: equipos de backend y frontend hablan el mismo “contrato” de la API.
- ⚙️ **Generación de código**: a partir del archivo OpenAPI puedes generar clientes en varios lenguajes (Node, Java, Python, etc.) o incluso servidores base.
- ✅ **Validación**: puedes validar si tu API realmente responde lo que prometiste en la definición.

### Ejemplo muy simple en YAML:

```yaml
openapi: 3.0.0
info:
  title: API de ejemplo
  version: 1.0.0
paths:
  /users:
    get:
      summary: Obtener lista de usuarios
      responses:
        '200':
          description: Lista de usuarios
          content:
            application/json:
              schema:
                type: array
                items:
                  type: string
```

Con este archivo, podrías abrir Swagger UI y ver la documentación lista para probar. 🚀
