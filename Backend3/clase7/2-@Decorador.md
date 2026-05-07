La sintaxis de la **`@`** que ves en `@Module(...)`, `@Injectable()`, `@Controller()`, etc. se llama **decorador**.

---

### 📌 Origen

- **No es algo exclusivo de TypeScript**.
- Es una propuesta de **ECMAScript (JavaScript)** que todavía está en desarrollo (Stage 3).
- TypeScript la soporta desde hace años como una **feature experimental**, y por eso la ves mucho en frameworks como NestJS o Angular.

---

### 📌 Qué hace un decorador

Un decorador es básicamente **una función que recibe una clase, método o propiedad**, y puede:

- Agregar **metadatos** (información extra).
- Modificar el comportamiento.
- Sustituir la definición por otra.

Ejemplo simple en TypeScript:

```ts
function MiDecorador(consola: string) {
  return function (target: any) {
    console.log(`Decorando la clase: ${consola}`);
  };
}

@MiDecorador('Hola!')
class Persona {}
```

Salida en consola:

```
Decorando la clase: Hola!
```

---

### 📌 En NestJS

Nest aprovecha esta característica para:

- `@Module` → definir qué controladores/servicios tiene un módulo.
- `@Controller` → marcar una clase como controlador HTTP.
- `@Injectable` → marcar un servicio para que se pueda inyectar en otros.

---

👉 Entonces, **la `@` no es exclusiva de TypeScript**, pero hoy la mayoría de los proyectos la usan con TypeScript porque ahí ya está bien integrada.

---

Se puede usar en JavaScript, pero con algunas aclaraciones:

---

### 📌 Estado actual

- Los **decoradores** forman parte de una propuesta oficial de **ECMAScript** (la organización que define el estándar de JavaScript).
- Hoy están en **Stage 3** → significa que ya están bastante maduros, y varios entornos modernos los soportan (Babel, TypeScript, e incluso Node.js 20+ con ciertas flags).
- Antes, solo se podían usar en **TypeScript** (porque lo implementó como feature experimental antes de que entrara al estándar).

---

### 📌 Ejemplo en **JavaScript moderno**

Si usás **Node.js 20+** o un bundler que soporte decoradores, podés hacer algo así:

```js
function logClass(target) {
  console.log(`Decorando la clase: ${target.name}`);
}

@logClass
class Persona {}

const p = new Persona();
```

Salida:

```
Decorando la clase: Persona
```

---

### 📌 Pero ojo

Para que funcione en **JavaScript puro** hoy, normalmente necesitás:

1. Un **transpilador** (ej: Babel con plugin de decoradores, o SWC).
2. O activar flags en Node (por ejemplo `--harmony`).

Por eso en la práctica:

- En proyectos **profesionales** casi siempre se usan con **TypeScript** (ejemplo NestJS, Angular).
- En **JavaScript puro** todavía no es tan común, pero ya es posible en entornos modernos.

---

👉 Resumen:

- **Sí se puede usar en JS.**
- Necesitás un entorno que soporte decoradores (Node 20+, Babel, etc.).
- En TypeScript es mucho más estable y por eso es donde más se ven.

---

En general **un decorador “decora” lo que tiene justo debajo”**, pero depende del tipo de decorador y del target: clase, método, propiedad o parámetro. Te explico con detalle:

---

### 1️⃣ Decorador de **clase**

Se coloca justo arriba de una clase y recibe la **clase completa** como argumento.

```ts
function logClass(target: any) {
  console.log(`Decorando la clase: ${target.name}`);
}

@logClass
class Persona {}
```

- Aquí `@logClass` **decora la clase `Persona`** directamente.
- NestJS hace algo similar con `@Module()`, `@Injectable()`, etc.

---

### 2️⃣ Decorador de **método**

Se coloca justo arriba de un método y recibe:

- La clase (target),
- El nombre del método,
- Descriptor del método.

```ts
function logMethod(target: any, key: string, descriptor: PropertyDescriptor) {
  const original = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.log(`Llamando a ${key}`);
    return original.apply(this, args);
  };
}

class Persona {
  @logMethod
  saludar() {
    console.log("Hola!");
  }
}

new Persona().saludar();
```

Salida:

```
Llamando a saludar
Hola!
```

- Decorador **afecta solo al método** que está justo debajo.

---

### 3️⃣ Decorador de **propiedad**

Se coloca sobre una propiedad de la clase:

```ts
function logProperty(target: any, key: string) {
  let value = target[key];
  Object.defineProperty(target, key, {
    get: () => {
      console.log(`Accediendo a ${key}`);
      return value;
    },
    set: (v) => {
      console.log(`Modificando ${key}`);
      value = v;
    },
  });
}

class Persona {
  @logProperty
  nombre = "Julio";
}

const p = new Persona();
p.nombre = "Ana"; // Modificando nombre
console.log(p.nombre); // Accediendo a nombre
```

---

### ⚡ Reglas generales

1. El decorador **siempre debe colocarse justo arriba** de lo que va a afectar.
2. Depende del tipo: clase, método, propiedad o parámetro.
3. No “salta” ni decora cosas lejanas: no podés poner un `@Module()` arriba de un método y que afecte otra clase.

---
