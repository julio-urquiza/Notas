**Nest (o NestJS)** es un **framework de Node.js** diseñado para construir **aplicaciones del lado del servidor (backend)** de manera estructurada, modular y escalable.

Se basa en **TypeScript** (aunque también permite usar JavaScript puro) y está inspirado en la arquitectura de **Angular**, aplicando conceptos como:

- **Módulos** → para organizar el código en diferentes áreas funcionales.
- **Controladores** → para manejar las rutas y las peticiones HTTP.
- **Servicios** → para la lógica de negocio y la interacción con datos.
- **Inyección de dependencias (DI)** → facilita la reutilización y testeo del código.

### Características principales:

- Soporta **REST APIs** y **GraphQL**.
- Fácil integración con **bases de datos** (MySQL, PostgreSQL, MongoDB, etc.).
- Compatible con **WebSockets** y **Microservicios**.
- Promueve una arquitectura **escalable, mantenible y limpia**.
- Tiene un ecosistema muy activo y plugins oficiales.

👉 En pocas palabras: **NestJS es al backend de Node.js lo que Angular es al frontend**: un framework de arquitectura sólida para proyectos grandes y profesionales.

---

Para instalar **NestJS** necesitás tener **Node.js** y **npm** (o **yarn/pnpm**) ya instalados en tu máquina.

### 1. Instalar el CLI de Nest

El CLI (Command Line Interface) es la forma más cómoda de crear y manejar proyectos en NestJS.

```bash
npm install -g @nestjs/cli
```

> Esto instala el comando `nest` de forma global en tu sistema.

---

### 2. Crear un nuevo proyecto

Con el CLI, podés crear un proyecto nuevo con:

```bash
nest new nombre-proyecto
```

Durante el proceso, te va a preguntar qué gestor de paquetes usar (**npm**, **yarn** o **pnpm**).

---

### 3. Entrar al proyecto

```bash
cd nombre-proyecto
```

---

### 4. Levantar el servidor

```bash
npm run start
```

Por defecto, NestJS arranca en [http://localhost:3000](http://localhost:3000/).

---

Cuando ejecutás `nest new nombre-proyecto`, NestJS genera una **estructura de carpetas y archivos** bien organizada.

Un ejemplo básico se ve así:

```
nombre-proyecto/
│
├── src/                       # Código fuente principal
│   ├── app.controller.ts      # Controlador (maneja rutas HTTP)
│   ├── app.controller.spec.ts # Test del controlador
│   ├── app.module.ts          # Módulo raíz (donde se registran controladores/servicios)
│   ├── app.service.ts         # Servicio (lógica de negocio)
│   └── main.ts                # Punto de entrada de la app
│
├── test/                      # Tests e2e (end-to-end)
│   └── app.e2e-spec.ts
│
├── node_modules/              # Dependencias instaladas
├── package.json               # Configuración del proyecto y scripts
├── tsconfig.json              # Configuración de TypeScript
└── nest-cli.json              # Configuración del CLI de NestJS
```

### 📌 Archivos clave

- **`main.ts`** → arranca la aplicación NestJS.    
   ```ts
    import { NestFactory } from '@nestjs/core';
    import { AppModule } from './app.module';
    
    async function bootstrap() {
      const app = await NestFactory.create(AppModule);
      await app.listen(3000);
    }
    bootstrap();
    ```

- **`app.module.ts`** → el "corazón" de la app, donde se registran controladores y servicios.
   ```ts
    import { Module } from '@nestjs/common';
    import { AppController } from './app.controller';
    import { AppService } from './app.service';
    
    @Module({
      imports: [],
      controllers: [AppController],
      providers: [AppService],
    })
    export class AppModule {}
    ```

- **`app.controller.ts`** → maneja las rutas (`GET /`, etc.).

   ```ts
    import { Controller, Get } from '@nestjs/common';
    import { AppService } from './app.service';
    
    @Controller()
    export class AppController {
      constructor(private readonly appService: AppService) {}
    
      @Get()
      getHello(): string {
        return this.appService.getHello();
      }
    }
    ```

- **`app.service.ts`** → contiene la lógica que usa el controlador.
   ```ts
    import { Injectable } from '@nestjs/common';
    
    @Injectable()
    export class AppService {
      getHello(): string {
        return 'Hola desde NestJS!';
      }
    }
    ```

---

Cuando levantás el servidor con `npm run start`, si entrás a `http://localhost:3000/`, vas a ver el texto `"Hola desde NestJS!"` (o `"Hello World!"` en el proyecto por defecto).
Buenísimo 🙌. Vamos a crear un **módulo de usuarios** en NestJS para que veas cómo se organiza un proyecto un poco más grande.

---

## 1. Crear el módulo de usuarios

Con el CLI de Nest:

```bash
nest generate module users
```

Esto crea:

```
src/users/users.module.ts
```

---

## 2. Crear un controlador para usuarios

```bash
nest generate controller users
```

Esto genera:

```
src/users/users.controller.ts
src/users/users.controller.spec.ts
```

Código de ejemplo (`users.controller.ts`):

```ts
import { Controller, Get, Post, Param, Body } from '@nestjs/common';
import { UsersService } from './users.service';

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  findAll() {
    return this.usersService.findAll();
  }

  @Get(':id')
  findOne(@Param('id') id: string) {
    return this.usersService.findOne(+id);
  }

  @Post()
  create(@Body() user: { name: string; email: string }) {
    return this.usersService.create(user);
  }
}
```

---

## 3. Crear un servicio para usuarios

```bash
nest generate service users
```

Esto genera:

```
src/users/users.service.ts
src/users/users.service.spec.ts
```

Ejemplo de servicio (`users.service.ts`):

```ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  private users = [
    { id: 1, name: 'Julio', email: 'julio@email.com' },
    { id: 2, name: 'Ana', email: 'ana@email.com' },
  ];

  findAll() {
    return this.users;
  }

  findOne(id: number) {
    return this.users.find(user => user.id === id);
  }

  create(user: { name: string; email: string }) {
    const newUser = { id: Date.now(), ...user };
    this.users.push(newUser);
    return newUser;
  }
}
```

---

## 4. Vincular módulo, controlador y servicio

Nest lo hace automáticamente, pero tu `users.module.ts` queda así:

```ts
import { Module } from '@nestjs/common';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';

@Module({
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

---

## 5. Importar el módulo en la app principal

En `app.module.ts`:

```ts
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { UsersModule } from './users/users.module';

@Module({
  imports: [UsersModule],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

---

## 6. Probar la API 🚀

Si levantás el servidor con:

```bash
npm run start:dev
```

Ahora podés probar:

- **GET** `http://localhost:3000/users` → devuelve todos los usuarios.
- **GET** `http://localhost:3000/users/1` → devuelve un usuario por ID.
- **POST** `http://localhost:3000/users` con body JSON:
   ```json
    { "name": "Carlos", "email": "carlos@email.com" }
    ```
    → agrega un nuevo usuario.

---
