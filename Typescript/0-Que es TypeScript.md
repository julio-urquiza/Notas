TypeScript es un **lenguaje de programación desarrollado por Microsoft** que actúa como un **superset de JavaScript**. Esto significa que **todo el código JavaScript válido también es TypeScript**, pero TypeScript agrega **características adicionales** orientadas a mejorar la calidad, mantenibilidad y escalabilidad del código.

### Definición técnica

TypeScript añade a JavaScript un **sistema de tipos estáticos opcional** y herramientas avanzadas de desarrollo. El código TypeScript **no se ejecuta directamente** en el navegador o en Node.js: primero se **transpila** a JavaScript estándar.

---

## ¿Para qué sirve TypeScript?

Su objetivo principal es:

- Detectar errores **en tiempo de desarrollo** (antes de ejecutar la app).
- Facilitar el mantenimiento de **aplicaciones grandes y complejas**.
- Mejorar la experiencia de desarrollo con **autocompletado, refactors y navegación de código** más precisa.

---

## Características principales

### 1. Tipado estático (opcional)

Permite definir el tipo de datos que una variable, función o clase puede manejar.

```ts
function sumar(a: number, b: number): number {
  return a + b;
}
```

Esto evita errores comunes como pasar un string donde se espera un número.

---

### 2. Inferencia de tipos

No siempre es necesario declarar tipos explícitamente; TypeScript puede inferirlos.

```ts
let nombre = "Juan"; // TypeScript infiere que es string
```

---

### 3. Programación orientada a objetos avanzada

Amplía las capacidades de JavaScript con:

- Interfaces
- Tipos
- Clases abstractas
- Modificadores de acceso (`public`, `private`, `protected`)
- Genéricos

```ts
interface Usuario {
  id: number;
  email: string;
}
```

---

### 4. Compatibilidad total con JavaScript

- Funciona con librerías JS existentes.
- Se puede migrar un proyecto JavaScript **gradualmente** a TypeScript.

---

### 5. Mejor tooling

TypeScript se integra profundamente con:

- VS Code
- Angular
- React    
- Node.js
- Frameworks backend (NestJS, Express con tipado) 

---

## Diferencia clave entre JavaScript y TypeScript

|JavaScript|TypeScript|
|---|---|
|Tipado dinámico|Tipado estático opcional|
|Errores en runtime|Errores en compilación|
|Menor escalabilidad|Ideal para proyectos grandes|
|Menos autocompletado|Autocompletado preciso|

---

## ¿Dónde se usa TypeScript?

En la industria se utiliza ampliamente en:

- Frontend (Angular, React, Vue)
- Backend (Node.js, NestJS)
- Microservicios
- Aplicaciones empresariales
- Proyectos financieros y de gran escala

---

## Resumen corto

TypeScript es JavaScript **con superpoderes**: mantiene la flexibilidad de JS, pero agrega control, seguridad y estructura, lo que lo hace especialmente valioso en entornos profesionales.
