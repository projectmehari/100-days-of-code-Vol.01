# Day 87

Tags: Redux
Date: October 24, 2023
Status: Done

Task of the day 

- Core concepts in Redux

---

### Redux

Redux is a state management library that follows a pattern known as the [Flux architecture](https://facebookarchive.github.io/flux/docs/in-depth-overview/). In Flux and Redux, shared information is consolidated within a single object instead of being scattered across individual components. Components receive data to render and can request changes using actions, which are events triggered by user interactions or other events. The state is available throughout the application, and updates are handled in a predictable manner, with components being notified whenever a change occurs.

### One-way Data flow

In most applications, there are three parts:

- State – the current data used in the app
- View – the user interface displayed to users
- Actions – events that a user can take to change the state

![Screen Shot 2023-10-24 at 7.13.20 PM.png](Day%2087%20e88e68cf3c1a409f89a292985d4fd602/Screen_Shot_2023-10-24_at_7.13.20_PM.png)

The flow of information would go like this:

- The state holds the current data used by the app’s components.
- The view components display that state data
- When a user interacts with the view, like clicking a button, the state will be updated in some way.
- The view is updated to display the new state.

### **State**

*State* in a web application represents the current information that drives the application’s behavior and appearance. It acts as a centralized source of data, storing the essential details of the application at any given moment.

With Redux, the state can be any JavaScript type, including number, string, boolean, array, and object.

Here’s an example state for a to-do app:

```jsx
const state = [ 'Print trail map', 'Pack snacks', 'Summit the mountain' ];

```

### Actions

A to-do list might have an input field where the user can type in a new to-do item. The application might transfer this data from the input field, add it to an array of all to-dos, and render them as text on the screen. This entire interaction can be defined as an **action**. Actions describe an event or an action that has occurred and provide information about what needs to be updated in the application’s state. In short, actions are how Redux manages and update the state.

In Redux, actions are represented as plain JS objects. Here’s what that action might look like:

```jsx
const action = {
  type: 'todos/addTodo',
  payload: 'Take selfies'
};

```

### Reducers

A **reducer**, or reducer function, is a plain JavaScript function that defines how the current state and an action are used in combination to create the new state.

Here’s an example of a reducer function for a todo app:

```jsx
const initialState = [ 'Print trail map', 'Pack snacks', 'Summit the mountain' ];

const todoReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'todos/addTodo': {
      return [ ...state, action.payload];
    }
    case 'todos/removeAll': {
      return [];
    }
    default: {
      return state;
    }
  }
}
```

There are a few things about this reducer that are true for all reducers:

- It’s a plain JavaScript function
- It defines the application’s next state given a current state and a specific action
- It returns a default initial state if no action is provided
- It returns the current state if the action is not recognized

### Rules of Reducers

In the previous exercise, we wrote reducers that returned a new copy of the state rather than editing it directly. We did this to adhere to the [rules of reducers provided by the Redux documentation](https://redux.js.org/tutorials/fundamentals/part-3-state-actions-reducers#rules-of-reducers):

1. They should only calculate the new state value based on the `state` and `action`arguments.
2. They are not allowed to modify the existing state. Instead, they must copy the existing state and make changes to the copied values.
3. They must not do any asynchronous logic or have other “side effects”.

By asynchronous logic or “side effects”, we mean anything that the function does aside from returning a value, e.g., logging to the console, saving a file, setting a timer, making an HTTP request, and generating random numbers.

By adhering to these rules, Redux promotes a clean separation of concerns, improves the maintainability of the codebase, and allows for efficient debugging and testing.

### Immutable Updates and Pure Functions

In programming, the three rules of reducers in Redux can be described more broadly. These rules state that reducers must perform **immutable** updates and be **pure functions**.

When a function makes immutable updates to its arguments, it doesn’t directly modify the original argument. Instead, it creates a copy and modifies that copy. This process is referred to as *immutable* updating because the function doesn’t alter or *mutate* the original arguments.

This function mutates its argument:

```jsx
const mutableUpdater = (obj) => {
  obj.completed = !obj.completed;
  return obj;
}

const task = { text: 'do dishes', completed: false };
const updatedTask = mutableUpdater(task);
console.log(updatedTask); 
// Prints { text: 'do dishes', completed: true };

console.log(task); 
// Prints { text: 'do dishes', completed: true };
```

Meanwhile, this function “immutably updates” its argument:

```jsx
const immutableUpdater = (obj) => {
  return {
    ...obj,
    completed: !obj.completed
  }
}

const task = { text: 'iron clothes', completed: false };
const updatedTask = immutableUpdater(task);
console.log(updatedTask); 
// Prints { text: 'iron clothes', completed: true };

console.log(task); 
// Prints { text: 'iron clothes', completed: false };
```

By copying the contents of the argument `obj` into a new object (`{...obj}`) and updating the `completed` property of the copy, the argument `obj` will remain unchanged.

Note that plain strings, numbers, and booleans are immutable in JavaScript, so we can just return them without making a copy:

```jsx
const immutator = (num) => num + 1;
const x = 5;
const updatedX = immutator(x);

console.log(x, updatedX); // Prints 5, 6
```

If a function is *pure*, then it will always have the same outputs given the same inputs.

This is a combination of rules 1 and 3:

- Reducers should only calculate the new state value based on the state and action arguments.
- Reducers must not do any asynchronous logic or other “side effects”.

In this example, the function is not a pure function because its returned value depends on the status of a remote endpoint.

```jsx
const addItemToList = (list) => {
  let item;
  fetch('https://anything.com/endpoint')
    .then(response => {
      if (!response.ok) {
        item = {};
      }
      
      item = response.json();
   });

   return [...list, item];  
};
```

The function can be made pure by pulling the `fetch()` statement outside of the function.
``

```jsx
let item;
  fetch('https://anything.com/endpoint')
    .then(response => {
      if (!response.ok) {
        item = {};
      }
      
      item = response.json();
   });

const addItemToList = (list, item) => {
    return [...list, item];
};
```

### Store

Redux uses a special object called the **store**. The store serves as a container for the state, and it is the center piece of your application and the single source of truth. The store is in charge of facilitating the dispatching of actions, and triggering the reducer when actions are dispatched. In most Redux applications, there is typically only one store.

Let’s rephrase the data flow using the new term:

1. The store initializes the state with a default value.
2. The view displays that state to the user.
3. When a user interacts with the view, such as clicking a button, an action is dispatched to the store.
4. The store’s reducer combines the dispatched action and the current state to determine the next state.
5. The view is updated to display the new state.

While we won’t be writing any code for the store during this lesson, it is essential that you understand the state, actions, reducers, and their role in the one-way data flow.

![Screen Shot 2023-10-24 at 7.45.50 PM.png](Day%2087%20e88e68cf3c1a409f89a292985d4fd602/Screen_Shot_2023-10-24_at_7.45.50_PM.png)

---

### Core Redux API

**What is the Redux API?**

Remember, Redux applications are built upon a one-way flow of data model and are managed by the *store*:

- The *state* is the set of data values that describes the application. It is used to render the user interface (UI).
- Users interact with the UI, which dispatches *actions* to the store. An action is an object that expresses a desired change to the state.
- The store generates its next state using a *reducer* function, which receives the most recent action and the current state as inputs.
- Finally, the UI is re-rendered based on the new state of the store, and the entire process can begin again.

Building an application that follows the core principles of Redux can be done without external libraries. However, the dedicated [Redux library](https://redux.js.org/) provides some very useful tools for handling the most common aspects of building a Redux application and helps ensure that the core Redux principles are enforced.

This lesson will focus on creating a basic Redux application with the `createStore()` method from the Redux API and the following related `store` methods:

- `store.getState()`
- `store.dispatch(action)`
- `store.subscribe(listener)`

### Create a Redux Store

Every Redux application uses a reducer function that describes which actions can update the state and how those actions lead to the next state.

For example, suppose you wanted to build an application for a light switch. Its reducer might look like this:

```jsx
const initialState = 'on';
const lightSwitchReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'toggle':
      return state === 'on' ? 'off' : 'on';
    default:
      return state;
  }
}
```

This reducer handles a single action type `'toggle'` and returns the next state of the store: `'on'` if it had been `'off'`and vice-versa. If an unrecognized action is received, the current state of the store is returned.

The programmer could manually execute the reducer with the current state of the store and the desired action to perform like so:

```jsx
let state = 'on';
state = lightSwitchReducer(state, { type: 'toggle' });
console.log(state); // Prints 'off'
```

However, this is the main responsibility of the `store`. The `store` is an object that enforces the one-way data flow model that Redux is built upon. It holds the current state inside, receives action dispatches, executes the reducer to get the next state, and provides access to the current state for the UI to re-render.

Redux exports a valuable helper function for creating this `store`object called `createStore()`. The `createStore()` helper function has a single argument, a reducer function.

To create a `store` with `lightSwitchReducer`, you could write:

```jsx

import { createStore } from 'redux'

const initialState = 'on';
const lightSwitchReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'toggle':
      return state === 'on' ? 'off' : 'on';
    default:
      return state;
  }
}

const store = createStore(lightSwitchReducer);
```

---

### Dispatch Actions to the Store

The `store` object returned by `createStore()` provides a number of useful methods for interacting with its state as well as the reducer function it was created with.

The most commonly used method, `store.dispatch()`, can be used to dispatch an action to the store, indicating that you wish to update the state. Its only argument is an action object, which must have a `type`property describing the desired state change.

```jsx
const action = { type: 'actionDescriptor' }; 
store.dispatch(action);
```

Each time `store.dispatch()` is called with an `action` object, the store’s reducer function will be executed with the same `action`object. Assuming that the `action.type` is recognized by the reducer, the state will be updated and returned.

Let’s see how this works in the light switch application from the last exercise:``

```jsx
import { createStore } from 'redux';

const initialState = 'on';
const lightSwitchReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'toggle':
      return state === 'on' ? 'off' : 'on';
    default:
      return state;
  }
}

const store = createStore(lightSwitchReducer);

console.log(store.getState()); // Prints 'on'

store.dispatch({ type: 'toggle' }); 
console.log(store.getState()); // Prints 'off'

store.dispatch({ type: 'toggle' });
console.log(store.getState()); // Prints 'on'
```

In this example, you can also see another `store` method, `store.getState()`, which returns the current value of the store’s state. Printing its value between each dispatched action allows us to see how the store’s state changes.

Internally, when the `store`executes its reducer, it uses `store.getState()` as the `state`argument. Though you won’t see it, you can imagine that when an action is dispatched like this…

```jsx
store.dispatch({ type: 'toggle'});
```

…the store calls the reducer like this:

```jsx
lightSwitchReducer(store.getState(), { type: 'toggle' });
```

---

### Action Creators

As you saw in the last exercise, you are likely to dispatch actions of the same type multiple times or from multiple places. Typing out the entire action object can be tedious and creates opportunities to make an error.

For example, in the light switch application, whose reducer accepts `'toggle'` actions to turn the light `'on'` or `'off'`, you might write:

```jsx
store.dispatch({Type:'toggle'});
store.dispatch({type:'toggel'});
store.dispatch({typo:'toggle'});
```

Did you spot the errors?

In most Redux applications, *action creators* are used to reduce this repetition and to provide consistency. An action creator is simply a function that returns an action object with a `type` property. They are typically called and passed directly to the `store.dispatch()` method, resulting in fewer errors and an easier-to-read dispatch statement.

The above code could be rewritten using an action creator called `toggle()` like so:

```jsx

const toggle = () => {
  return { type: "toggle" };
}
store.dispatch(toggle()); // Toggles the light to 'off'
store.dispatch(toggle()); // Toggles the light back to 'on'
store.dispatch(toggle()); // Toggles the light back to 'off'
```

Though not necessary in a Redux application, action creators save us the time needed to type out the entire action object, reduce the chances of making a typo, and improve the readability of our application.

Often, before the reducer of an application is even written, Redux programmers will write action creators as a way of planning out which actions will be available to dispatch to the store.

---

### Respond to State Changes

In a typical web application, user interactions that trigger [DOM events](https://developer.mozilla.org/en-US/docs/Web/Events) (`"click"`, `"keydown"`, etc…) can be listened for and responded to using an [event listener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener).

Similarly, in Redux, actions dispatched to the `store` can be listened for and responded to using the `store.subscribe()`method. This method accepts one argument: a function, often called a *listener*, that is executed in response to changes to the `store`‘s state.

```jsx
const reactToChange = () => console.log('change detected!');
store.subscribe(reactToChange);
```

In this example, each time an action is dispatched to the `store`, and a change to the state occurs, the subscribed listener, `reactToChange()`, will be executed.

Sometimes it is useful to stop the listener from responding to changes to the `store`, so `store.subscribe()` returns an `unsubscribe` function.

We can see this in action in the light switch application:

```jsx
// lightSwitchReducer(), toggle(), and store omitted...

const reactToChange = () => {
  console.log(`The light was switched ${store.getState()}!`);
}
const unsubscribe = store.subscribe(reactToChange);

store.dispatch(toggle());
// reactToChange() is called, printing:
// 'The light was switched off!'

store.dispatch(toggle());
// reactToChange() is called, printing:
// 'The light was switched on!'

unsubscribe(); 
// reactToChange() is now unsubscribed

store.dispatch(toggle());
// no print statement!

console.log(store.getState()); // Prints 'off'
```

- In this example, the listener function `reactToChange()` is subscribed to the `store`.
- Each time an action is dispatched, `reactToChange()` is called and prints the current value of the light switch. It is common for callbacks subscribed to the `store` to use `store.getState()` inside them.
- After the first two dispatched actions, `unsubscribe()` is called causing `reactToChange()` to no longer be executed in response to further dispatches made to `store`.

---

### Review

Congratulations! You were able to apply the core concepts of the Redux framework by implementing an application using the Redux library.

By completing this lesson, you are now able to:

- Import the `createStore()`helper function from the `'redux'` library.
- Create a `store` object that holds the entire state of your Redux application using `createStore()`.
- Get the current state of the `store` using `store.getState()`.
- Dispatch actions to the `store` using `store.dispatch(action)`.
- Create action creators to reduce the repetitive creation of action objects.
- Register a change listener function to respond to changes to the store using `store.subscribe(listener)`.
- Recognize the pattern for connecting Redux to any user interface.

Throughout this lesson, you may have thought that Redux adds a lot of unnecessary complexity to these simple applications. We implemented Redux in a very basic way, which is useful for learning but not how it’s done in the real world.

Redux shines when it is used in applications with many features and a lot of data, where having a centralized store to keep it all organized is advantageous. In the next lesson, you will learn how to build and organize Redux applications with complex state.