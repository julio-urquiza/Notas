## Qué es bcrypt

bcrypt es una librería usada para **hashear contraseñas** antes de guardarlas en la base de datos.

La idea principal es:

> Nunca se guardan contraseñas reales en texto plano.

Por ejemplo, esto está mal:

```json
{
  "email": "julio@gmail.com",
  "password": "123456"
}
```

Porque si alguien accede a la base de datos, ve todas las contraseñas.

Con bcrypt hacemos esto:

```json
{
  "email": "julio@gmail.com",
  "password": "$2b$10$Qx8..."
}
```

Eso es un hash.

---

# Cómo explicarlo conceptualmente

## 1. Hashing

bcrypt transforma una contraseña en un valor irreconocible mediante un algoritmo matemático.

```txt
"123456"
↓
"$2b$10$Qx8..."
```

Y algo importante:

- No se puede “desencriptar”
    
- bcrypt no guarda la contraseña original
    
- solo genera un hash
    

Entonces cuando el usuario inicia sesión:

1. escribe `"123456"`
    
2. bcrypt vuelve a hashear eso
    
3. compara el resultado con el hash guardado
    

Si coinciden → login correcto.

---

# Diferencia entre hashing y encriptación

Esto suele preguntarse mucho.

## Encriptación

Se puede revertir con una clave.

```txt
texto → encriptado → desencriptado
```

Ejemplo:

- HTTPS
    
- JWT firmados
    
- archivos cifrados
    

---

## Hashing

No está pensado para revertirse.

```txt
password → hash
```

Por eso se usa para contraseñas.

---

# Qué hace especial a bcrypt

No cualquier hash sirve para passwords.

Algoritmos como:

- MD5
    
- SHA1
    

son demasiado rápidos y hoy son inseguros para contraseñas.

bcrypt agrega:

---

## Salt

bcrypt genera un valor aleatorio llamado _salt_.

Entonces:

```txt
123456
```

no genera siempre el mismo hash.

Eso evita ataques con:

- rainbow tables
    
- hashes precalculados
    

---

## Cost factor

bcrypt también puede hacerse más lento intencionalmente.

```js
bcrypt.hash(password, 10)
```

Ese `10` es el número de rondas.

Más rondas:

- más seguro
    
- más lento
    

La idea es dificultar ataques de fuerza bruta.

---

# Cómo mostrarlo en Express

## Instalación

```bash
npm install bcrypt
```

---

# Hashear password al registrarse

```js
import bcrypt from 'bcrypt';

const password = '123456';

const hashedPassword = await bcrypt.hash(password, 10);

console.log(hashedPassword);
```

---

# Comparar password en login

```js
const isValid = await bcrypt.compare(
  '123456',
  hashedPassword
);

console.log(isValid);
```

Devuelve:

```js
true
```

o

```js
false
```

---

# Dentro de una arquitectura

En un proyecto Express profesional normalmente bcrypt vive en el service de autenticación.

Ejemplo:

```txt
AuthController
    ↓
AuthService
    ↓
bcrypt
    ↓
UserRepository
```

Porque:

- el controller no debería manejar lógica criptográfica
    
- el service maneja reglas de negocio
    
- el repository solo accede a datos
    

---

# Conceptualmente

> bcrypt es una librería que usamos para proteger contraseñas.  
> En vez de guardar la contraseña real, guardamos un hash irreversible.  
> Cuando el usuario inicia sesión, bcrypt compara la contraseña ingresada con el hash almacenado.  
> Además bcrypt usa salt y múltiples rondas para dificultar ataques de fuerza bruta.