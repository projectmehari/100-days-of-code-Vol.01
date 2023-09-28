# Day 58

Tags: React
Date: September 10, 2023
Status: Done

Task of the day 

- CLI tools
    - [Create React App](https://create-react-app.dev)
        - [Official docs](https://react.dev/learn/start-a-new-react-project)
- Components
    - [https://react.dev/learn#components](https://react.dev/learn#components)
    - **[Explore the different types of components in React](https://www.robinwieruch.de/react-component-types/)**
    - **[What is the difference between components, elements, and instances?](https://www.robinwieruch.de/react-element-component/)**
- Functional Components
    - **[Your first component](https://react.dev/learn/your-first-component)**
    - **[Functional Components in React](https://www.robinwieruch.de/react-function-component/)**
    - **[Passing props to a component](https://react.dev/learn/passing-props-to-a-component)**

---

### Components

Creating and nesting components

React apps are made out of components. A component is a piece of the UI (user interface) that has its own logic and appearance. A component can be as small as a button, or as large as an entire page.

React components are JavaScript functions that return markup:

```jsx
function MyButton() {
  return (
    <button>I'm a button</button>
  );
}
```

Now that you’ve declared `MyButton`, you can nest it into another component:

```jsx
export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```

Notice that `<MyButton />` starts with a capital letter. That’s how you know it’s a React component. React component names must always start with a capital letter, while HTML tags must be lowercase.

Have a look at the result:

```jsx
function MyButton() {
  return (
    <button>
      I'm a button
    </button>
  );
}

export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```

The `export default` keywords specify the main component in the file. If you’re not familiar with some piece of JavaScript syntax, [MDN](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) and [javascript.info](https://javascript.info/import-export) have great references.

### Adding styles

In React, you specify a CSS class with `className`. It works the same way as the HTML `[class](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/class)` attribute:

```jsx
<img className="avatar" />
```

Then you write the CSS rules for it in a separate CSS file:

```jsx
/* In your CSS */
.avatar {
  border-radius: 50%;
}
```

React does not prescribe how you add CSS files. In the simplest case, you’ll add a `[<link>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link)` tag to your HTML. If you use a build tool or a framework, consult its documentation to learn how to add a CSS file to your project.

**Displaying data**

JSX lets you put markup into JavaScript. Curly braces let you “escape back” into JavaScript so that you can embed some variable from your code and display it to the user. 

```jsx
return (
  <h1>
    {user.name}
  </h1>
);
```

You can also “escape into JavaScript from JSC attributes, but you have to use curly braces instead of quotes. For example, `className="avatar"` passes the `"avatar"` string as the CSS class, but `src={user.imageUrl}` reads the JavaScript `user.imageUrl` variable value, and then passes that value as the `src` attribute:

```jsx
return (
  <img
    className="avatar"
    src={user.imageUrl}
  />
);
```

You can put more complex expressions inside the JSX curly braces too, for example, for example, [string concatenation](https://javascript.info/operators#string-concatenation-with-binary):

```jsx
const user = {
  name: 'Hedy Lamarr',
  imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
  imageSize: 90,
};

export default function Profile() {
  return (
    <>
      <h1>{user.name}</h1>
      <img
        className="avatar"
        src={user.imageUrl}
        alt={'Photo of ' + user.name}
        style={{
          width: user.imageSize,
          height: user.imageSize
        }}
      />
    </>
  );
}
```

in the above example, `style={{}}` is not a special syntax, but a regular `{}` object inside the `style={ }` JSX curly braces. You can use the `style` attribute when your styles depend on JavaScript variables.

**Conditional rendering** 

In React there is no special syntax for writing conditions. Instead, you’ll  use the same techniques as you use when writing regular JavaScript code. For example, you can use an if statement to conditionally include JSX:

```jsx
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```

If you prefer more compact code, you can use the conditional ? operator. Unlike if, it works inside JSX:

```jsx
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```

When you don’t need the else branch, you can also use a shorter logical && syntax:

```jsx
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```

All of these approaches also work for conditionally specifying attributes. If you’re familiar with some of this JavaScript syntax, you can start by always using if…else.

**Rendering lists**

You will rely JavaScript features like for loop and the array map()function to render lists of components. 

For example, let’s say you have an array of products.

```jsx
const products = [
  { title: 'Cabbage', id: 1 },
  { title: 'Garlic', id: 2 },
  { title: 'Apple', id: 3 },
];
```

Inside your component, use the `map()` function to transform an array of products into an array of `<li>` items:

```jsx
const listItems = products.map(product =>
  <li key={product.id}>
    {product.title}
  </li>
);

return (
  <ul>{listItems}</ul>
);
```

Notice how `<li>` has a `key` attribute. For each item in a list, you should pass a string or a number that uniquely identifies that item among its siblings. Usually, a key should be coming from your data, such as a database ID. React uses your keys to know what happened if you later insert, delete, or reorder the items.

```jsx
const products = [
  { title: 'Cabbage', isFruit: false, id: 1 },
  { title: 'Garlic', isFruit: false, id: 2 },
  { title: 'Apple', isFruit: true, id: 3 },
];

export default function ShoppingList() {
  const listItems = products.map(product =>
    <li
      key={product.id}
      style={{
        color: product.isFruit ? 'magenta' : 'darkgreen'
      }}
    >
      {product.title}
    </li>
  );

  return (
    <ul>{listItems}</ul>
  );
}
```

**Responding to events**

You can respond to events by declaring event handler functions inside your components: 

```jsx
function MyButton() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

Notice how `onClick={handleClick}` has no parentheses at the end! Do not *call* the event handler function: you only need to *pass it down*. React will call your event handler when the user clicks the button.

**Updating the screen**

Often, you’ll want your component to “remember” some information and display it. For example, maybe you want to count the number of times a button is clicked. To do this, add *state* to your component.

First, import `[useState](https://react.dev/reference/react/useState)` from React:

```jsx
import { useState } from 'react';
```

Now you can declare a *state variable* inside your component:

```jsx
function MyButton() {
  const [count, setCount] = useState(0);
  // ...
```

You’ll get two things from `useState`: the current state (`count`), and the function that lets you update it (`setCount`). You can give them any names, but the convention is to write `[something, setSomething]`.

The first time the button is displayed, `count` will be `0` because you passed `0` to `useState()`. When you want to change state, call `setCount()` and pass the new value to it. Clicking this button will increment the counter:

```jsx
function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```

React will call your component function again. This time, `count` will be `1`. Then it will be `2`. And so on.

If you render the same component multiple times, each will get its own state. Click each button separately:

```jsx
import { useState } from 'react';

export default function MyApp() {
  return (
    <div>
      <h1>Counters that update separately</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}

function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```

Notice how each button “remembers” its own `count` state and doesn’t affect other buttons.

**Using Hooks**

Functions starting with `use` are called *Hooks*. `useState` is a built-in Hook provided by React. You can find other built-in Hooks in the [API reference.](https://react.dev/reference/react) You can also write your own Hooks by combining the existing ones.

Hooks are more restrictive than other functions. You can only call Hooks *at the top* of your components (or other Hooks). If you want to use `useState` in a condition or a loop, extract a new component and put it there.

**Sharing data between components**

In the previous example, each `MyButton` had its own independent `count`, and when each button was clicked, only the `count` for the button clicked changed:

![Screen Shot 2023-09-09 at 4.20.55 PM.png](Day%2058%209799c0e4e15b4fe487ac409065d70845/Screen_Shot_2023-09-09_at_4.20.55_PM.png)

However, often you’ll need components to *share data and always update together*.

To make both `MyButton` components display the same `count` and update together, you need to move the state from the individual buttons “upwards” to the closest component containing all of them.

In this example, it is `MyApp`:

![Screen Shot 2023-09-09 at 4.21.14 PM.png](Day%2058%209799c0e4e15b4fe487ac409065d70845/Screen_Shot_2023-09-09_at_4.21.14_PM.png)

Now when you click either button, the `count` in `MyApp` will change, which will change both of the counts in `MyButton`. Here’s how you can express this in code.

First, *move the state up* from `MyButton` into `MyApp`:

```jsx
export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Counters that update separately</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}

function MyButton() {
  // ... we're moving code from here ...
}
```

Then, *pass the state down* from `MyApp` to each `MyButton`, together with the shared click handler. You can pass information to `MyButton` using the JSX curly braces, just like you previously did with built-in tags like `<img>`:

```jsx
export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Counters that update together</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}
```

The information you pass down like this is called *props*. Now the `MyApp` component contains the `count` state and the `handleClick` event handler, and *passes both of them down as props* to each of the buttons.

Finally, change `MyButton` to *read* the props you have passed from its parent component:

```jsx
function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Clicked {count} times
    </button>
  );
}
```

The information you pass down like this is called *props*. Now the `MyApp` component contains the `count` state and the `handleClick` event handler, and *passes both of them down as props* to each of the buttons.

Finally, change `MyButton` to *read* the props you have passed from its parent component:

```jsx
function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Clicked {count} times
    </button>
  );
}
```

When you click the button, the `onClick` handler fires. Each button’s `onClick` prop was set to the `handleClick` function inside `MyApp`, so the code inside of it runs. That code calls `setCount(count + 1)`, incrementing the `count` state variable. The new `count` value is passed as a prop to each button, so they all show the new value. This is called “lifting state up”. By moving state up, you’ve shared it between components.

```jsx
import { useState } from 'react';

export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Counters that update together</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}

function MyButton({ count, onClick }) {
  return (
    <button onClick={onClick}>
      Clicked {count} times
    </button>
  );
}
```

---

### Tutorial: Tic-Tac-Toe

You will build a small tic-tac-toe game during this tutorial. This tutorial does not assume any existing React knowledge. The techniques you’ll learn in the tutorial are fundamental to building any React app, and fully understanding it will give you a deep understanding of React.

**Finished code**

```jsx
import { useState } from 'react';

function Square({ value, onSquareClick }) {
  return (
    <button className="square" onClick={onSquareClick}>
      {value}
    </button>
  );
}

function Board({ xIsNext, squares, onPlay }) {
  function handleClick(i) {
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    const nextSquares = squares.slice();
    if (xIsNext) {
      nextSquares[i] = 'X';
    } else {
      nextSquares[i] = 'O';
    }
    onPlay(nextSquares);
  }

  const winner = calculateWinner(squares);
  let status;
  if (winner) {
    status = 'Winner: ' + winner;
  } else {
    status = 'Next player: ' + (xIsNext ? 'X' : 'O');
  }

  return (
    <>
      <div className="status">{status}</div>
      <div className="board-row">
        <Square value={squares[0]} onSquareClick={() => handleClick(0)} />
        <Square value={squares[1]} onSquareClick={() => handleClick(1)} />
        <Square value={squares[2]} onSquareClick={() => handleClick(2)} />
      </div>
      <div className="board-row">
        <Square value={squares[3]} onSquareClick={() => handleClick(3)} />
        <Square value={squares[4]} onSquareClick={() => handleClick(4)} />
        <Square value={squares[5]} onSquareClick={() => handleClick(5)} />
      </div>
      <div className="board-row">
        <Square value={squares[6]} onSquareClick={() => handleClick(6)} />
        <Square value={squares[7]} onSquareClick={() => handleClick(7)} />
        <Square value={squares[8]} onSquareClick={() => handleClick(8)} />
      </div>
    </>
  );
}

export default function Game() {
  const [history, setHistory] = useState([Array(9).fill(null)]);
  const [currentMove, setCurrentMove] = useState(0);
  const xIsNext = currentMove % 2 === 0;
  const currentSquares = history[currentMove];

  function handlePlay(nextSquares) {
    const nextHistory = [...history.slice(0, currentMove + 1), nextSquares];
    setHistory(nextHistory);
    setCurrentMove(nextHistory.length - 1);
  }

  function jumpTo(nextMove) {
    setCurrentMove(nextMove);
  }

  const moves = history.map((squares, move) => {
    let description;
    if (move > 0) {
      description = 'Go to move #' + move;
    } else {
      description = 'Go to game start';
    }
    return (
      <li key={move}>
        <button onClick={() => jumpTo(move)}>{description}</button>
      </li>
    );
  });

  return (
    <div className="game">
      <div className="game-board">
        <Board xIsNext={xIsNext} squares={currentSquares} onPlay={handlePlay} />
      </div>
      <div className="game-info">
        <ol>{moves}</ol>
      </div>
    </div>
  );
}

function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
```

---

## **Types of React Components**

### React CreateClass Components

Everything started out with **React's createClass Components**. The `createClass` method provided developers with a factory method to create React class components without using a JavaScript class. It was the status quo for creating React components prior JavaScript ES6, because in JavaScript ES5 there was no class syntax available:

```jsx
var App = React.createClass({
  getInitialState: function() {
    return {
      value: '',
    };
  },

  onChange: function(event) {
    this.setState({ value: event.target.value });
  },

  render: function() {
    return (
      <div>
        <h1>Hello React "createClass" Component!</h1>

        <input
          value={this.state.value}
          type="text"
          onChange={this.onChange}
        />

        <p>{this.state.value}</p>
      </div>
    );
  },
})
```

### React Mixins

A **React Mixin** got introduced as React's first advanced pattern for reusable component logic. With a Mixin, it's possible to extract logic from a React component as standalone object. When using a Mixin in a component, all features from the Mixin are introduced to the component:

```jsx
var localStorageMixin = {
  getInitialState: function() {
    return {
      value: localStorage.getItem('myValueInLocalStorage') || '',
    };
  },

  setLocalStorage: function(value) {
    localStorage.setItem('myValueInLocalStorage', value);
  },
};

var App = React.createClass({
  mixins: [localStorageMixin],

  componentDidUpdate: function() {
    this.setLocalStorage(this.state.value);
  },

  onChange: function(event) {
    this.setState({ value: event.target.value });
  },

  render: function() {
    return (
      <div>
        <h1>Hello React "createClass" Component with Mixin!</h1>

        <input
          value={this.state.value}
          type="text"
          onChange={this.onChange}
        />

        <p>{this.state.value}</p>
      </div>
    );
  },
});
```

### React Class Components

**React Class Components** were introduced with JavaScript ES6, because JS classes were made available to the language. Sometimes they are called **React ES6 class components** as well. Having [at least JavaScript ES6 at your disposal](https://www.robinwieruch.de/javascript-fundamentals-react-requirements/), you no longer had to use React's createClass method. Finally classes come with JS itself:

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      value: '',
    };

    this.onChange = this.onChange.bind(this);
  }

  onChange(event) {
    this.setState({ value: event.target.value });
  }

  render() {
    return (
      <div>
        <h1>Hello React ES6 Class Component!</h1>

        <input
          value={this.state.value}
          type="text"
          onChange={this.onChange}
        />

        <p>{this.state.value}</p>
      </div>
    );
  }
}
```

A React Component written with a JavaScript class comes with methods like the class constructor — which is primarily used in React to set initial state or to bind methods — and the mandatory render method to return JSX as output. All the internal React Component logic comes from the extends React.component via object-oriented inheritance that is used in the class component. However, it isn’t recommended to use the concept of inheritance for more than that. Instead, it's recommended to use [composition over inheritance](https://www.robinwieruch.de/react-component-composition/).

---

### React Higher-Order Components

React Higher-Order Components (HOCs), a popular advanced React pattern, are an alternative for React Mixins to deploy reusable logic across React components. If you haven't heard about HOCs, you can read more about them in detail in my other tutorial: [Higher-Order Components](https://www.robinwieruch.de/react-higher-order-components/). The shortest explanation for a Higher-Order Component is that it is a component which takes a component as input and returns the component as output but with extended functionalities. Let's revisit the example with the local storage and how the functionality can be extracted into a reusable Higher-Order Component:

Both, **React’s Higher-order Components** and **React’s Render Prop Components** are actively used in React applications, even though React Function Components with **React Hooks** — shown in the next section of this tutorial — may be the better abstraction layer for React components. However, HOCs and Render Props are used for Function Components as well.

---

### React Function Components

**React Function Components** are the equivalent of React Class Components but expressed as functions instead of classes. In the past, it wasn't possible to use state or side-effects in Function Components -- that's why they were called **Functional Stateless Components** -- but that's not the case anymore with [React Hooks](https://www.robinwieruch.de/react-hooks/) which rebranded them to Function Components.

React Hooks bring state and side-effects to React Function Components. React comes with a variety of built-in hooks, but also the ability to create custom hooks for yourself or others. 

All React Components share the common sense of how to use [React Props](https://www.robinwieruch.de/react-pass-props-to-component/), because they are just used to pass information down the component tree. However, the usage of state and side-effects varies for React Class Components and React Function Components with lifecycle methods and hooks.

This guide has shown you all the different Types of React Components, how they are used, and how they are put into a historical context. All examples from the tutorial can be seen and tried out over [here](https://github.com/the-road-to-learn-react/react-component-types). In the end it's perfectly fine to use React Class Components, Function Components with Hooks, advanced concepts like Higher-Order Components and React Render Prop Components. However, it's good to know for older React applications/tutorials that there were other React Components and Patterns used in the past as well.

---

### React Element vs Component

A **React component** is literally the declaration of a component as we see it in the previous code snippet. In our case, it's a [function component](https://www.robinwieruch.de/react-function-component/) but it could be any [other kind](https://www.robinwieruch.de/react-component-types/) of React component (e.g. React Class Component) too.

In the case of a function component, it is declared as a JavaScript function which returns React's JSX. While more complex JSX is a mixture of HTML and JavaScript, here we are dealing with a simple example which returns just one HTML element with an inner content.

Let's summarize React Elements and Components: While a React Component is the one time declaration of a component, it can be used once or multiple times as React Element in JSX. In JSX it can be used with angle brackets, however, under the hood React's `createElement` method kicks in to create React elements as JavaScript object for each HTML element.

```jsx
const Text = ({ children }) => {
  console.log('I am calling as an instance of Text');

  return <p>{children}</p>;
};

console.log('I am a component', Text);

const App = () => {
  console.log('I am calling as an instance of App');

  const paragraphOne = <p>You rock, React!</p>;
  const paragraphTwo = <Text>Bye!</Text>;

  console.log('I am an element:', paragraphOne);
  console.log('I am an element too:', paragraphTwo);

  return (
    <div>
      <p>Hello React</p>
      {paragraphOne}
      {paragraphTwo}
    </div>
  );
};

console.log('I am a component', App);
console.log('I am an element', <App />);
console.log('I am an element', <p>too</p>);
```

---

## Your first Component

Components: UI building blocks

```html
<article>
  <h1>My First Component</h1>
  <ol>
    <li>Components: UI Building Blocks</li>
    <li>Defining a Component</li>
    <li>Using a Component</li>
  </ol>
</article>
```

React lets you combine your markup, CSS, and JavaScript into custom “components”, **reusable UI elements for your app.** The table of contents code you saw above could be turned into a `<TableOfContents />` component you could render on every page. Under the hood, it still uses the same HTML tags like `<article>`, `<h1>`, etc.

Just like with HTML tags, you can compose, order and nest components to design whole pages. For example, the documentation page you’re reading is made out of React components:

```jsx
<PageLayout>
  <NavigationHeader>
    <SearchBar />
    <Link to="/docs">Docs</Link>
  </NavigationHeader>
  <Sidebar />
  <PageContent>
    <TableOfContents />
    <DocumentationText />
  </PageContent>
</PageLayout>
```

As your project grows, you will notice that many of your designs can be composed by reusing components you already wrote, speeding up you development. Our table of contents above could be added to any screen with <TableOfContents />! You can even jumpstart your project with the thousands of components shared by the React open source community like Chakra UI and Material UI.

### Defining a component

Traditionally when creating web pages, web developers marked up their content and then added interaction by sprinkling on some JavaScript. This worked great when interaction was a nice-to-have on the web. Now it is expected for many sites and all apps. React puts interactivity first while still using the same technology: **a React component is a JavaScript function that you can *sprinkle with markup*.** Here’s what that looks like (you can edit the example below):

```jsx
export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3Am.jpg"
      alt="Katherine Johnson"
    />
  )
}
```

### Using a component

Now that you’ve defined your `Profile` component, you can nest it inside other components. For example, you can export a `Gallery` component that uses multiple `Profile` components:

```jsx
function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3As.jpg"
      alt="Katherine Johnson"
    />
  );
}

export default function Gallery() {
  return (
    <section>
      <h1>Amazing scientists</h1>
      <Profile />
      <Profile />
      <Profile />
    </section>
  );
}
```

### Nesting and organizing components

Components are regular JavaScript functions, so you can keep multiple components in the same file. This is convenient when components are relatively small or tightly related to each other. If this file gets crowded, you can always move `Profile` to a separate file. You will learn how to do this shortly on the [page about imports.](https://react.dev/learn/importing-and-exporting-components)

Because the `Profile` components are rendered inside `Gallery`—even several times!—we can say that `Gallery` is a **parent component,** rendering each `Profile` as a “child”. This is part of the magic of React: you can define a component once, and then use it in as many places and as many times as you like.

### **Recap**

You’ve just gotten your first taste of React! Let’s recap some key points.

- React lets you create components, **reusable UI elements for your app.**
- In a React app, every piece of UI is a component.
- React components are regular JavaScript functions except:
    1. Their names always begin with a capital letter.
    2. They return JSX markup.

---

### ****Passing Props to a Component****

React components use props to communicate with each other. Every parent components can pass some information to its child components by giving them props. Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, and functions.

### ****Familiar props****

Props are the information that you pass to a JSX tag. For example, `className`, `src`, `alt`, `width`, and `height` are some of the props you can pass to an `<img>`:

```jsx
function Avatar() {
  return (
    <img
      className="avatar"
      src="https://i.imgur.com/1bX5QH6.jpg"
      alt="Lin Lanying"
      width={100}
      height={100}
    />
  );
}
```

The props you can pass to an `<img>` tag are predefined (ReactDOM conforms to [the HTML standard](https://www.w3.org/TR/html52/semantics-embedded-content.html#the-img-element)). But you can pass any props to *your own* components, such as `<Avatar>`, to customize them. Here’s how!

### How props change over time

```jsx
export default function Clock({ color, time }) {
  return (
    <h1 style={{ color: color }}>
      {time}
    </h1>
  );
}
```

### **Recap**

- To pass props, add them to the JSX, just like you would with HTML attributes.
- To read props, use the `function Avatar({ person, size })` destructuring syntax.
- You can specify a default value like `size = 100`, which is used for missing and `undefined` props.
- You can forward all props with `<Avatar {...props} />` JSX spread syntax, but don’t overuse it!
- Nested JSX like `<Card><Avatar /></Card>` will appear as `Card` component’s `children` prop.
- Props are read-only snapshots in time: every render receives a new version of props.
- You can’t change props. When you need interactivity, you’ll need to set state.