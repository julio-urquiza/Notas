**Commander** es una **librería de Node.js** que te facilita crear **programas de línea de comandos (CLI)**.  
Sirve para manejar **comandos**, **opciones**, **argumentos** y **mensajes de ayuda** de una manera cómoda y clara.

Se instala así:

```bash
npm install commander
```

---

## 🧑‍💻 ¿Para qué se usa?

Cuando querés hacer herramientas como:

- `mi-app init proyecto`
- `mi-app build`
- `mi-app --version`
- `mi-app --port 3000`    

Commander te permite definir esos comandos y opciones fácilmente.

---

## ✨ Ejemplo simple

`index.js`:

```js
const { program } = require('commander');

program
  .name('saludar')
  .description('Un programa para saludar personas')
  .version('1.0.0');

program
  .argument('<nombre>', 'Nombre de la persona')
  .option('-u, --upper', 'Convertir a mayúsculas')
  .action((nombre, opciones) => {
    const saludo = `Hola ${nombre}!`;
    console.log(opciones.upper ? saludo.toUpperCase() : saludo);
  });

program.parse();
```

Ejecutar:

```bash
node index.js julio
# Hola julio!

node index.js julio --upper
# HOLA JULIO!
```

---

## 🔥 ¿Por qué usarlo?

| Problema sin commander                  | Solución con commander            |
| --------------------------------------- | --------------------------------- |
| Parsing manual de args (`process.argv`) | Maneja argumentos automáticamente |
| Difícil mostrar ayuda                   | Genera `--help` solo              |
| Mucho boilerplate                       | API clara y declarativa           |

Ejemplo de ayuda automática:

```bash
node index.js --help
```

---

## 🏁 Resumen

**Commander**:

- Permite crear **CLI** de manera fácil
- Maneja comandos, opciones y argumentos
- Genera ayuda (`--help`) automáticamente
- Muy usado en herramientas reales como `vue-cli`, `vite`, etc.

---