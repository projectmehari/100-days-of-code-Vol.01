# Day 88

Tags: Redux
Date: October 25, 2023
Status: Done

**Task of the day**

- Redux: Strategies for complex State
- Intro to Redux Toolkit
- Implementing the Redux store from scratch

---

### Strategies for complex state

Redux really shines when used in applications with many features and lot of data, where having a centralized store to keep it all organized is advantageous. It would give you the following features:

- Display a set of items that are pulled from a database
- Allows the user to add/remove their favorite items to/from a separate list
- Allows the user to enter a search term to filter the visible recipes

The Frontend engineer would implement both react and redux

- React
    - How to create components
    - How to render components using `ReactDOM.render()`
    - How to nest components and pass data through props
- Redux
    - One-way data flow model: State → View → Actions → State → View
    - How to create a reducer function: `(state, action) => nextState`
    - How to write action objects and action creators
    - How to create a `store`  methods `getState()`,`Dispatch()`, and `subscribe()`

---

### Slice

Redux is best suited for complex applications with many features that each have some state-related data to be managed. In these cases, objects are the go-to data type to represent the entire store’s state.

For example, consider a todo app that allows a user to:

- Add to a list of todos.
- Mark individual todos as complete or incomplete.
- Apply a filter to show only the completed todos, only the incomplete todos, or all of the todos.

---

### Actions and Payloads for Complex State

When an application state has multiple slices, individual actions typically only change one slice at a time. Therefore, it is recommended that each action’s `type` follows the pattern `'sliceName/actionDescriptor'`, to clarify which slice of state should be updated.

For example, in a todo application with a `state.todos`slice, the action type for adding a new todo might be `'todos/addTodo'`.

---

### Immutable Updates & Complex State

