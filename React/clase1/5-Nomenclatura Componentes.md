### 📌 Convenciones principales de nomenclatura de componentes

1. **PascalCase (UpperCamelCase)**
    - Cada componente debe comenzar con mayúscula.
    - Si tiene varias palabras, cada una empieza en mayúscula.

   ```jsx
    function MiBoton() {
      return <button>Click!</button>;
    }
    export default MiBoton;
    ```

    ✔️ Correcto: `MiBoton`, `UserCard`, `Navbar`  
    ❌ Incorrecto: `miboton`, `usercard`, `nav_bar`

---

2. **Nombres descriptivos y específicos**
    - El nombre debe reflejar lo que hace o representa.
    - Evitá nombres genéricos como `Componente1` o `Cosa`.

   ```jsx
    // Mal
    function Caja() { ... }  
    
    // Mejor
    function ProductCard() { ... }
    ```

---

3. **Archivos también en PascalCase**
    - El archivo que contiene el componente debería llamarse igual.

   ```
    src/
    └── components/
        ├── Navbar.jsx
        ├── ProductCard.jsx
        └── UserForm.jsx
    ```

---

4. **Componentes pequeños y reutilizables → sustantivos**  
    Ejemplos:
    - `Button`, `InputField`, `Card`
    
    **Componentes que representan páginas o vistas → sustantivos más específicos**  
    Ejemplos:
    - `HomePage`, `LoginPage`, `Dashboard`

---

5. **Prefijos cuando hay variantes**  
    Si un componente tiene varias versiones, usá prefijos o sufijos claros:
    
    - `PrimaryButton`, `SecondaryButton`
    - `UserCard`, `AdminCard`

---

6. **Hooks y utilidades → camelCase**  
    Si hacés un hook personalizado, **debe empezar con `use`**:
   ```jsx
    function useFetchData() { ... }
    ```

---

👉 En resumen:

- Componentes: **PascalCase** (`Navbar`, `UserCard`)
- Archivos: igual que el componente (`Navbar.jsx`)
- Hooks: **camelCase** empezando con `use` (`useAuth`, `useForm`)

---

