# 🔹 Módulo 1: Fundamentos específicos de C#

## 1. 🧱 Value types vs Reference types

Esto en C# es **crítico** porque afecta memoria, performance y bugs.

### ✔ Value types (tipos por valor)

- `int`, `double`, `bool`, `DateTime`, `struct`
- Se copian **por valor**

```csharp
int a = 10;
int b = a;
b = 20;

Console.WriteLine(a); // 10
```

👉 `a` no cambia porque `b` es una copia

---

### ✔ Reference types (tipos por referencia)

- `class`, `object`, `string`, arrays

```csharp
class User {
    public string Name { get; set; }
}

var user1 = new User { Name = "Julio" };
var user2 = user1;

user2.Name = "Carlos";

Console.WriteLine(user1.Name); // Carlos
```

👉 Ambos apuntan al mismo objeto

---

## 2. 🧠 `var` vs `dynamic`

### ✔ `var` (tipado estático inferido)

El compilador infiere el tipo

```csharp
var name = "Julio"; // string
```

👉 Es **fuertemente tipado igual**

---

### ✔ `dynamic` (tipado dinámico)

Se resuelve en runtime

```csharp
dynamic x = "Hola";
x = 10;
x = true;
```

⚠️ Evitar salvo casos específicos (reflection, interoperabilidad)

---

## 3. 🏗 Propiedades (`get; set;`)

En C# no se usan getters/setters manuales como en Java.

```csharp
class User {
    public string Name { get; set; }
}
```

---

### ✔ Propiedades con lógica

```csharp
private int age;

public int Age {
    get { return age; }
    set {
        if (value < 0) throw new ArgumentException("Edad inválida");
        age = value;
    }
}
```

---

### ✔ `init` (inmutabilidad parcial)

```csharp
class User {
    public string Name { get; init; }
}

var user = new User { Name = "Julio" };
// user.Name = "Otro"; ❌ no permitido
```

---

## 4. 🧬 `class` vs `record`

### ✔ `class` (mutable por defecto)

```csharp
class User {
    public string Name { get; set; }
}
```

Comparación por referencia

---

### ✔ `record` (inmutable + comparación por valor)

```csharp
record User(string Name);
```

```csharp
var u1 = new User("Julio");
var u2 = new User("Julio");

Console.WriteLine(u1 == u2); // true
```

👉 Muy usado en:

- DTOs
    
- Respuestas de APIs
    

---

## 5. ⚙️ `struct`

Tipo por valor definido por vos

```csharp
struct Point {
    public int X;
    public int Y;
}
```

👉 Cuándo usar:

- Objetos pequeños
    
- Inmutables
    
- Sin identidad
    

⚠️ No abusar

---

## 6. 📦 Namespaces

Organizan el código

```csharp
namespace MyApp.Models {
    class User { }
}
```

Uso:

```csharp
using MyApp.Models;
```

👉 En .NET moderno:

```csharp
namespace MyApp.Models;

class User { }
```

---

## 7. 🚨 Manejo de excepciones

```csharp
try {
    int x = int.Parse("abc");
}
catch (FormatException ex) {
    Console.WriteLine("Error de formato");
}
finally {
    Console.WriteLine("Siempre se ejecuta");
}
```

---

### ✔ Buenas prácticas

- No usar excepciones para lógica normal
    
- Capturar excepciones específicas
    
- No hacer `catch (Exception)` sin motivo
    

---

# 🧪 Ejercicio guiado (importante)

## 🎯 Parte 1: con `class`

Modelá:

```csharp
class User {
    public string Name { get; set; }
    public int Age { get; set; }
}
```

Probar:

- Crear 2 usuarios
    
- Asignar uno a otro
    
- Modificar uno y ver qué pasa
    

---

## 🎯 Parte 2: con `record`

```csharp
record User(string Name, int Age);
```

Probar:

- Comparar dos usuarios iguales
    
- Usar `with`
    

```csharp
var u1 = new User("Julio", 30);
var u2 = u1 with { Age = 31 };
```

---

# 🧠 Conceptos clave que TENÉS que llevarte

Si esto no te queda claro, el resto se complica:

- Diferencia real entre **value vs reference**
    
- Cuándo usar `record`
    
- Cómo funcionan las propiedades
    
- Evitar `dynamic` salvo casos específicos
    

---

# 🚀 Siguiente paso

Si querés avanzar bien:

👉 Te puedo:

- corregir el ejercicio que hagas
    
- darte un mini challenge más realista
    
- o pasar al **Módulo 2 (POO aplicada en C#)**
    

Decime cómo querés seguir.