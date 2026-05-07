# JavaScript Vanilla

![[Pasted image 20250924001355.png]]

```javascript
// recuperamos todos los botones
const buttons = document.querySelectorAll('button')

buttons.forEach(button => {
  // al hacer click en el botón, tenemos que ejecutar una función
  button.addEventListener('click', function () {
    // recuperar la id del atributo del HTML
    const id = button.getAttribute('data-id')

    // llamar a un servicio para actualizar si me gusta
    // toggleLike(id)

    if (button.classList.contains('liked')) {
      button.classList.remove('liked')
      button.innerText = 'Me gusta'
    } else {
      button.classList.add('liked')
      button.innerText = 'Quitar me gusta'
    }
  })
})
```

```html
<button data-id="123">Me gusta</button>
<button data-id="456">Me gusta</button>
<button data-id="789">Me gusta</button>

<style>
  button {
    background: #09f;
    color: #fff;
    border: 0;
    padding: 4px 8px;
    font-size: 18px;
    cursor: pointer;
  }

  body {
    background: #222;
  }
</style>
```
# React

![[Pasted image 20250924003219.png]]

```javascript
import React from "https://esm.sh/react@18.2.0"
import ReactDOM from "https://esm.sh/react-dom@18.2.0/client"

const appDomElement = document.getElementById('app')

const root = ReactDOM.createRoot(appDomElement)

const button = React.createElement('button', { "data-id": 123 }, 'Button 1')
const button2 = React.createElement('button', { "data-id": 456 }, 'Button 2')
const button3 = React.createElement('button', { "data-id": 789 }, 'Button 3')

const app = React.createElement(
  React.Fragment,
  null,
  [button, button2, button3]
)

root.render(app)
```

```html
<div id="app"></div>

<style>
  button {
    background: #09f;
    color: #fff;
    border: 0;
    padding: 4px 8px;
    font-size: 18px;
    cursor: pointer;
  }

  body {
    background: #222;
  }
</style>
```