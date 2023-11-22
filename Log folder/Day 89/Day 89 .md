# Day 89

Tags: Redux
Date: October 26, 2023
Status: Done

**Tasks of the day**

- Middleware in Redux

---

### Middleware

![Screen Shot 2023-10-26 at 3.40.16 PM.png](Day%2089%2037acf052dd6d438da079eb1ba922f81a/Screen_Shot_2023-10-26_at_3.40.16_PM.png)

In Redux, middleware runs between when an action is dispatched and when that action is passed along to the reducer. By this point, you’re familiar with the way data flows through Redux: actions are dispatched to the store, where they are processed by reducers that produce a new state; that new state becomes accessible to all the components that reference it, causing those components to update.

Middleware intercepts actions after they are dispatched and before they are passed along to the reducer. Some common tasks that middleware performs include logging, caching, adding auth tokens to request headers, crash reporting, routing, and making asynchronous requests for data. You can add any of these functionalities to your apps by using popular open-source middleware. Of course, you can also write your own middleware to solve problems that are specific to your application and its architecture.

---

### Thunks

One of the most flexible and popular ways to add asynchronous functionality to Redux involves using thunks. A thunk is a higher-order function that wraps the computation we want to perform later. For example, this `add()` function returns a thunk that will perform `x+y`when called.

```jsx
const add = (x,y) => {
  return () => {
    return x + y; 
  } 
}
```

---

### **createAsyncThunk()**

`createAsyncThunk()` is a function with two parameters, an action type string, and an asynchronous callback, that generates a thunk action creator that will run the provided callback and automatically dispatch promise lifecycle actions as appropriate so that you don’t have to dispatch pending/fulfilled/rejected actions by hand.

To use `createAsyncThunk()`, you’ll first need to import it from Redux Toolkit like so:

```jsx
import { createAsyncThunk } from '@reduxjs/toolkit';

```

---

### Review

- Learned about Redux middleware and wrote your own simple logging middleware
- Encountered thunks and learned about how valuable thunks are for deferring computation
- Learned the three promise lifecyle actions: pending, fufilled, and rejected
- Learned how to use `createAsyncThunk()`, which abstracts the process of handling promise lifecycle states according to best practices/common design paradigms
- Imported `createAsyncThunk` from the Redux Toolkit:

```jsx
import { createAsyncThunk } from '@reduxjs/toolkit';
```

- Created action creators using `createAsyncThunk()`.
- Made your reducers respond to pending/fulfilled/rejected promise lifecycle actions by supplying the `extraReducers` property to `createSlice()`.