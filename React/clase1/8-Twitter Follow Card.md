## App.jsx
``` jsx
import './App.css'
import { TwitterFollowCard } from './TwitterFollowCard.jsx'

const users = [
  {
    userName: 'midudev',
    name: 'Miguel Ángel Durán',
    isFollowing: true
  },
  {
    userName: 'pheralb',
    name: 'Pablo H.',
    isFollowing: false
  },
  {
    userName: 'PacoHdezs',
    name: 'Paco Hdez',
    isFollowing: true
  },
  {
    userName: 'TMChein',
    name: 'Tomas',
    isFollowing: false
  }
]

export function App () {
  return (
    <section className='App'>
      {
        users.map(({ userName, name, isFollowing }) => (
          <TwitterFollowCard
            key={userName}
            userName={userName}
            initialIsFollowing={isFollowing}
          >
            {name}
          </TwitterFollowCard>
        ))
      }
    </section>
  )
}
```
---
## TwitterFollowCard.jsx
``` jsx
import { useState } from 'react'

export function TwitterFollowCard ({ children, userName, initialIsFollowing }) {
  const [isFollowing, setIsFollowing] = useState(initialIsFollowing)

  console.log('[TwitterFollowCard] render with userName: ', userName)

  const text = isFollowing ? 'Siguiendo' : 'Seguir'
  const buttonClassName = isFollowing
    ? 'tw-followCard-button is-following'
    : 'tw-followCard-button'

  const handleClick = () => {
    setIsFollowing(!isFollowing)
  }

  return (
    <article className='tw-followCard'>
      <header className='tw-followCard-header'>
        <img
          className='tw-followCard-avatar'
          alt='El avatar de midudev'
          src={`https://unavatar.io/${userName}`}
        />
        <div className='tw-followCard-info'>
          <strong>{children}</strong>
          <span className='tw-followCard-infoUserName'>@{userName}</span>
        </div>
      </header>

      <aside>
        <button className={buttonClassName} onClick={handleClick}>
          <span className='tw-followCard-text'>{text}</span>
          <span className='tw-followCard-stopFollow'>Dejar de seguir</span>
        </button>
      </aside>
    </article>
  )
}
```
---
## App.css
``` css
.tw-followCard {
  display: flex;
  align-items: center;
  color: #fff;
  font-size: .8rem;
  justify-content: space-between;
}

.tw-followCard-header {
  display: flex;
  align-items: center;
  gap: 4px
}

.tw-followCard-info {
  display: flex;
  flex-direction: column;
}

.tw-followCard-infoUserName {
  opacity: .6;
}

.tw-followCard-avatar {
  width: 48px;
  height: 48px;
  border-radius: 1000px;
}

.tw-followCard-button {
  cursor: pointer;
  margin-left: 16px;
  border: 0;
  border-radius: 999px;
  padding: 6px 16px;
  font-weight: bold;
  border: 1px solid #000;
  transition: .3s ease background-color;
}

.tw-followCard-button:hover {
  opacity: .8;
}

.tw-followCard-text {
  display: block;
}

.tw-followCard-button.is-following {
  border: 1px solid #bbb;
  background: transparent;
  color: #fff;
  width: 140px;
}

.tw-followCard-button.is-following:hover {
  background-color: rgba(255, 0, 0, 0.178);
  color: red;
  border: 1px solid red;
  transition: .3s ease all;
  opacity: 1;
}

.tw-followCard-button.is-following:hover .tw-followCard-text {
  display: none;
}

.tw-followCard-button.is-following:hover .tw-followCard-stopFollow {
  display: block;
}

.tw-followCard-stopFollow {
  display: none;
}
```
---
## main.jsx
``` jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import { App } from './App.jsx'
import './index.css'

const root = ReactDOM.createRoot(document.getElementById('root'))

root.render(
  <App />
)
```
---
## index.css
``` css
body {
  margin: 0;
  background: #222;
  font-family: system-ui;
  display: grid;
  place-content: center;
  min-height: 100vh;
}

.App {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
```
---
