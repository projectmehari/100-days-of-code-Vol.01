# Day 42

Tags: React
Date: August 20, 2023
Status: Done

Task of the day

- React hooks

---

**THE STATE HOOK**

### **Why Use Hooks?**

What should we do if we want to add a state to our function component? How about if we wanted our app to respond to the changes in data?

In this lesson, we’ll learn about *React Hooks* and how they can help us powerfully wield function components.

React Hooks, plainly put, are functions that let us manage the internal state of components and handle post-rendering side effects directly from our function components. Using Hooks, we can determine what we want to show the users by declaring how our user interface should look based on the state.

React offers a number of built-in Hooks. A few of these include `useState()`, `useEffect()`, `useContext()`, `useReducer()`, and `useRef()`. See [the full list](https://react.dev/reference/react) in the React docs.

---

**THE STATE HOOK**

### **Review**

We can now build stateful function components using the `useState` React Hook!

Let’s review what we learned and practiced in this lesson:

- With React, we feed static and dynamic data models to JSX to render a view to the screen.
- Hooks are used to “hook into” the internal component state for managing dynamic data in function components.
- We employ the State Hook using the code below. The `currentState` references the current value of the state and `initialState` initializes the value of the state for the component’s first render.

```jsx
const [currentState, stateSetter] = useState( initialState );

```

- State setters can be called in event handlers.
- We can define simple event handlers inline in our JSX and complex event handlers outside of our JSX.
- We use a state setter callback function when our next value depends on our previous value.
- We use arrays and objects to organize and manage related data that tend to change together.
- Use the spread syntax on collections of dynamic data to copy the previous state into the next state like so: `setArrayState((prev) => [ ...prev ])` and `setObjectState((prev) => ({ ...prev }))`.
- It’s best practice to have multiple, simpler states instead of having one complex state object.

---

**THE EFFECT HOOK**

### **Why Use useEffect?**

Before Hooks, function components were only used to accept data in the form of props and return some JSX to be rendered. However, as we learned in the last lesson, the State Hook allows us to manage dynamic data, in the form of component state, within our function components.

In this lesson, we’ll use the **Effect Hook** to run some JavaScript code after each render to:

- fetch data from a back-end service.
- subscribe to a stream of data.
- manage timers and intervals.
- read from and make changes to the DOM.

Components will re-render multiple times throughout their lifetime. These key moments present the perfect opportunity to execute these “side effects”.

There are three key moments when the Effect Hook can be utilized:

1. When the component is first added, or *mounted*, to the DOM and renders.
2. When the state or props change, causing the component to re-render.
3. When the component is removed, or *unmounted*, from the DOM.

Later on in this lesson, we’ll learn how to further fine-tune exactly when the Effect Hook executes.

---

**THE EFFECT HOOK**

### **Review**

In this lesson, we learned how to write effects that manage timers, manipulate the DOM, and fetch data from a server. With the Effect Hook, we can perform these types of actions in function components with ease!

Let’s review the main concepts from this lesson:

- We can import the `useEffect()` function from the `'react'`library and call it in our function components.
- *Effect* refers to a function that we pass as the first argument of the `useEffect()` function. By default, the Effect Hook calls this effect after each render.
- The *cleanup function* is optionally returned by the effect. If the effect does anything that needs to be cleaned up to prevent memory leaks, then the effect returns a cleanup function, then the Effect Hook will call this cleanup function before calling the effect again as well as when the component is being unmounted.
- The *dependency array* is the optional second argument that the `useEffect()` function can be called with in order to prevent repeatedly calling the effect when this is not needed. This array should consist of all variables that the effect depends on.

The Effect Hook is all about scheduling when our effect’s code gets executed. We can use the dependency array to configure when our effect is called in the following ways:

| Dependency Array | Effect called after first render & … |
| --- | --- |
| undefined | every re-render |
| Empty array | no re-renders |
| Non-empty array | when any value in the dependency array changes |

Hooks gives us the flexibility to organize our code in different ways, grouping related data as well as separating concerns to keep code simple, error-free, reusable, and testable!

---

**REACT PROGRAMMING PATTERNS**

### **Review**

Congrats! You’ve learned your first programming pattern to help organize your React code. You divided a complex React component into a container component and a couple of presentational components.

Here are the steps we took:

- Identified that the original component needed to be refactored: it handled calculations/logic and presentation/rendering.
- Created a container component containing all the stateful logic.
- Created a function that calls the state setter method provided by `useState()`.
- Created and exported presentational components containing only JSX.
- Imported the presentational components into the container component.
- Used the presentational components in the return statement of the container component.
- Passed state and functions used to change state as props to the rendered presentational components.

In this programming pattern, the container component does the work of figuring out what to display using state. The presentational component does the work of actually displaying the state through props. If a component does a significant amount of work in both areas, then that’s a sign that you should use this pattern!