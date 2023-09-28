# Day 67

Tags: React, React Native
Date: September 20, 2023
Status: Done

Task of the day

- React Basics
    - Components
    - State
    - Props
    - JSX
- Environment Setup
    - Expo
        - create-expo-app
        - Expo Snack
        - Expo tradeoffs
- React Native CLI
- Metro Bundler

---

### React Basics

React Native uses React, a JavaScript library for building user interfaces. You should have a basic understanding of React concepts before proceeding with React Native. Some of the concepts you should be familiar with include:

**Components**

*Components* are one of the core concepts of React. They are the foundation upon which you build user interfaces (UI), which makes them the perfect place to start your React journey!

**Using a component**

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

- React lets you create components, **reusable UI elements for your app.**
- In a React app, every piece of UI is a component.
- React components are regular JavaScript functions except:
    1. Their names always begin with a capital letter.
    2. They return JSX markup.

---

### Props

React components use *props* to communicate with each other. Every parent component can pass some information to its child components by giving them props. Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, and functions.

**Familar props**

React components use *props* to communicate with each other. Every parent component can pass some information to its child components by giving them props. Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, and functions.

- To pass props, add them to the JSX, just like you would with HTML attributes.
- To read props, use the `function Avatar({ person, size })` destructuring syntax.
- You can specify a default value like `size = 100`, which is used for missing and `undefined`props.
- You can forward all props with `<Avatar {...props} />` JSX spread syntax, but don’t overuse it!
- Nested JSX like `<Card><Avatar /></Card>` will appear as `Card` component’s `children` prop.
- Props are read-only snapshots in time: every render receives a new version of props.
- You can’t change props. When you need interactivity, you’ll need to set state.

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

---

### JSX

JSX is a syntax extension for JavaScript that allows you to write HTML-like code within your JavaScript code. It was developed to be used with React and has become an integral part of working with React.

**Basic syntax**

JSX looks similar to HTML, and you can mix it with JavaScript expressions within curly braces `{}`

Here’s an example with a simple JSZ element:

```jsx
const element = <h1>Hello, world!</h1>;
```

### JavaScript expressions in JSX

You can embed JavaScript expressions within JSX by wrapping them in curly braces **`{}`**.

Here’s an example:

```jsx
const name = 'John Doe';
const element = <h1>Hello, {name}!</h1>;
```

### Attributes in JSX

You can use JSX to define attributes for your elements, similar to how you would in HTML. However, some attribute names in JSX are slightly different from their HTML counterparts due to conflicts with reserved JavaScript keywords (for example, `className` instead of `class`).

Here’s an example

```jsx
const className = 'my-class';
const element = <h1 className={className}>Hello, world!</h1>;
```

### Children in JSX

You can nest JSX elements by enclosing them within the opening and closing tags of a parent element.

```jsx
const element = (
  <div>
    <h1>Hello, world!</h1>
    <p>This is an example of nested JSX elements.</p>
  </div>
);
```

### ****JSX Represents Objects****

Under the hood, JSX represents JavaScript objects called “React elements”. When you use JSX, your JavaScript code gets automatically transformed into these React elements.

```jsx
const elementJSX = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);

const elementJSObject = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

Both **`elementJSX`** and **`elementJSObject`** represent the same thing and will produce the same result when rendered.

That’s a brief summary of JSX. You’ll find that it becomes an essential part of working with React as you continue learning about React Native.

# **Pro-tip: Use a JSX Converter**

Converting all these attributes in existing markup can be tedious! We recommend using a [converter](https://transform.tools/html-to-jsx) to translate your existing HTML and SVG to JSX. Converters are very useful in practice, but it’s still worth understanding what is going on so that you can comfortably write JSX on your own.

---

### Environmental setup

In React Native, setting up the development environment is a crucial step. The environment setup process includes installing and configuring various tools and packages required for developing, building, and launching a React Native application. There are two main approaches when setting up your React Native development environment:

Expo CLI is a command-line tool built for creating and managing React Native projects easily. It streamlines your development process by providing an entire development environment, including building and deploying your app to both iOS and Android platforms.

### Expo

Expo is a framework and a platform that allows you to develop, build, and deploy React Native applications easily and quickly. It simplifies the development process and provides a set of useful tools and services, including its own CLI (Command Line Interface), a managed workflow, and an SDK (Software Development Kit) with pre-built modules for common features

**Create Expo App**

**`create-expo-app`** is a command line tool that generates a React Native project that works out of the box with Expo. It is the easiest way to get started building a new React Native application.

**Expo snack**

Expo Snack is an online playground and development environment for creating and testing React Native projects. With Snack, you can easily edit and preview your code changes directly in your browser or on a mobile device using the Expo Go app. It offers a fast, easy, and convenient way to develop, test, and share your projects without needing to set up a local development environment.

- **[Expo Snack Website](https://snack.expo.dev/)**

**Expo Tradeoffs**

Expo is a powerful tool that simplifies the React Native development process, but it has some limitations. Here’s a summary of the tradeoffs you may face when using Expo.

**Limited native modules**

Expo offers a set of pre-built native modules, which are really helpful but might not cover all the functionalities required for your specific app. If you need a custom native module or a third-party library that is not supported by Expo, you’ll have to eject from the Expo managed workflow and switch to the bare-workflow or create a custom native module (native code) yourself.

**Performance**

Expo adds an extra layer to your React Native app, which can cause performance issues, especially for large or complex apps. The bare-workflow may provide better performance as you have more control over the native libraries and app optimization.

**App size**

Expo apps tend to have a larger app size because they include the entire Expo SDK, regardless of which modules you use in your app. In contrast, non-Expo apps can optimize their size by including only the required native modules.

**Updates and upgrades**

When you rely on Expo, you depend on their release cycle for updates and upgrades. If React Native adds a new feature or fixes a bug, you have to wait for an updated Expo version to implement it. This may cause delays or limitations in your app development process.

**Ejecting complications**

If you start a project with Expo and later decide to eject and use regular React Native, you might face challenges migrating your code and adjusting to the new configuration. You may need to rewrite some parts of your code or manually migrate dependencies.

**Limited customizability**

Expo abstracts various aspects of customization and configuration, which can be a double-edged sword. If you need additional customizations that are not supported by Expo, you’ll have to eject or switch to a bare-workflow project, which gives you more control over the native code.

In summary, while Expo offers great tooling and simplifies the development process, it has certain limitations that you should consider before choosing it for your app development.

---

### React Native CLI

React Native CLI is the official command-line interface for building native mobile apps using React Native. This method requires you to manually set up the native development environment and tools needed for iOS and Android app development.

[Setting up the development environment](https://reactnative.dev/docs/environment-setup?guide=native)

---

### Metro Bundler

Metro Bundler is the default bundler for React Native applications. It’s a JavaScript module bundler that takes all your application code and dependencies, and bundles them together into a single JavaScript file or multiple files (based on platform).

[https://facebook.github.io/metro/docs/getting-started](https://facebook.github.io/metro/docs/getting-started)