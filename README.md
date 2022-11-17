# React Redux Template

This goes through the set up of Redux toolkit within a React app and follow

## Create React App

```
npx create-react-app react-redux-template
```

## Install redux and redux toolkit
In the root dir:
`npm i @reduxjs/toolkit react-redux`


### Set up the store
>This stores the state of the entire app

In the src directory add a folder called app

In the app directory create a file called store.js


Inside store.js
1. Add
```javaScript
import { configureStore } from "@reduxjs/toolkit";

export const store = configureStore({
    reducer: {
       // This is where we will put our reducers later
    })
```

In index.js:
1. Import the store that we just created
2. Import Provider from react-redux
```javaScript
import { store } from './app/store';
import { Provider } from 'react-redux';
```
3. Wrap the App with the Provider and pass in the store
```javaScript
<React.StrictMode>
  <Provider store={store}>
    <App />
  </Provider>
</React.StrictMode>
```
### Creating a slice
> This is where we define we will 'slice' the state objects into multiple slices of state and define reducer logic 

In the src directory add a folder called features

In the features folder add a folder that will contain your slice.  Name it someting that makes sense semanticly (what does it do?)

Add a file that is this folder name plus slice.js

Examples:
- [ ] /counter/counterSlice.js
- [x] /sequencer/sequencerSlice.js

In sequencerSlice.js
1. Import createSlice from @reduxjs/toolkit
```javaScript
import { createSlice } from '@reduxjs/toolkit'
```
2. Set an intitial state
```javaScript
const initialState = {
  row1: [null, null, null, null, null, null, null, null],
  row2: [null, null, null, null, null, null, null, null],
  row3: [null, null, null, null, null, null, null, null],
  row4: [null, null, null, null, null, null, null, null],
  row5: [null, null, null, null, null, null, null, null],
  row6: [null, null, null, null, null, null, null, null],
  row7: [null, null, null, null, null, null, null, null]
}
```
3. Define and export the slice
```javaScript
 export const sequencerSlice = createSlice({
    name: 'sequencer',
    initialState,
    reducers: {
        // these are the actions
        activateRow1: (state) => {
        state.row1 
      }
    }
 })
```

4. Export actions
```javaScript
export const { activateRow1 } = counterSlice.actions;
```

5. Export reducer
```javaScript
export default sequencerSlice.reducer;
```

### Import reducer to the store
In store.js 
1. Import
```javaScript
import sequencerReducer from '../features/sequencer/sequencerSlice'
```
2. Add reducer to the store in our place holder from eairler
```javaScript
export const store = configureStore({
    reducer: {
       // This is where we will put our reducers later
       sequencer: sequencerReducer
    })
```

### Import Actions, useSelector and use dispatch
Make a new component in the features folder called Sequences.js

In Sequences.js
```javaScript
import { useSelector, useDispatch } from 'react-redux';
import { activateRow1 } from './sequencerSlice'
```
