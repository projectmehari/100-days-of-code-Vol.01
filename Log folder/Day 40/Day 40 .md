# Day 40

Tags: React
Date: August 16, 2023
Status: Done

Task of the day 

- Web frameworks
- React
    - Intro to JSX
    - React Components

---

### ****What is the difference between a framework and a library?****

[https://www.youtube.com/watch?v=D_MO9vIRBcA](https://www.youtube.com/watch?v=D_MO9vIRBcA)

The difference is within the caller/callee relationship 

Framework code

- your code
- Library code

---

### ****I built the same app 10 times // Which JS Framework is best?****

[https://www.youtube.com/watch?v=cuHDQhDhvPE](https://www.youtube.com/watch?v=cuHDQhDhvPE)

### React

- Minimal
- Open source community
- + flexibility
- Create React App
- you can create an new react project by using

```jsx
npx create-react-app myapp
```

**Your information is organized as a tree**

![Screen Shot 2023-08-16 at 2.48.19 PM.png](Day%2040%2043e2e184f2974274aecf15f5b8d2c363/Screen_Shot_2023-08-16_at_2.48.19_PM.png)

The react is organized **UI = f(state)**

---

### Why React?

React.js is a JavaScript library developed by engineers at Facebook. Here are just a few of the reasons why people choose to program with React:

- **React is *fast*.** Apps made in React can handle complex updates and still feel quick and responsive.
- **React is *modular*.** Instead of writing large, dense files of code, you can write many smaller, reusable files. React’s modularity can be a beautiful solution to JavaScript’s [maintainability problems](https://en.wikipedia.org/wiki/Spaghetti_code).
- **React is *scalable*.** Large programs that display a lot of changing data are where React performs best.
- **React is *flexible*.** You can use React for interesting projects that have nothing to do with making a web app. People are still figuring out React’s potential. [There’s room to explore](https://github.com/jiwonbest/amazing-react-projects).
- **React is *popular*.** While this reason has admittedly little to do with React’s quality, the truth is that understanding React will make you more employable.

---

**INTRO TO JSX**

## **What is JSX?**

*JSX* is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does “syntax extension” mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it!

If a JavaScript file contains JSX code, then that file will have to be *compiled*. This means that before the file reaches a web browser, a *JSX compiler* will translate any JSX into regular JavaScript.

Codecademy’s servers already have a JSX compiler installed, so you don’t have to worry about that for now. Eventually we’ll walk through how to set up a JSX compiler on your personal computer.

**INTRO TO JSX**

## **Rendering JSX Explained**

Let’s examine the code that you just wrote in the last exercise.

```
const container = document.getElementById('app');
const root = createRoot(container);
root.render(<h1>Hello world</h1>);

```

Before we get started it is essential to understand that React relies on two things to render: what content to render and where to place the content at.

With that in mind, let’s look at the first line:

```
const container = document.getElementById('app')

```

This line:

- Uses [the `document` object](https://developer.mozilla.org/en-US/docs/Web/API/Document) which represents our web page.
- Uses the `getElementById()` method of `document` to get [the `Element` object](https://developer.mozilla.org/en-US/docs/Web/API/Element) representing the HTML element with the passed in id (`app`).
- Stores the element in `container`.

In the next line:

```
const root = createRoot(container)

```

we use `createRoot()` from the `react-dom/client` library, which creates a React root from `container` and stores it in `root`. `root` can be used to render a JSX expression. This is the “where to place the content” part of React rendering.

Finally, the last line:

```
root.render(<h1>Hello world</h1>)

```

uses the `render()` method of `root` to render the content passed in as an argument. Here we pass an `<h1>` element, which displays `Hello world`. This is the “what content to render” part of React rendering.

---

## **Review**

Congratulations! You’ve learned to create and render JSX elements! This is the first step toward becoming fluent in React.

In this lesson, we learned that:

- React is a modular, scalable, flexible, and popular front-end framework.
- JSX is a syntax extension for JavaScript which allows us to treat HTML as expressions.
    - They can be stored in variables, objects, arrays, and more!
- JSX elements can have attributes and be nested within each other, just like in HTML.
- JSX must have exactly one outer element, and other elements can be nested inside.
- `createRoot()` from `react-dom/client` can be used to create a React root at the specified DOM element.
- A React root’s `render()` method can be used to render JSX on the screen.
- A React root’s `render()` method only updates DOM elements that have changed using the virtual DOM.

As you continue to learn more about React, you’ll learn some powerful things you can do with JSX, some common JSX issues, and how to avoid them.

---

**YOUR FIRST REACT COMPONENT**

## **React Components**

React applications are made of **components.**

What’s a component?

A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML and re-render it when some data changes.

Take a look at the code below. This code will create and render a new React component:

```
import React from 'react';
import ReactDOM from 'react-dom/client';

function MyComponent() {
  return <h1>Hello world</h1>;
}

ReactDOM.createRoot(
document.getElementById('app')
).render(<MyComponent />);

```

A lot of these look unfamiliar but do not worry. We are going to unpack that code, one small piece at a time. By the end of this lesson, you’ll understand how to build a React component!

---

## **Function Component Instructions**

Let’s review what you’ve learned so far! Find each of these points in **App.js** and **index.js**:

- On line 1 of **App.js** and **index.js**, `import React from 'react'` creates a JavaScript object. This object contains properties that are needed to make React work, such as `React.createElement()`.
- On line 2 of **index.js** `import ReactDOM from 'react-dom/client'` creates another JavaScript object. This object contains methods that help React interact with the DOM, such as `ReactDOM.createRoot()`.
- On line 3 of **App.js**, by writing a JavaScript function, a function component was defined. We can’t see this component quite yet, as it’s more of a factory that produces instances of itself when used. If we want to see it, we need to render it into the DOM.
- Whenever you create a function component, you need to give that function component a name. That name should be written in Pascal case like this: UpperCamelCase.

Something that we *haven’t* talked about yet is the *body* of your function component: the pair of curly braces after the function definition and all of the code between those curly braces.

Like all JavaScript functions, this one needs a body. The body will act as a set of instructions, explaining to your function component how it should build a React component.

Here’s what your function body would look like on its own, without the rest of the function declaration syntax. Find it in **App.js**:

```
return <h1>Hello, this is a function component body.</h1>;

```

That doesn’t look like a set of instructions explaining how to build a React component! Yet that’s exactly what it is.

---

## **Review**

In this lesson, you’ve learned about a foundational React concept: components.

Before you go, here’s a recap:

- React applications are made up of **components**.
- Components are responsible for rendering pieces of the user interface.
- To create components and render them, `react` and `reactDOM` must be imported.
- React components can be defined with Javascript functions to make **function components**.
- Function component names must start with a capitalized letter, and Pascal case is the adopted naming convention.
- Function components must return some React elements in JSX syntax.
- React components can be exported and imported from file to file.
- A React component can be used by calling the component name in an HTML-like self-closing tag syntax.
- Rendering a React component requires using `.createRoot()` to specify a root container and calling the `.render()` method on it.