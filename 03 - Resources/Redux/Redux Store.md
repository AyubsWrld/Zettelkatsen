#### What is a Redux Store?
____
A redux store is essentially just an object that contains a reference to state and actions which can alter the internal state. when these actions are called, A UI re-render is triggered.  
#### Create a Redux Store
___
```javascript
import { configureStore } from '@reduxjs/toolkit

export default configureStore({
	reducer: {}
})
```


#### Providing Store to React
____
Simply wrap it around a `<Provider>` tag and pass store prop into `store`. 

```javascript
import React from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App'
import store from './app/store'
import { Provider } from 'react-redux'

const root = createRoot(document.getElementById('root')!)

root.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
)
```


____
Tags: #programming #redux #react #state-management