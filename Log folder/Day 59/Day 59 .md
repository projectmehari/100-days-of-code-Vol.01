# Day 59

Tags: React
Date: September 10, 2023
Status: Done

Task of the day

- JSX
    - • **[Writing markup with JSX](https://react.dev/learn/writing-markup-with-jsx)**
    - • **[JSX in React – Explained with Examples](https://www.freecodecamp.org/news/jsx-in-react-introduction/)**
    - • **[JSX in React on w3school](https://www.w3schools.com/react/react_jsx.asp)**
- Props vs State
    - • **[State: A Component’s Memory](https://react.dev/learn/state-a-components-memory)**
    - • **[How to use Props in React](https://www.robinwieruch.de/react-pass-props-to-component/)**
    - • **[What is the difference between state and props in React?](https://stackoverflow.com/questions/27991366/what-is-the-difference-between-state-and-props-in-react)**
- Conditional Rendering
    - • **[Conditional Rendering](https://react.dev/learn/conditional-rendering)**
    - • **[Different techniques for conditional rendering in React](https://www.robinwieruch.de/conditional-rendering-react/)**

---

### What is JSX

[https://www.youtube.com/watch?v=9GtB5G2xGTY](https://www.youtube.com/watch?v=9GtB5G2xGTY)

### ****Writing Markup with JSX****

*JSX* is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file. Although there are other ways to write components, most React developers prefer the conciseness of JSX, and most codebases use it

![Screen Shot 2023-09-10 at 3.02.50 PM.png](Day%2059%2016429b2f58864f4fa3856c6df9d9a13a/Screen_Shot_2023-09-10_at_3.02.50_PM.png)

![Screen Shot 2023-09-10 at 3.03.21 PM.png](Day%2059%2016429b2f58864f4fa3856c6df9d9a13a/Screen_Shot_2023-09-10_at_3.03.21_PM.png)

Each React component is a JavaScript function that may contain some markup that React renders into the browser. React components use a syntax extension called JSX to represent that markup. JSX looks a lot like HTML, but it is a bit stricter and can display dynamic information. The best way to understand this is to convert some HTML markup to JSX markup.

### Converting HTML to JSX

```jsx
<h1>Hedy Lamarr's Todos</h1>
<img 
  src="https://i.imgur.com/yXOvdOSs.jpg" 
  alt="Hedy Lamarr" 
  class="photo"
>
<ul>
    <li>Invent new traffic lights
    <li>Rehearse a movie scene
    <li>Improve the spectrum technology
</ul>
```

### The rules of JSX

1. **Return a single root element**

To return multiple elements from a component, **wrap them with a single parent tag.**

For example, you can use a `<div>`:

```jsx
<div>
  <h1>Hedy Lamarr's Todos</h1>
  <img 
    src="https://i.imgur.com/yXOvdOSs.jpg" 
    alt="Hedy Lamarr" 
    class="photo"
  >
  <ul>
    ...
  </ul>
</div>
```

This empty tag is called a *[Fragment.](https://react.dev/reference/react/Fragment)* Fragments let you group things without leaving any trace in the browser HTML tree.

1. **Close all the tags**

JSX requires tags to be explicitly closed: self-closing tags like `<img>` must become `<img />`, and wrapping tags like `<li>oranges` must be written as `<li>oranges</li>`.

```jsx
<>
  <img 
    src="https://i.imgur.com/yXOvdOSs.jpg" 
    alt="Hedy Lamarr" 
    class="photo"
   />
  <ul>
    <li>Invent new traffic lights</li>
    <li>Rehearse a movie scene</li>
    <li>Improve the spectrum technology</li>
  </ul>
</>
```

1. **CamelCase most of the things!**

JSX turns into JavaScript and attributes written in JSX become keys of JavaScript objects. In your own components, you will often want to read those attributes into variables. But JavaScript has limitations on variable names. For example, their names can’t contain dashes or be reserved words like `class`.

This is why, in React, many HTML and SVG attributes are written in camelCase. For example, instead of `stroke-width` you use `strokeWidth`. Since `class` is a reserved word, in React you write `className` instead, named after the [corresponding DOM property](https://developer.mozilla.org/en-US/docs/Web/API/Element/className):

### **Recap**

Now you know why JSX exists and how to use it in components:

- React components group rendering logic together with markup because they are related.
- JSX is similar to HTML, with a few differences. You can use a [converter](https://transform.tools/html-to-jsx) if you need to.
- Error messages will often point you in the right direction to fixing your markup.

---

### ****JSX in React – Explained with Examples****

**What is JSX?**

> JSX is a JavaScript Extension Syntax used in React to easily write HTML and JavaScript together.
> 

```jsx
const jsx = <h1>This is JSX</h1>
```

This is simple JSX code in React. But the browser does not understand this JSX because it's not valid JavaScript code. This is because we're assigning an HTML tag to a variable that is not a string but just HTML code.

So to convert it to browser understandable JavaScript code, we use a tool like [Babel](https://babeljs.io/) which is a JavaScript compiler/transpiler.

You can set up your own babel configuration using Webpack as I show in [this article](https://medium.com/javascript-in-plain-english/webpack-and-babel-setup-with-react-from-scratch-bef0fe2ae3e7?source=friends_link&sk=880a6b9a35fb638eef19e5e99276428e). Or you can use [create-react-app](https://github.com/facebook/create-react-app) which internally uses Babel for the JSX to JavaScript conversion.

**What is the React.createElement function**

Every JSX is converted to the `React.createElement` function call that the browser understands.

The `React.createElement` has the following syntax:

```jsx
React.createElement(type, [props], [...children])
```

Let’s look at the parameters of the createElement function

- **Type** can be an HTML tag like h1, div, or it can be a React component
- **Props** are the attributes you want the element to have
- **Children** contain other HTML tags or can be a component

The `React.createElement` call will also be converted to the object representation like this:

```jsx
{   
 type: 'h1',   
 props: {     
   children: 'This is JSX'   
 }
}
```

### **Conclusion**

In this article, we have seen how to use JSX in React. Here are some major takeaways:

- Every JSX tag is converted to `React.createElement` call and its object representation.
- JSX Expressions, which are written inside curly brackets, allow only things that evaluate to some value like string, number, array map method and so on.
- In React, we have to use `className` instead of `class` for adding classes to the HTML element
- All attribute names in React are written in camelCase.
- `undefined`, `null`, and `boolean` are not displayed on the UI when used inside JSX.

---

### ****State: A Component's Memory****

Components often need to change what’s on the screen as a result of an interaction. Typing into the form should update the input field, clicking “next” on an image carousel should change which image is displayed, clicking “buy” should put a product in the shopping cart. Components need to “remember” things: the current input value, the current image, the shopping cart. In React, this kind of component-specific memory is called *state*.

****Adding a state variable****

To add a state variable, import `useState` from React at the top of the file:

```jsx
import { useState } from 'react';
```

Then, replace this line:

```jsx
let index = 0;
```

with 

```jsx
 const [index, setIndex] = useState(0);
```

`index` is a state variable and `setIndex` is the setter function.

```jsx
function handleClick() {
  setIndex(index + 1);
}
```

Now clicking the “Next” button switches the current sculpture:

```jsx
import { useState } from 'react';
import { sculptureList } from './data.js';

export default function Gallery() {
  const [index, setIndex] = useState(0);

  function handleClick() {
    setIndex(index + 1);
  }

  let sculpture = sculptureList[index];
  return (
    <>
      <button onClick={handleClick}>
        Next
      </button>
      <h2>
        <i>{sculpture.name} </i> 
        by {sculpture.artist}
      </h2>
      <h3>  
        ({index + 1} of {sculptureList.length})
      </h3>
      <img 
        src={sculpture.url} 
        alt={sculpture.alt}
      />
      <p>
        {sculpture.description}
      </p>
    </>
  );
}
```

**Meet your first hook** 

In React, `useState`, as well as any other function starting with ”`use`”, is called a Hook.

*Hooks* are special functions that are only available while React is [rendering](https://react.dev/learn/render-and-commit#step-1-trigger-a-render) (which we’ll get into in more detail on the next page). They let you “hook into” different React features.

State is just one of those features, but you will meet the other Hooks later.

****Anatomy of `useState`**

When you call `[useState](https://react.dev/reference/react/useState)`, you are telling React that you want this component to remember something:

```jsx
const [index, setIndex] = useState(0);
```

In this case, you want React to remember `index`.

The only argument to `useState` is the **initial value** of your state variable. In this example, the `index`’s initial value is set to `0` with `useState(0)`.

Every time your component renders, `useState` gives you an array containing two values:

1. The **state variable** (`index`) with the value you stored.
2. The **state setter function** (`setIndex`) which can update the state variable and trigger React to render the component again.

Here’s how that happens in action:

```jsx
const [index, setIndex] = useState(0);
```

1. **Your component renders the first time.** Because you passed `0` to `useState` as the initial value for `index`, it will return `[0, setIndex]`. React remembers `0` is the latest state value.
2. **You update the state.** When a user clicks the button, it calls `setIndex(index + 1)`. `index` is `0`, so it’s `setIndex(1)`. This tells React to remember `index` is `1` now and triggers another render.
3. **Your component’s second render.** React still sees `useState(0)`, but because React *remembers* that you set `index` to `1`, it returns `[1, setIndex]` instead.
4. And so on!

### ****State is isolated and private****

State is local to a component instance on the screen. In other words, **if you render the same component twice, each copy will have completely isolated state!** Changing one of them will not affect the other.

State is local to a compenent instance on the screen. In other words, if you render the same component twice, each copy will have completely isolated state! Changing one of them will not affect the other.

In this example, the Gallery component from earlier is rendered twice with no changes to its logic. Try clicking the buttons inside each of the galleries. Notice that their state is independent

### Recap

- Use a state variable when a component needs to “remember” some information between renders.
- State variables are declared by calling the `useState` Hook.
- Hooks are special functions that start with `use`. They let you “hook into” React features like state.
- Hooks might remind you of imports: they need to be called unconditionally. Calling Hooks, including `useState`, is only valid at the top level of a component or another Hook.
- The `useState` Hook returns a pair of values: the current state and the function to update it.
- You can have more than one state variable. Internally, React matches them up by their order.
- State is private to the component. If you render it in two places, each copy gets its own state.

---

### **How to use Props in React**

- [React Component Props by Example](https://www.robinwieruch.de/react-pass-props-to-component/#react-component-props-by-example)

``

```jsx
import * as React from 'react';

const App = () => {
  const greeting = 'Welcome to React';

  return (
    <div>
      <Welcome text={greeting} />
    </div>
  );
};

const Welcome = (props) => {
  return <h1>{props.text}</h1>;
};

export default App;
```

- [React Props vs. State](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-vs-state)

``

```jsx
import * as React from 'react';

const App = () => {
  const greeting = 'Welcome to React';

  const [isShow, setShow] = React.useState(true);

  const handleToggle = () => {
    setShow(!isShow);
  };

  return (
    <div>
      <button onClick={handleToggle} type="button">
        Toggle
      </button>

      {isShow ? <Welcome text={greeting} /> : null}
    </div>
  );
};

const Welcome = ({ text }) => {
  return <h1>{text}</h1>;
};

export default App;
```

```jsx
import * as React from 'react';

const App = () => {
  const [greeting, setGreeting] = React.useState('Welcome to React');

  const handleChange = (event) => {
    setGreeting(event.target.value);
  };

  return (
    <div>
      <Button label="Toggle" />

      <input type="text" value={greeting} onChange={handleChange} />

      {isShow ? <Welcome text={greeting} /> : null}
    </div>
  );
};

const Button = ({ label }) => {
  const [isShow, setShow] = React.useState(true);

  const handleToggle = () => {
    setShow(!isShow);
  };

  return (
    <button onClick={handleToggle} type="button">
      {label}
    </button>
  );
};

const Welcome = ({ text }) => {
  return <h1>{text}</h1>;
};

export default App;
```

- [React Props are just the Communication Channel](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-are-just-the-communication-channel)
- [React Props Destructuring](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-destructuring)

```jsx
import * as React from 'react';

const App = () => {
  return (
    <div>
      <Welcome text="Welcome to React" />
    </div>
  );
};

const Welcome = (props) => {
  return <h1>{props.text}</h1>;
};
```

- [React Spread Props](https://www.robinwieruch.de/react-pass-props-to-component/#react-spread-props)
- [React Rest Props](https://www.robinwieruch.de/react-pass-props-to-component/#react-rest-props)
- [React props with Default Value](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-with-default-value)
- [React's children prop](https://www.robinwieruch.de/react-pass-props-to-component/#reacts-children-prop)
- [How to pass Components as Props](https://www.robinwieruch.de/react-pass-props-to-component/#how-to-pass-components-as-props)
- [Children as a Function](https://www.robinwieruch.de/react-pass-props-to-component/#children-as-a-function)
- [React's Context API for Prop Drilling](https://www.robinwieruch.de/react-pass-props-to-component/#reacts-context-api-for-prop-drilling)
- [How to set Props to State](https://www.robinwieruch.de/react-pass-props-to-component/#how-to-set-props-to-state)
- [React Props Pitfalls](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-pitfalls)
    - [React props are not being passed in Components](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-are-not-being-passed-in-components)
    - [React props key is undefined](https://www.robinwieruch.de/react-pass-props-to-component/#react-props-key-is-undefined)
    - [Pass props to Styled Components](https://www.robinwieruch.de/react-pass-props-to-component/#pass-props-to-styled-components)

---

### ****Conditional Rendering****

Your components will often need to display different things depending on different conditions. In React, you can conditionally render JSX using JavaScript syntax like `if` statements, `&&`, and `? :` operators.

****Conditionally returning JSX****

Let’s say you have a `PackingList` component rendering several `Item`s, which can be marked as packed or not:

```jsx
function Item({ name, isPacked }) {
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

Notice that some of the `Item` components have their `isPacked` prop set to `true` instead of `false`. You want to add a checkmark (✔) to packed items if `isPacked={true}`.

You can write this as an `[if`/`else` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) like so:

```jsx
if (isPacked) {
  return <li className="item">{name} ✔</li>;
}
return <li className="item">{name}</li>;
```

If the `isPacked` prop is `true`, this code **returns a different JSX tree.** With this change, some of the items get a checkmark at the end:

```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return <li className="item">{name} ✔</li>;
  }
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

****Conditionally returning nothing with `null`**

In some situations, you won’t want to render anything at all. For example, say you don’t want to show packed items at all. A component must return something. In this case, you can return `null`:

```jsx
if (isPacked) {
  return null;
}
return <li className="item">{name}</li>;
```

If `isPacked` is true, the component will return nothing, `null`. Otherwise, it will return JSX to render.

```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return null;
  }
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item 
          isPacked={true} 
          name="Space suit" 
        />
        <Item 
          isPacked={true} 
          name="Helmet with a golden leaf" 
        />
        <Item 
          isPacked={false} 
          name="Photo of Tam" 
        />
      </ul>
    </section>
  );
}
```

In practice, returning `null` from a component isn’t common because it might surprise a developer trying to render it. More often, you would conditionally include or exclude the component in the parent component’s JSX. Here’s how to do that!

****Logical AND operator (`&&`)**

Another common shortcut you’ll encounter is the [JavaScript logical AND (`&&`) operator.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#:~:text=The%20logical%20AND%20(%20%26%26%20)%20operator,it%20returns%20a%20Boolean%20value.) Inside React components, it often comes up when you want to render some JSX when the condition is true, **or render nothing otherwise.** With `&&`, you could conditionally render the checkmark only if `isPacked` is `true`:

```jsx
return (
  <li className="item">
    {name} {isPacked && '✔'}
  </li>
);
```

A [JavaScript && expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND) returns the value of its right side (in our case, the checkmark) if the left side (our condition) is `true`. But if the condition is `false`, the whole expression becomes `false`. React considers `false` as a “hole” in the JSX tree, just like `null` or `undefined`, and doesn’t render anything in its place.

### **Recap**

- In React, you control branching logic with JavaScript.
- You can return a JSX expression conditionally with an `if` statement.
- You can conditionally save some JSX to a variable and then include it inside other JSX by using the curly braces.
- In JSX, `{cond ? <A /> : <B />}` means *“if `cond`, render `<A />`, otherwise `<B />`”*.
- In JSX, `{cond && <A />}` means *“if `cond`, render `<A />`, otherwise nothing”*.
- The shortcuts are common, but you don’t have to use them if you prefer plain `if`.

---

### **React Conditional Rendering**

Conditional rendering in React isn't difficult. In JSX - the syntax extension used for React - you can use plain JavaScript which includes if else statements, ternary operators, switch case statements, and much more. In a conditional render, a React component decides based on one or several conditions which DOM elements it will return. For instance, based on some logic it can either return a list of items or a text that says "Sorry, the list is empty". When a component has a conditional rendering, the appearance of the rendered component differs based on the condition. This article aims to be an exhaustive list of options for conditional renderings in React and best practices for these patterns.****

- [Conditional Rendering in React: if](https://www.robinwieruch.de/conditional-rendering-react/#conditional-rendering-in-react-if)
- [Conditional Rendering in React: if else](https://www.robinwieruch.de/conditional-rendering-react/#conditional-rendering-in-react-if-else)
- [Conditional Rendering in React: ternary](https://www.robinwieruch.de/conditional-rendering-react/#conditional-rendering-in-react-ternary)
- [Conditional Rendering in React: &&](https://www.robinwieruch.de/conditional-rendering-react/#conditional-rendering-in-react-)
- [Conditional Rendering in React: switch case](https://www.robinwieruch.de/conditional-rendering-react/#conditional-rendering-in-react-switch-case)
- [Multiple Conditional Renderings in React](https://www.robinwieruch.de/conditional-rendering-react/#multiple-conditional-renderings-in-react)
- [Nested Conditional Rendering in React](https://www.robinwieruch.de/conditional-rendering-react/#nested-conditional-rendering-in-react)
- [Conditional Rendering with HOC](https://www.robinwieruch.de/conditional-rendering-react/#conditional-rendering-with-hoc)
- [If Else Components in React](https://www.robinwieruch.de/conditional-rendering-react/#if-else-components-in-react)

---