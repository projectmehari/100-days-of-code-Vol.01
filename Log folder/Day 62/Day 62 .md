# Day 62

Tags: React
Date: September 13, 2023
Status: Done

Task of the day

- Rendering
    - **[React.js under the Hood](https://www.freecodecamp.org/news/react-under-the-hood/)**
- Component life cycle
- List and keys
- Render Props
- Refs
- Events
- High order components

---

### Rendering

React follows a declarative approach to rendering components, which means that developers specify what a component should look like, and React takes care of rendering the component to the screen. This is in contrast to an imperative approach, where developers would write code to manually manipulate the DOM (Document Object Model) to update the UI.

The virtual DOM (VDOM) is an important aspect of how React works. It is a lightweight in-memory representation of the DOM (Document Object Model), and it is used to optimize the rendering of components in a React application.

- Components are written as JavaScript classes or functions that define a render method. The render method returns a description of what the component should look like, using JSX syntax.
- When a component is rendered, React creates a virtual DOM (VDOM) representation of the component. The VDOM is a lightweight in-memory representation of the DOM, and it is used to optimize the rendering of components.
- React compares the VDOM representation of the component with the previous VDOM representation (if it exists). If there are differences between the two VDOMs, React calculates the minimum number of DOM updates needed to bring the actual DOM into line with the new VDOM.
- React updates the actual DOM with the minimum number of DOM updates needed to reflect the changes in the VDOM.

This process is known as reconciliation, and it is an important aspect of how React works. By using a declarative approach and a VDOM, React is able to optimize the rendering of components and improve the performance of web applications.

```jsx
                  +--------+
                  |  React |
                  +--------+
                      |
                      |
                +--------------+
                | Declarative  |
                | Rendering    |
                +--------------+
                      |
                      |
              +------------------+
              | Virtual DOM (VDOM) |
              +------------------+
                |                |
                |                |
          +----------+    +-------------+
          | Components|    |   Render    |
          |           |    |   Method    |
          +----------+    +-------------+
                             |
                    +----------------+
                    | Component       |
                    | Rendering       |
                    +----------------+
                             |
                    +----------------+
                    | Reconciliation  |
                    +----------------+
                             |
                  +-------------------------+
                  | Performance Optimization |
                  +-------------------------+
```

---

****How React works under the hood****

React is a very popular JavaScript library. With over 5.5 million weekly downloads, React is enjoying great popularity. But not a lot of React developers know how React works under the hood. 

**What does React do** 

At its very core, React basically maintains a tree for you. This tree is able to do efficient diff computations on the nodes.

Think of your HTML code as a tree. In fact, that is exactly how the browser treats your DOM (your rendered HTML on the browser). React allows you to effectively re-construct your DOM in JavaScript and push only those changes to the DOM which have actually occurred.

**JSX is syntactic sugar**

there’s nothing like JSX - neither to JavaScript, nor to the browser. JSX is simply syntactic sugar for creating very specific Javascript objects.

When you write something like:

```jsx
const tag = <h1>Hello</h1>
```

What you’re essentially doing is this: 

```jsx
const tag = React.createElement("h1", {}, "Hello")
```

You see, when you start writing nested stuff, not only is this difficult to code, but it also becomes very inconvenient to maintain such a codebase. JSX thus helps you bring the cleanliness of HTML to the power of JavaScript.

**React Renderer**

Now, if you go back to the point where we start our app, you’ll see that in your index.js file, you would find the following line:

```jsx
// .. prev code

ReactDOM.render(<App />, container)
```

From above, we know that when `<App />` has been done parsing, this is just a huge object of React elements. Then how is React able to construct actual divs and p tags out of it? Meet ReactDOM.

ReactDOM in turn, recursively creates nodes depending on their 'type' property and appends them finally to the DOM.

It should be clear at this point that why decoupling React from the renderers is actually a great move! What React does is, simply construct a tree of UI which could be used not only on web, but on environments like mobile too, given that a renderer is available which is able to communicate with the host OS. Here, React Native comes to play. You see, React Native uses React library, but not ReactDOM as the render. Instead, the package react-native itself is a renderer.

We do this in a react native application to start the app:

```jsx
const { AppRegistry } = require('react-native')
AppRegistry.registerComponent('app', () => MainComponent)
```

Look! No ReactDOM. Why not? Because we don't have methods like appendChild, neither do we have a DOM like environment. Instead, for mobiles, we need support for UI directly from OS. But the React library doesn't need to know that, the renderer (React Native) takes care of that.

**React Reconciliation**

When we say that React maintains a copy of DOM using virtual DOM in JavaScript, and it uses to diff it to any changes and apply it to real DOM, we don't want React to brute-force its way. React, in fact does very lazy reconciliation. React would make the least amount of changes possible, i.e. it would try to re-use elements, attributes, and even styles if possible!

consider this example:

```jsx
<img className="class-1" alt="stuff" />
```

Let's say you change this JSX expression to the below one using some condition or some state:

```jsx
<img className="class-1" alt="something else" />
```

Now while diffing, React would see that well, the img tag makes use of the same className both in old and new trees, so why modify it. And it would just modify your alt attribute and move on.

However, there's a catch. Because we don't want React to do a lot of computation on diffing part, React would assume that if a parent has changed, its containing subtree has definitely changed. For example:

```jsx
<div className="class-1">
	<p>I did not change</p>
</div>
```

If you change this JSX to the below using condition/state:

```jsx
<p className="class-1">
	<p>I did not change</p>
</p>
```

Although you could see that we don't need to re-create the inner p tag, but React has no way of knowing that while traversing the tree from top (unless, of course you perform heavy tree diffing, which are much expensive algorithms than the heuristic O(n) react follows for diffing). So, React decides to destroy all children (i.e. calling their cleanup functions in useEffect, or componentWillUnmount in class based components) and re-create the children from scratch.

**React keys**

When adding/removing elements in a node, React would simply loop over the children in old tree and children in the new tree of the node and mark the places where it needs to perform any addition/removal. But this has a disadvantage without additional help from developer. Consider this example:

```jsx
<ul>
    <li>A</li>
    <li>B</li>
</ul>
```

Consider this changed to the below by condition/state:

```jsx
<ul>
    <li>Z</li>
    <li>A</li>
    <li>B</li>
<ul>
```

Now, when React would start comparing the two lists for difference, it would find the difference at child node 1, would mutate the old A to new Z, then again at child node 2, would mutate it from the old B to new A, and then finally append the new B node.

However, a better way would've been to preserve the existing A and B nodes and just prepend the Z node. But how would React know about that? React keys would help.

Keys just provide a nice way to React to know which elements have changed or not changed while diffing. Now, instead of comparing the whole element, React would compare the keys of the children to see which element needs to be added/removed. The below way is an efficient way of performing the same thing: 

```jsx
<ul>
    <li key="A">A</li>
    <li key="B">B</li>
</ul>
```

Now, if this gets changed to:

```jsx
<ul>
    <li key="Z">Z</li>
    <li key="A">A</li>
    <li key="B">B</li>
</ul>
```

React would now know that keys 'A' and 'B' already exists, so we just need to add the new element with key 'Z'.

*Are you a React developer? Show off your **React skills** by developing a 3 minute interactive game in React and **win hoodies, shirts and coffee mugs**! Take part in **codecomp** by joining codedamn's discord server **[here](http://bit.ly/codedamn-discord)***

So these were some important concepts I believe would be really helpful for you as a React developers to start understanding the core of React and how it actually works. Feel free to pass down any suggestions or questions you have about the same

---

### Component life cycle

React components have a lifecycle consisting of three phases: Mounting, updating and Unmounting along with several “lifecycle methods” that you can override to run code at particular times in the process. 

It is not recommended to use lifecycle methods manually. Instead, use the useEffect hook with the functional components

**Class component**

`Component` is the base class for the React components defined as [JavaScript classes.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) Class components are still supported by React, but we don’t recommend using them in new code.

```jsx
class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

**Component**

To define a React component as a class, extend the built-in `Component` class and define a `[render` method:](https://react.dev/reference/react/Component#render)

```jsx
import { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

Only the `render` method is required, other methods are optional.

**Usage: Define a class component**

To define a React component as a class, extend the built-in `Component` class and define a `[render` method:](https://react.dev/reference/react/Component#render)

```jsx
import { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

React will call your `[render](https://react.dev/reference/react/Component#render)` method whenever it needs to figure out what to display on the screen. Usually, you will return some [JSX](https://react.dev/learn/writing-markup-with-jsx) from it. Your `render` method should be a [pure function:](https://en.wikipedia.org/wiki/Pure_function) it should only calculate the JSX.

Similarly to [function components,](https://react.dev/learn/your-first-component#defining-a-component) a class component can [receive information by props](https://react.dev/learn/your-first-component#defining-a-component) from its parent component. However, the syntax for reading props is different. For example, if the parent component renders `<Greeting name="Taylor" />`, then you can read the `name` prop from `[this.props](https://react.dev/reference/react/Component#props)`, like `this.props.name`:

```jsx
import { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default function App() {
  return (
    <>
      <Greeting name="Sara" />
      <Greeting name="Cahal" />
      <Greeting name="Edite" />
    </>
  );
}
```

Note that Hooks (functions starting with `use`, like `[useState](https://react.dev/reference/react/useState)`) are not supported inside class components.****

---

### Lifecycle of Reactive effects

Effects have a different lifecycle from components. Components may mount, update, or unmount. An Effect can only do two things: to start synchronizing something, and later to stop synchronizing it. This cycle can happen multiple times if your Effect depends on props and state that change over time. React provides a linter rule to check that you’ve specified your Effect’s dependencies correctly. This keeps your Effect synchronized to the latest props and state.

**The lifecycle of an effect**

Every React component goes through the same lifecycle:

- A component mounts when it’s added to the screen
- A component updates when it receives new props or state, usually in response to an interaction.
- A component unmounts when it’s removed from the screen

**It’s a good way to think about components, but not about Effects.**  

Instead, try to think about each Effect independently from your component’s lifecycle. An Effect describes how to [synchronize an external system](https://react.dev/learn/synchronizing-with-effects) to the current props and state. As your code changes, synchronization will need to happen more or less often. To illustrate this point, consider this Effect connecting your component to a chat server:

```jsx
const serverUrl = 'https://localhost:1234';

function ChatRoom({ roomId }) {
  useEffect(() => {
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
  }, [roomId]);
  // ...
}
```

Your Effect’s body specifies how to **start synchronizing:**

```jsx
// ...
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
    // ...
```

The cleanup function returned by your Effect specifies how to **stop synchronizing:**

```jsx
// ...
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
    // ...
```

Intuitively, you might think that React would **start synchronizing** when your component mounts and **stop synchronizing** when your component unmounts. However, this is not the end of the story! Sometimes, it may also be necessary to **start and stop synchronizing multiple times** while the component remains mounted.

---

### List & keys

[https://www.youtube.com/watch?v=Jh47pOXwGq0](https://www.youtube.com/watch?v=Jh47pOXwGq0)

**Key**: a string attribute that identifies items in lists of elements.

**Keeping list items in order with `key`**

Notice that all the sandboxes above shown an erro in the console:

**Warning: Each child in a list should have a unique “key” prop.

You need to give each array item a key — a string or a number that uniquely identifies it among other items in that array:

```jsx
<li key={person.id}>...</li>
```

Keys tell React which array item each component corresponds to, so that it can match them up later. This becomes important if your array items can move (e.g. due to sorting), get inserted, or get deleted. A well-chosen `key` helps React infer what exactly has happened, and make the correct updates to the DOM tree.

**Where to get your key**

Different sources of data provide different sources of keys:

- **Data from a database:** If your data is coming from a database, you can use the database keys/IDs, which are unique by nature.
- **Locally generated data:** If your data is generated and persisted locally (e.g. notes in a note-taking app), use an incrementing counter, `[crypto.randomUUID()](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/randomUUID)` or a package like `[uuid](https://www.npmjs.com/package/uuid)` when creating items.

**Rules of keys**

- **Keys must be unique among siblings.** However, it’s okay to use the same keys for JSX nodes in *different* arrays.
- **Keys must not change** or that defeats their purpose! Don’t generate them while rendering.

**Why does React need keys?**

Imagine that files on your desktop didn’t have names. Instead, you’d refer to them by their order — the first file, the second file, and so on. You could get used to it, but once you delete a file, it would get confusing. The second file would become the first file, the third file would be the second file, and so on.

File names in a folder and JSX keys in an array serve a similar purpose. They let us uniquely identify an item between its siblings. A well-chosen key provides more information than the position within the array. Even if the *position* changes due to reordering, the `key` lets React identify the item throughout its lifetime.

---

### Render Props

[https://www.youtube.com/watch?v=NdapMDgNhtE](https://www.youtube.com/watch?v=NdapMDgNhtE)

**Passing props to a component**

React components use props to communicate with each other. Every parent component can pass some information to its child components by giving them props. Props might remind you of HTML attributes, but you can pass any JavaScripts value through them, including objects, arrays, and functions.

```
[ Parent Component ]
         |
    +----+----+
    |         |
[ Child 1 ] [ Child 2 ]
```

**Familiar props**

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

export default function Profile() {
  return (
    <Avatar />
  );
}
```

The props you can pass to an `<img>` tag are predefined (ReactDOM conforms to [the HTML standard](https://www.w3.org/TR/html52/semantics-embedded-content.html#the-img-element)). But you can pass any props to *your own* components, such as `<Avatar>`, to customize them. Here’s how!

**Passing props to a component**

In this code, the `Profile` component isn’t passing any props to its child component, `Avatar`:

```jsx
export default function Profile() {
  return (
    <Avatar />
  );
}
```

You can give `Avatar` some props in two steps.

**Step 1: Pass props to the child component**

First, pass some props to `Avatar`. For example, let’s pass two props: `person` (an object), and `size` (a number):

```jsx
export default function Profile() {
  return (
    <Avatar
      person={{ name: 'Lin Lanying', imageId: '1bX5QH6' }}
      size={100}
    />
  );
}
```

Now you can read these props inside the `Avatar` component.

**Step 2: Read props inside the child component**

You can read these props by listing their names `person, size` separated by the commas inside `({` and `})` directly after `function Avatar`. This lets you use them inside the `Avatar` code, like you would with a variable.

```jsx
function Avatar({ person, size }) {
  // person and size are available here
}
```

Add some logic to `Avatar` that uses the `person` and `size` props for rendering, and you’re done.

Now you can configure `Avatar` to render in many different ways with different props. Try tweaking the values!

```jsx
import { getImageUrl } from './utils.js';

function Avatar({ person, size }) {
  return (
    <img
      className="avatar"
      src={getImageUrl(person)}
      alt={person.name}
      width={size}
      height={size}
    />
  );
}

export default function Profile() {
  return (
    <div>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi', 
          imageId: 'YfeOqp2'
        }}
      />
      <Avatar
        size={80}
        person={{
          name: 'Aklilu Lemma', 
          imageId: 'OKS67lh'
        }}
      />
      <Avatar
        size={50}
        person={{ 
          name: 'Lin Lanying',
          imageId: '1bX5QH6'
        }}
      />
    </div>
  );
}
```

Props let you think about parent and child components independently. For example, you can change the `person` or the `size` props inside `Profile` without having to think about how `Avatar` uses them. Similarly, you can change how the `Avatar` uses these props, without looking at the `Profile`.

You can think of props like “knobs” that you can adjust. They serve the same role as arguments serve for functions—in fact, props *are* the only argument to your component! React component functions accept a single argument, a `props` object:

```jsx
function Avatar(props) {
  let person = props.person;
  let size = props.size;
  // ...
}
```

Usually you don’t need the whole `props` object itself, so you destructure it into individual props.****

**Specifying a default value for a prop**

If you want to give a prop a default value to fall back on when no value is specified, you can do it with the destructuring by putting `=` and the default value right after the parameter:

```jsx
function Avatar({ person, size = 100 }) {
  // ...
}
```

Now, if `<Avatar person={...} />` is rendered with no `size` prop, the `size` will be set to `100`.

The default value is only used if the `size` prop is missing or if you pass `size={undefined}`. But if you pass `size={null}` or `size={0}`, the default value will **not** be used.

**Forwarding props with the JSX spread syntax**

Sometimes, passing props gets very repetitive:

```jsx
function Profile({ person, size, isSepia, thickBorder }) {
  return (
    <div className="card">
      <Avatar
        person={person}
        size={size}
        isSepia={isSepia}
        thickBorder={thickBorder}
      />
    </div>
  );
}
```

There’s nothing wrong with repetitive code—it can be more legible. But at times you may value conciseness. Some components forward all of their props to their children, like how this `Profile` does with `Avatar`. Because they don’t use any of their props directly, it can make sense to use a more concise “spread” syntax:

```jsx
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```

This forwards all of `Profile`’s props to the `Avatar` without listing each of their names.

**Use spread syntax with restraint.** If you’re using it in every other component, something is wrong. Often, it indicates that you should split your components and pass children as JSX. More on that next!

**Passing JSX as children**

It is common to nest built-in browser tags:

```jsx
<div>
  <img />
</div>
```

Sometimes you’ll want to nest your own components the same way:

```jsx
<Card>
  <Avatar />
</Card>
```

When you nest content inside a JSX tag, the parent component will receive that content in a prop called `children`. For example, the `Card` component below will receive a `children` prop set to `<Avatar />` and render it in a wrapper div:

```jsx
import Avatar from './Avatar.js';

function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}

export default function Profile() {
  return (
    <Card>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi',
          imageId: 'YfeOqp2'
        }}
      />
    </Card>
  );
}
```

Try replacing the `<Avatar>` inside `<Card>` with some text to see how the `Card` component can wrap any nested content. It doesn’t need to “know” what’s being rendered inside of it. You will see this flexible pattern in many places.

You can think of a component with a `children` prop as having a “hole” that can be “filled in” by its parent components with arbitrary JSX. You will often use the `children` prop for visual wrappers: panels, grids, etc.

![Screen Shot 2023-09-14 at 2.07.43 PM.png](Day%2062%2026cc9c2c4cd345f5ba72495693a32e02/Screen_Shot_2023-09-14_at_2.07.43_PM.png)

**How props change over time**

The `Clock` component below receives two props from its parent component: `color` and `time`. (The parent component’s code is omitted because it uses [state](https://react.dev/learn/state-a-components-memory), which we won’t dive into just yet.

Try changing the color in the select box below:

```jsx
export default function Clock({ color, time }) {
  return (
    <h1 style={{ color: color }}>
      {time}
    </h1>
  );
}
```

This example illustrates that **a component may receive different props over time.** Props are not always static! Here, the `time` prop changes every second, and the `color` prop changes when you select another color. Props reflect a component’s data at any point in time, rather than only in the beginning.

However, props are [immutable](https://en.wikipedia.org/wiki/Immutable_object)—a term from computer science meaning “unchangeable”. When a component needs to change its props (for example, in response to a user interaction or new data), it will have to “ask” its parent component to pass it *different props*—a new object! Its old props will then be cast aside, and eventually the JavaScript engine will reclaim the memory taken by them.

**Don’t try to “change props”.** When you need to respond to the user input (like changing the selected color), you will need to “set state”, which you can learn about in [State: A Component’s Memory.](https://react.dev/learn/state-a-components-memory)

### Recap

- To pass props, add them to the JSX, just like you would with HTML attributes.
- To read props, use the `function Avatar({ person, size })` destructuring syntax.
- You can specify a default value like `size = 100`, which is used for missing and `undefined` props.
- You can forward all props with `<Avatar {...props} />` JSX spread syntax, but don’t overuse it!
- Nested JSX like `<Card><Avatar /></Card>` will appear as `Card` component’s `children`prop.
- Props are read-only snapshots in time: every render receives a new version of props.
- You can’t change props. When you need interactivity, you’ll need to set state

**Summary**

React components use props to communicate with each other. You can pass any JavaScript value through props, including objects, arrays, and functions. To pass props, add them to the JSX, and to read props, use the destructuring syntax. You can specify a default value for a prop, forward all props with JSX spread syntax, and nest JSX to appear as a component's children prop. Props are read-only snapshots in time, and you can't change props; when you need interactivity, you'll need to set state.

```jsx
                      React Components
                             |
                           props
                             |
     +-----------------------+-----------------------+
     |                       |                       |
  JavaScript              Passing                 Reading
  Values                 props                   props
     |                       |                       |
   Objects                Adding                Destructuring
     |                       |                       |
   Arrays                to JSX                    Syntax
     |                       |                       |
  Functions             Default                  Forwarding
     |                    Value                     props
     |                       |                    JSX Spread
     |                       |                       | 
  Setting                  Nesting                   |
   State                JSX as Children            |
     |                       |                       |
  Interactivity              |                       |
     |                       |                       |
     +-----------------------+-----------------------+
                             |
                          Props
                             |
             +---------------+---------------+
             |                               |
      Read-only Snapshots              Can't Change Props
             |                               |
        In Time                    Need to Set State
```

---

### [Render props pattern](https://www.patterns.dev/posts/render-props-pattern)

Another way of making components very reusable, is by using the **render prop** pattern. A render prop is a prop on a component, which value is a function that returns a JSX element. The component itself does not render anything besides the render prop. Instead, the component simply calls the render prop, instead of implementing its own rendering logic.

**Pros**

Sharing logic and data among several components is easy with the render props pattern. Components can be made very reusable, by using a render or `children` prop. Although the Higher Order Component pattern mainly solves the same issues, namely **reusability** and **sharing data**, the render props pattern solves some of the issues we could encounter by using the HOC pattern.

The issue of **naming collisions** that we can run into by using the HOC pattern no longer applies by using the render props pattern, since we don't automatically merge props. We explicitly pass the props down to the child components, with the value provided by the parent component.

Since we explicitly pass props, we solve the HOC's implicit props issue. The props that should get passed down to the element, are all visible in the render prop's arguments list. This way, we know exactly where certain props come from.

We can separate our app's logic from rendering components through render props. The stateful component that receives a render prop can pass the data onto stateless components, which merely render the data.

**Cons**

The issues that we tried to solve with render props, have largely been replaced by React Hooks. As Hooks changed the way we can add reusability and data sharing to components, they can replace the render props pattern in many cases.

Since we can't add lifecycle methods to a `render` prop, we can only use it on components that don't need to alter the data they receive.

---

### **Refs**

Refs provide a way to access DOM nodes or React elements created in the render method.

In the typical React dataflow, props are the only way that parent components interact with their children. To modify a child, you re-render it with new props. However, there are a few cases where you need to imperatively modify a child outside of the typical dataflow. The child to be modified could be an instance of a React component, or it could be a DOM element. For both of these cases, React provides an escape hatch.

**Referencing values with Refs**

When you want a component to “remember” some information, but you don’t want that information to [trigger new renders](https://react.dev/learn/render-and-commit), you can use a *ref*.

**Adding a ref to your component**

You can add a ref to your component by importing the `useRef` Hook from React:

```jsx
import { useRef } from 'react';
```

Inside your component, call the `useRef` Hook and pass the initial value that you want to reference as the only argument. For example, here is a ref to the value `0`:

```jsx
const ref = useRef(0);
```

`useRef` returns an object like this:

```jsx
{ 
  current: 0 // The value you passed to useRef
}
```

You can access the current value of that ref through the `ref.current` property. This value is intentionally mutable, meaning you can both read and write to it. It’s like a secret pocket of your component that React doesn’t track. (This is what makes it an “escape hatch” from React’s one-way data flow—more on that below!)

Here, a button will increment `ref.current` on every click:

```jsx
import { useRef } from 'react';

export default function Counter() {
  let ref = useRef(0);

  function handleClick() {
    ref.current = ref.current + 1;
    alert('You clicked ' + ref.current + ' times!');
  }

  return (
    <button onClick={handleClick}>
      Click me!
    </button>
  );
}
```

The ref points to a number, but, like [state](https://react.dev/learn/state-a-components-memory), you could point to anything: a string, an object, or even a function. Unlike state, ref is a plain JavaScript object with the `current` property that you can read and modify.

Note that **the component doesn’t re-render with every increment.** Like state, refs are retained by React between re-renders. However, setting state re-renders a component. Changing a ref does not!

**Best practices for Refs**

Following these principles will make your components more predictable:

- Treat refs as an escape hatch: Refs are useful when you work with external systems or browser APIs. If much of your application logic and data flows relies on refs, you might want to rethink your approach.
- Don’t read or write **`ref.current` during rendering.** If some information is needed during rendering, use [state](https://react.dev/learn/state-a-components-memory) instead. Since React doesn’t know when `ref.current`changes, even reading it while rendering makes your component’s behavior difficult to predict. (The only exception to this is code like `if (!ref.current) ref.current = new Thing()` which only sets the ref once during the first render.)

Limitations of React state don’t apply to refs. For example, state acts like a [snapshot for every render](https://react.dev/learn/state-as-a-snapshot) and [doesn’t update synchronously.](https://react.dev/learn/queueing-a-series-of-state-updates) But when you mutate the current value of a ref, it changes immediately:

```jsx
ref.current = 5;
console.log(ref.current); // 5
```

This is because **the ref itself is a regular JavaScript object,** and so it behaves like one.

You also don’t need to worry about [avoiding mutation](https://react.dev/learn/updating-objects-in-state) when you work with a ref. As long as the object you’re mutating isn’t used for rendering, React doesn’t care what you do with the ref or its contents.

**Refs and the DOM**

You can point a ref to any value. However, the most common use case for a ref is to access a DOM element. For example, this is handy if you want to focus an input programmatically. When you pass a ref to a `ref` attribute in JSX, like `<div ref={myRef}>`, React will put the corresponding DOM element into `myRef.current`. You can read more about this in [Manipulating the DOM with Refs.](https://react.dev/learn/manipulating-the-dom-with-refs)

**Recap**

- Refs are an escape hatch to hold onto values that aren’t used for rendering. You won’t need them often.
- A ref is a plain JavaScript object with a single property called `current`, which you can read or set.
- You can ask React to give you a ref by calling the `useRef` Hook.
- Like state, refs let you retain information between re-renders of a component.
- Unlike state, setting the ref’s `current` value does not trigger a re-render.
- Don’t read or write `ref.current` during rendering. This makes your component hard to predict.

---

### Events

Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:

- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.

**[Responding to events](https://react.dev/learn/responding-to-events)**

React lets you add *event handlers* to your JSX. Event handlers are your own functions that will be triggered in response to interactions like clicking, hovering, focusing form inputs, and so on.

**Recap**

- You can handle events by passing a function as a prop to an element like <button>
- Event handlers must be passed, not called! `onClick={handleClick}`, not `onClick={handleClick()}`.
- You can define an event handler function separately or inline
- Event handlers are defined inside a component, so they can access props.
- You can declare an event handler in a parent and pass it as a prop to a child.
- You can define your own event handler props with application-specific names.
- Events propagate upwards. `e.stopPropagation()` on the first argument to prevent that.
- Events may have unwanted default browser behavior. Call `e.preventDefault()` to prevent that.
- Explicitly calling an event handler prop from a child handler is a good alternative to propagation.

---

### High order components

A higher-order component (HOC) is advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React’s compositional nature.

Concretely, a higher-order component is a function that takes a component and returns a new component.

Higher-order components are not commonly used in modern React code. In order to reuse logic, **React hooks are mainly used now.**

Whereas a component transforms props into UI, a higher-order component transforms a component into another component.

HOCs are common in third-party React libraries, such as Redux’s `[connect](https://react-redux.js.org/api/connect)` and Relay’s `[createFragmentContainer](https://relay.dev/docs/v10.1.3/fragment-container/#createfragmentcontainer)`.