The [second rule of reducers](https://redux.js.org/tutorials/fundamentals/part-3-state-actions-reducers#rules-of-reducers) states that when the reducer is updating the `state`, it must make a copy and return the copy rather than directly mutating the incoming `state`. When the state is a mutable data type, like an array or object, this is typically done using the spread operator (`...`).

- The `todosReducer` uses the `initialState` as the default `state` value.
- When a `'filter/setFilter'`action is received, it spreads the old `state`‘s contents (`...state`) into a new object before updating the `filter`property with the new filter from `action.payload`.
- When a `'todos/addTodo'`action is received, it does the same except this time, since `state.todos` is a mutable array, its contents are also spread into a new array, with the new todo from `action.payload` added to the end.
- When a `'todos/toggleTodo`action is received, it uses the `.map()` method to create a copy of the `state.todos`array. Additionally, the todo being toggled is found using `action.payload.id`, and it is spread into a new object and updated.

---

### Reducer composition

As an application state becomes increasingly  more complex, managing it all with a single reducer will become impractical.

This solution is to follow a pattern called reducer composition. In this pattern, individual slice reducers are responsible for updating only one slice of the application’s state, and their results are recombined by `rootReducer` to form a single state object.

```jsx
// Handles only `state.todos`.
const initialTodos = [
  { id: 0, text: 'learn redux', completed: false },
  { id: 1, text: 'build a redux app', completed: true },
  { id: 2, text: 'do a dance', completed: false },
];
const todosReducer = (todos = initialTodos, action) => {
  switch (action.type) {
    case 'todos/addTodo': 
      return [...todos, action.payload]
    case 'todos/toggleTodo':
      return todos.map(todo => {
        return (todo.id === action.payload.id) ? 
          { ...todo, completed: !todo.completed } : 
          {...todo};
      });
    default:
      return todos;
  }
};

// Handles only `state.filter`
const initialFilter = 'SHOW_INCOMPLETE',
const filterReducer = (filter = initialFilter, action) => {
  switch (action.type) {
    case 'filter/setFilter':
      return action.payload;
    default:
      return filter;
};

const rootReducer = (state = {}, action) => {
  const nextState = {
    todos: todosReducer(state.todos, action),
    filter: filterReducer(state.filter, action)
  };
  return nextState;
};

const store = createStore(rootReducer);
```

---

### combineReducers

In the reducer composition pattern, the same steps are taken by the `rootReducer` for each slice reducer:

1. Call the slice reducer with its slice of the `state` and the `action` as arguments.
2. Store the returned slice of state in a new object that is ultimately returned by the `rootReducer()`.

```jsx
import { createStore } from 'redux';

// todosReducer and filterReducer omitted

const rootReducer = (state = {}, action) => {
  const nextState = {
    todos: todosReducer(state.todos, action),
    filter: filterReducer(state.filter, action)
  };
  return nextState;
};

const store = createStore(rootReducer);
```

The Redux package helps facilitate this pattern by providing a utility function called `combineReducers()`, which handles this boilerplate for us:

```jsx
import { createStore, combineReducers } from 'redux'

// todosReducer and filterReducer omitted.

const reducers = {
    todos: todosReducer,
    filter: filterReducer
};
const rootReducer = combineReducers(reducers);
const store = createStore(rootReducer);
```

---

### A file structure for redux

Redux Ducks pattern

```markdown
src/
|-- index.js
|-- app/
    |-- store.js
|-- features/
    |-- featureA/
        |-- featureASlice.js
    |-- featureB/
        |-- featureBSlice.js
```

---

### Review

- The `action.payload`property is used to hold additional data that the reducer might need to carry out a given action. The name `payload` is simply a convention, and its value can be anything!
- The spread syntax (`...`) and array methods such as `.map()`, `.slice()`, and `.filter()` can be used to immutably update the state of a complex app.
- *Reducer composition* is a design pattern for managing a Redux store with multiple slices.
- The *root reducer* delegates actions to *slice reducers* that are responsible for updating only their assigned slice of the store’s state. The root reducer then reassembles the slices into a new state object.
- `combineReducers()` is a method provided by the `redux` library that accepts a collection of reducer functions and returns a `rootReducer` that implements the reducer composition pattern.
- In a Redux application, slice reducers are often written in separate files. This pattern is known as [Redux Ducks](https://github.com/erikras/ducks-modular-redux).

---

### Intro to Redux Toolkit

Common issues and grievances that people encounter when working with Redux include:

- “Setting up a Redux store is overly complex.”
- “I have to add a lot of packages to get Redux to do anything useful.”
- “Redux requires too much boilerplate code.”
- “Writing immutable updates is too error-prone.”

Redux Toolkit contains packages and functions tailored for constructing a Redux application. It incorporates best practices, simplifies most Redux tasks, prevents common mistakes, and makes it easier to write Redux applications.

Because of how effective it has proven to be at addressing the concerns of the verbose “hand-written” logic of the past, Redux Toolkit has become the preferred way to write Redux application logic.

---

### “Slice” of State

Before we dive deeper into this lesson, let’s refresh our memory about what we’re referring to when talking about a “slice” of state. A “slice” of state is a segment of the global state that focuses on a particular feature. It encompasses the related data, along with its associated reducers, actions, and selectors. Think of it as a self-contained unit dedicated to managing a specific part of your application’s functionality.

In the following example, `state.todos` and `state.visibilityFilter`represent distinct slices.

```jsx
const state = {
  todos: [
    {
      id: 0,
      text: "Learn Redux-React",
      completed: true,
    },
    {
      id: 1,
      text: "Learn Redux Toolkit",
      completed: false,
    }
  ], 
  visibilityFilter: "SHOW_ALL"
}
```

For each slice of the state, we usually define a corresponding reducer. These are known as “slice reducers.” Each reducer is akin to a worker solely responsible for managing the state of its respective slice. This modular approach simplifies complex applications and makes debugging a breeze.

Let’s explore the slice reducer for the `state.todos` slice:
``

```jsx
/* todosSlice.js  */
const addTodo = (todo) => {
  return {
    type: 'todos/addTodo',
    payload: todo
  }
}

const toggleTodo = (todo) => {
  return {
    type: 'todos/toggleTodo',
    payload: todo
  }
}

const todos = (state = [], action) => {
 switch (action.type) {
   case 'todos/addTodo':
     return [
       ...state,
       {
         id: action.payload.id,
         text: action.payload.text,
         completed: false
       }
     ]
   case 'todos/toggleTodo':
     return state.map(todo =>
       todo.id === action.payload.id ? { ...todo, completed: !todo.completed } : todo
     )
   default:
     return state
 }
}
```

Notice that this file exclusively handles the `state.todos` data and doesn’t interact with the `state.visibilityFilter` slice. Managing state one slice at a time enables us to more effectively handle the distinct logic of each individual part of our application.

---

### Refactoring with createSlice()

`createSlice` has one parameter, a configuration object. The object has the following properties:

- `name`: A string that identifies the name of the slice. `createSlice()` uses this to generate the action types and action creators.
- `initialState`: The initial state value for the reducer.
- `reducers`: An object where each key represents an action `type`, a string identifier for the action. The associated method, known as a “case reducer,” describes how the state should be updated when that action is triggered. These reducers function as sets of instructions, directing the state changes based on the type of action dispatched.

---

### Writing “Mutable” Code with Immer

Immer uses a special JS object called a Proxy to wrap the data you provide and lets you write code that “mutates” that wrapped data. Immer does this by tracking all the changes you’ve made and then uses that list of changes to return an immutably updated value as if you’d written all the immutable update logic by hand.

Immer is used internally automatically, so there is nothing for you to do on your part to make sure it updates immutably! You can write code that looks like this:

```jsx
const todosSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => {
      state.push({ 
        ...action.payload, 
        completed: false 
      })
    },
    toggleTodo: (state, action) => {
      const todo = state.find(todo => todo.id === action.payload.id)
      if (todo) {
        todo.completed = !todo.completed
      }
    }
  }
})
```

`addTodo` is calling `state.push()`here, which is normally bad because the `array.push()`function mutates the existing array. Similarly, `toggleTodo` is simply finding the matching todo object, and then mutating it by reassigning its value.

You don’t need to learn the Immer library. All you do need to know is that `createSlice()`takes advantage of it, allowing us to safely “mutate” our state. You may find it useful to look through some of the common [update patterns used with Immer](https://immerjs.github.io/immer/docs/update-patterns).

---

### Returned objects and Auto-Generated actions

So far, we’ve covered the object passed to `createSlice()`. Now, let’s dive into what this function actually returns.

Take the `todosSlice` example we’ve been working with. When you apply `createSlice()`, it gives you back an object like this:

```jsx
const todosSlice = createSlice({
 name: 'todos',
 initialState: [],
 reducers: {
   addTodo(state, action) {
     const { id, text } = action.payload
     state.push({ id, text, completed: false })
   },
   toggleTodo(state, action) {
     const todo = state.find(todo => todo.id === action.payload)
     if (todo) {
       todo.completed = !todo.completed
     }
   }
 }
})

/* Object returned by todosSlice */
{
 name: 'todos',
 reducer: (state, action) => newState,
 actions: {
   addTodo: (payload) => ({type: 'todos/addTodo', payload}),
   toggleTodo: (payload) => ({type: 'todos/toggleTodo', payload})
 },
 // case reducers field omitted
}
```

Let’s break this down:

- `name`: This holds a string used as the prefix for generated action types.
- `reducer`: This is the completed reducer function.
- `actions`: These are auto-generated action creators.

So, what do these auto-generated action objects look like?

By default, each action creator accepts one argument, which becomes the `action.payload`. The `action.type` string is formed by combining the slice’s `name` with the case reducer function’s name.

With these auto-generated action creators, we can export them and use them in other files. Theoretically, you could export the entire slice object returned by `createSlice()`. But, following the Redux community’s [“ducks” pattern](https://redux.js.org/style-guide/style-guide#structure-files-as-feature-folders-or-ducks) pattern, we suggest exporting named action creators separately from the reducer:

---

### Returned Objects and Reducers

Let’s now take a closer look at the `reducer` within the object returned by `createSlice()`. 
``

```jsx
const options = {
  // options fields omitted.
}
const todosSlice = createSlice(options);

/* Object returned by todosSlice */
{
 name: 'todos',
 reducer: (state, action) => newState,
 actions: {
   addTodo: (payload) => ({type: 'todos/addTodo', payload}),
   toggleTodo: (payload) => ({type: 'todos/toggleTodo', payload})
 },
 // case reducers field omitted
}
```

`todosSlice.reducer` is the comprehensive reducer function that represents the collection of case reducers, each associated with different actions your slice is meant to handle. Effectively, it combines the case reducers into one. This is commonly referred to as the “slice reducer.”

When an action with the type `'todos/addTodo'` is dispatched, `todosSlice` employs `todosSlice.reducer()` to check whether the dispatched action’s type aligns with any of the case reducers in `todos.actions`. If a match is found, the matching case reducer function is executed; if not, the current state is returned. This mirrors the pattern we earlier employed with `switch`/`case` statements!

Once auto-generated, `todosSlice.reducer` needs to be exported so that it can be integrated into the global store and used as the `todos` slice of state. Per the  [“ducks” pattern](https://redux.js.org/style-guide/style-guide#structure-files-as-feature-folders-or-ducks), we default export `todosSlice.reducer`.

---

### Converting the Store to use ‘configureStore()’

In addition to simplifying the logic for actions and reducers, Redux Toolkit has a `configureStore()` method that simplifies the store setup process. `configureStore()`wraps around the Redux library’s `createStore()` method and the `combineReducers()` method, and handles most of the store set up for us automatically.

For example, take a look at this file, which creates and exports a `rootReducer:`

```jsx
// rootReducer.js

import { combineReducers } from 'redux'

import todosReducer from './features/todos/todosSlice'
import filtersReducer from './features/filters/filtersSlice'

const rootReducer = combineReducers({
 // Define a top-level state field named `todos`, handled by `todosReducer`
 todos: todosReducer,
 visibilityFilter: visibilityFilterReducer
})

export default rootReducer
```

and this file, which creates and exports the store:

```jsx
// store.js
        
import { createStore } from 'redux'
import { composeWithDevTools } from 'redux-devtools-extension'
import rootReducer from './reducer'
import { fetchTodos } from './actions'; 

const store = createStore(rootReducer, composeWithDevTools())
store.dispatch(fetchTodos());
export default store
```

`configureStore()` accepts a single configuration object parameter. The input object should have a `reducer` property that defines either a function to be used as the root reducer, or an object of slice reducers, which will be combined to create a root reducer.

[There are many properties available in this object](https://redux-toolkit.js.org/api/configureStore), but for the purposes of this lesson, just the `reducer` property will be sufficient.

```jsx
import { configureStore } from '@reduxjs/toolkit'

import todosReducer from './features/todos/todosSlice'
import filtersReducer from './features/filters/filtersSlice'

const store = configureStore({
 reducer: {
   // Define a top-level state field named `todos`, handled by `todosReducer`
   todos: todosReducer,
   filters: filtersReducer
 }
})

export default store
```

Note all the work that this one call to `configureStore()` does for us:

- Reducer: It combines `todosReducer` and `filtersReducer` into the root reducer function, which will handle a root state that looks like `{todos, filters}`, removing the need to call `combineReducers()`. This lowers the amount of boilerplate code we need to write.
- Store: It creates a Redux store using that root reducer, removing the need to call `createStore()`
- Middleware: It automatically adds middleware to check for common mistakes like accidentally mutating the state. In the traditional manual way, we’d need to set this up ourselves.
- DevTools: It automatically sets up the Redux DevTools Extension connection. In the traditional manual way, we’d also need to set this up ourselves.

Because of how much boilerplate code we’re able to bypass with `configureStore()`, we can just import the individual slice reducers straight into this file instead of creating a separate file for the root reducer and having to export/import it.

---

### Review

- Redux Toolkit (RTK) contains packages and functions that build in suggested best practices, simplify most Redux tasks, prevent common mistakes, and make it easier to write Redux applications.
- RTK has `createSlices()` function that will help us simplify our Redux reducer logic and actions.
- `CreateSlice()`has one parameter, a configuration object, which we call options. In this lesson, we covered three object `name`, `initialState`, and `reducers`. The configuration object has more properties which will be covered in the following lessons.
- A case reducer is a method that can update the state and will be executed when the corresponding action type is dispatched. This is similar to a case in a switch statement.
- You can write code that “mutates” the state inside the case reducers passed to `createSlice()`, and Immer will safely and accurately return an immutably updated state.
- `createSlice()` returns an object with the following properties: `name`, `reducer`, `actions`, and `caseReducers`.
- We typically use a Redux community code convention called the “ducks” pattern when exporting the action creators and the reducer.
- RTK has a `configureStore()`function that simplifies the store setup process. `configureStore()` wraps around the Redux core `createStore()` function and the `combineReducers()`function, and handles most of the store setup for us automatically.

---

### Implementing the redux store from scratch

### **Who is this article for?**

Though the **`redux`** package provides the **`createStore()`** method for us, examining how this powerful object can be created using vanilla [JavaScript](https://www.codecademy.com/resources/docs/javascript) will help illuminate how Redux works under the hood. This article is for learners who want to solidify their understanding of the Redux store.

It is assumed that you have some familiarity with the following Redux-related terms and concepts:

- The one-way data-flow model (state → view → actions → state)
- Reducer functions
- Action objects
- The **`createStore()`** function (by the **`redux`** package)
- The **`store`** object and [its three main methods](https://redux.js.org/api/store)

Visit [our course on Redux](https://www.codecademy.com/learn/learn-redux) to learn about or refresh yourself with these terms and concepts.

### **Part 1: What is the Redux store and how is it used?**

[Redux](https://redux.js.org/) is a state-management library centered around a single, powerful object called the **`store`**. This one object is responsible for holding the entire application’s state, receiving *action objects* and then executing state changes based on the type of the action received, and informing (executing) *listener functions* when such changes occur.

To help create this **`store`** object, the Redux library provides the **`createStore()`** function. This function accepts a reducer function as an argument and returns a **`store`** object with three essential methods:

- **`store.getState()`**: for retrieving the current state value held by the **`store`**
- **`store.dispatch(action)`**: for triggering changes to the state, given an action object
- **`store.subscribe(listener)`**: for registering listener functions to be called when state changes occur

All of this can be seen in the example below which implements a simple counting application:

```jsx
import { createStore } from 'redux';

const countReducer = (state = 0, action) => {
  switch (action.type) {
    case 'increment':
      return state + 1;
    case 'decrement':
      return state - 1;
    default:
      return state;
  }
}
const store = createStore(countReducer);

const render = () => {
  document.getElementById('count').text = store.getState(); // Display the current state.
}
render(); // Render once with the initial state of 0.

store.subscribe(render); // Re-render on state changes.

document.getElementById('plusButton').addEventListener('click', () => {
  store.dispatch({ type: 'increment' }); // Request a state change.
});

```

With this working knowledge of how to use the **`createStore()`** function and the **`store`** methods, we can begin to write the outline of this function:

```
const createStore = (reducer) => {
  const getState = () => {};
  const dispatch = () => {};
  const subscribe = () => {};
  return { getState, dispatch, subscribe };
}

```

Above, we define **`createStore()`** simply as a function with a **`reducer`**argument that returns an object containing three methods: **`getState()`**, **`dispatch()`**, and **`subscribe()`**.

### **Part 2: Holding the current state of the application**

Let’s now turn our attention to the primary responsibility of the **`store`**: to hold the current state of the application and to provide access to this value via the **`store.getState()`** method. Implementing this behavior is as simple as storing an encapsulated variable (we can call it **`state`**) within the function and returning it with **`store.getState()`**:

```jsx
const createStore = (reducer) => {
  let state;
  const getState = () => state;
  const dispatch = () => {};
  const subscribe = () => {};
  return { getState, dispatch, subscribe };
}
```

Hiding the **`state`** behind the [API](https://www.codecademy.com/resources/docs/general/api) of the **`store`** avoids common dangers associated with having global variables:

- Polluting the global namespace increases the chances of naming collisions.
- Granting variable access to parts of an application while limiting it to others is impossible.
- Debugging is difficult when a variable is referenced in many parts of the application.

Redux solves these problems by requiring the programmer to use only the **`store`** methods to access the state.

### **Part 3: Managing listener functions**

The state of the **`store`** will likely change many times and the features of the application must be notified when those changes occur. The **`store.subscribe()`** method allows you to subscribe callback functions, called *listeners*, to be executed when the state data changes. As in the first example, functions that render the view-layer are often subscribed to the **`store`** and use **`store.getState()`** to get the most up-to-date state data.

Any number of listeners may be subscribed to the **`store`** at once so an array is maintained by the **`store`** and the **`subscribe()`** method adds provided listeners to that array.

```jsx
const createStore = (reducer) => {
  let state;
  let listeners = [];

  const getState = () => state;

  const dispatch = () => {};

  const subscribe = (listener) => {
    listeners.push(listener);
    return () => {
      listeners = listeners.filter(l => l !== listener)
    }
  };

  return { getState, dispatch, subscribe };
}
```

Also notice that the **`subscribe()`** method returns a function. If you no longer want the given listener to be executed in response to state changes, this function can be saved and called to *unsubscribe* the given listener. For example:

```
const unsubscribe = store.subscribe(render); // Subscribes `render` to the store.

// somewhere else in the program...
unsubscribe(); // Unsubscribes `render` from the store.

```

### **Part 4: Handling incoming actions**

Redux ensures that the state is maintained reliably by requiring the programmer to dispatch actions to the store if they wish to update the state. The **`store.dispatch()`** function accepts an **`action`** object as an argument and calculates the next **`state`** value by calling the **`reducer()`** with the current **`state`** and the **`action`**:

```jsx
const createStore = (reducer) => {
  let state;
  let listeners = [];

  const getState = () => state;

  const dispatch = (action) => {
    state = reducer(state, action);
    listeners.forEach(listener => listener());
  };

  const subscribe = (listener) => {
    listeners.push(listener);
    return () => {
      listeners = listeners.filter(l => l !== listener)
    }
  };

  dispatch({});
  return { getState, dispatch, subscribe };
}
```

Each listener that has been subscribed to the **`store`** (stored in the **`listeners`**array) is then executed. Notice that the state is not passed directly to these listeners. It is up to each listener to use **`store.getState()`** to get the most up-to-date data.

Finally, notice that before the **`store`** object is returned, the function call **`dispatch({})`** is made. This initializes the **`state`** value with the default initial state value of the **`reducer`**.

Apart from a few details and edge cases, this is the full implementation of the **`createStore()`** method provided by the **`redux`** package. As you can see, the technology behind the Redux **`store`** is not particularly complicated, though the pattern it enforces is incredibly powerful.