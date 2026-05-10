[Passport.js](https://www.passportjs.org/?utm_source=chatgpt.com) es un middleware de autenticación para [Express.js](https://expressjs.com/?utm_source=chatgpt.com).  
Su objetivo es abstraer y estandarizar cómo autenticás usuarios.

Sin Passport, vos implementás manualmente:

- login
    
- validación de credenciales
    
- generación/verificación de JWT
    
- sesiones
    
- OAuth con Google/GitHub/etc.
    

Con Passport, todo eso se organiza mediante _strategies_.

---

# Qué es una strategy

Una _strategy_ es una forma de autenticación.

Ejemplos:

- LocalStrategy → email/password
    
- JwtStrategy → JWT
    
- GoogleStrategy → login con Google
    
- GitHubStrategy → login con GitHub
    

Passport actúa como un framework de autenticación enchufable.

---

# Ejemplo conceptual SIN Passport

```txt
request
  ↓
controller
  ↓
buscar usuario
  ↓
comparar password
  ↓
crear token
  ↓
res.json(token)
```

Todo lo hacés manualmente.

---

# Ejemplo conceptual CON Passport

```txt
request
  ↓
passport.authenticate('jwt')
  ↓
strategy valida token
  ↓
req.user
  ↓
controller
```

Passport mueve la lógica de autenticación a middleware reutilizable.

---

# Cuándo se usa realmente

Passport se usa mucho cuando:

- hay múltiples métodos de login
    
- necesitás OAuth
    
- querés desacoplar autenticación
    
- trabajás con sesiones tradicionales
    

Especialmente útil para:

- Google Login
    
- GitHub Login
    
- Facebook Login
    
- Discord Login
    

Porque Passport ya trae strategies listas.

---

# JWT sin Passport

Hoy en muchas APIs modernas se hace simplemente:

```txt
Express + JWT + middleware propio
```

Porque es más simple y controlable.

Ejemplo típico:

```js
const authMiddleware = (req, res, next) => {
  const token = req.headers.authorization;

  const decoded = jwt.verify(token);

  req.user = decoded;

  next();
};
```

Y listo.

---

# Entonces, ¿vale la pena Passport?

Depende.

## Para APIs modernas REST

Muchas veces NO.

Porque:

- agrega complejidad
    
- abstrae demasiado
    
- cuesta debuggear
    
- JWT manual es sencillo
    

Hoy es muy común:

```txt
Express
+ JWT
+ middleware propio
```

---

## Para OAuth/social login

Sí tiene mucho sentido.

Ejemplo:

```txt
Login con Google
```

Sin Passport:

- manejar redirects OAuth
    
- tokens OAuth
    
- callbacks
    
- refresh tokens
    
- validaciones
    

Con Passport:

```js
passport.authenticate('google')
```

y gran parte ya viene resuelta.

---

# Arquitectura típica con Passport

```txt
src/
├── config/
│   └── passport.js
├── strategies/
│   ├── jwt.strategy.js
│   └── google.strategy.js
├── middleware/
├── controllers/
├── services/
```

---

# Ejemplo básico JWT Strategy

Instalación:

```bash
npm install passport passport-jwt
```

---

## Configuración

```js
import passport from 'passport';
import { Strategy, ExtractJwt } from 'passport-jwt';

passport.use(
  new Strategy(
    {
      jwtFromRequest: ExtractJwt.fromAuthHeaderAsBearerToken(),
      secretOrKey: process.env.JWT_SECRET
    },
    async (payload, done) => {
      try {
        return done(null, payload);
      } catch (error) {
        return done(error, false);
      }
    }
  )
);
export default passport
```

---

## Uso

```js
router.get(
  '/profile',
  passport.authenticate('jwt', { session: false }),
  controller
);
```

---

# Qué hace internamente

Passport:

1. extrae token
    
2. verifica JWT
    
3. decodifica payload
    
4. guarda usuario en `req.user`
    
5. deja pasar al controller
    

---

# Diferencia importante: Passport NO crea tokens

Passport autentica.

El JWT normalmente lo seguís creando vos:

```js
jwt.sign(...)
```

Passport solamente ayuda a validar/authenticate requests.

---

# Resumen práctico

## JWT manual

Ideal para:

- APIs REST modernas
    
- proyectos chicos/medianos
    
- control total
    
- simplicidad
    

Muy usado hoy.

---

## Passport

Ideal para:

- OAuth
    
- múltiples providers
    
- autenticación compleja
    
- apps enterprise
    
- sesiones tradicionales
    

---

# En la práctica profesional actual

Muchos proyectos modernos usan:

```txt
Express
+ jsonwebtoken
+ middleware propio
```

Y agregan Passport solamente si aparece OAuth/social login.