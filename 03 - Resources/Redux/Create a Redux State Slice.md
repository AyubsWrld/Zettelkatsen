____
##### Import `createslice`: 

```javascript
import { createSlice } from '@reduxjs/toolkit'
```

- Needed for the `createSlice` function. 
____

#### Create the slice:

```javascript
export const counterSlice = createSlice()
```

- Create the slice object. listed below are the arguments. 

_____

##### Name the slice: 

```javascript
  name: 'counter',
```

- The name of the slice so that we may refer to it within the store. 
____

##### Provide an initial state: 

```javascript
  initialState: {
    value: 0
  },
```

- Initialized the state with a value of any type, in this case we have it as an integer representing count. 
____
##### Define reducers ( [[Pure Functions]] ) :

```javascript
  reducers: {
    increment: state => {
      // Redux Toolkit allows us to write "mutating" logic in reducers. It
      // doesn't actually mutate the state because it uses the Immer library,
      // which detects changes to a "draft state" and produces a brand new
      // immutable state based off those changes
      state.value += 1
    },
    decrement: state => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    }
  }
}
```

- These are the functions that have the affinity to alter the state. Notice how we have different [[Types of Reducers]] which differ in their signatures. Some are just reference state while others take in actions which have associated play loads ( Arguments ) . 
 
____

#### Export actions & slice: 

```javascript
// Action creators are generated for each case reducer function
export const { increment, decrement, incrementByAmount } = counterSlice.actions
export default counterSlice.reducer
```

- After we have defined the necessary parameters for our object we can export the actions as well as the reducer so that we may pass it into our [[Redux Store]]. 


____
### Full Code Snippet: 

```javascript
import { createSlice } from '@reduxjs/toolkit'

export const counterSlice = createSlice({
  name: 'counter',
  initialState: {
    value: 0
  },
  reducers: {
    increment: state => {
      // Redux Toolkit allows us to write "mutating" logic in reducers. It
      // doesn't actually mutate the state because it uses the Immer library,
      // which detects changes to a "draft state" and produces a brand new
      // immutable state based off those changes
      state.value += 1
    },
    decrement: state => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    }
  }
})

// Action creators are generated for each case reducer function
export const { increment, decrement, incrementByAmount } = counterSlice.actions

export default counterSlice.reducer
```
____
____
Tags: #programming #redux #react #state-management
