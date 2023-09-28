# Day 65

Tags: React
Date: September 17, 2023
Status: Done

Task of the day

- SSR Framework
    - Next.js
- Forms
    - React hook form
- Advanced topics
    - React Suspense

---

### ****SSR Frameworks****

Server-side rendering (SSR) is a technique for rendering a JavaScript application on the server, rather than in the browser. This can improve the performance and user experience of a web application, as the initial render of the application is done on the server and the content is sent to the browser as a fully-rendered HTML page.

---

### [The Next.js Handbook - learn Next.js for beginners](https://flaviocopes.com/books-dist/next-handbook.pdf)

### Introduction

- Next.js is one React framework to do all of this in a very simple way, but it's
not limited to this. It's advertised by its creators as a **zero-configuration,
single-command toolchain for React apps**.
- Features provided by Next.js
    - **Hot code reloading:** Next.js reloads the page when it detects any change saved to disk.
    - **Automatic Routing:** Any URL is mapped to the filesystem, to files put in the pages folder, and you don't need any configuration (you have customization options of course).

### Next.js vs Gatsby vs create-react-app

Next.js, Gatsby, and create-react-app are amazing tools we can use to power our applications.
Let's first say what they have in common. They all have React under the hood, powering the entire development experience. They also abstract webpack and all those low level things that we used to configure manually in the good old days.
create-react-app does not help you generate a server-side-rendered app easily. Anything that comes with it (SEO, speed...) is only provided by tools like Next.js and Gatsby.

### When is Next.js better than Gatsby?

They can both help with **server-side rendering**, but in 2 different ways.

The end result using Gatsby is a static site generator, without a server. You
build the site, and then you deploy the result of the build process statically on
Netlify or another static hosting site.

Next.js provides a backend that can server side render a response to request,
allowing you to create a dynamic website, which means you will deploy it on
a platform that can run Node.js.

Next.js *can* generate a static site too, but I would not say it's its main use
case.

If my goal was to build a static site, I'd have a hard time choosing and
perhaps Gatsby has a better ecosystem of plugins, including many for
blogging in particular.

Gatsby is also heavily based on GraphQL, something you might really like or
dislike depending on your opinions and needs.

---

### Forms

Although you can build forms using vanilla React, it normally requires a lot of boilerplate code. This is because the form is built using a combination of state and props. To make it easier to manage forms, we use some sort of library.

[https://www.youtube.com/watch?v=IkMND33x0qQ](https://www.youtube.com/watch?v=IkMND33x0qQ)

---

### [React Suspense](https://react.dev/reference/react/Suspense)

React Suspense is a feature in React that allows components to “suspend” rendering while they are waiting for something to happen, such as data to be fetched from an API or an image to be loaded. Suspense allows developers to create a more seamless user experience by rendering a placeholder or fallback component while the component is waiting for the required data to be available.

Here is a general overview of how React Suspense works:

- A component that uses Suspense wraps a component that may need to “suspend” rendering in a suspense component.
- The wrapped component throws a promise when it needs to suspends rendering
- The Suspense component catches the promise and renders a fallback component while the promise is pending
- When the promise resolves, the wrapped component is rendered with the required data

`<Suspense>` lets you display a fallback until its children have finished loading.

```jsx
<Suspense fallback={<Loading />}>
  <SomeComponent />
</Suspense>
```

---

### Portals

Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

**createPortal**

`createPortal` lets you render some children into a different part of the DOM.

```jsx
<div>
  <SomeComponent />
  {createPortal(children, domNode, key?)}
</div>
```

---

### Error Boundaries

In the past, JavaScript errors inside components used to corrupt React’s internal state and cause it to emit cryptic errors on next renders. These errors were always caused by an earlier error in the application code, but React did not provide a way to handle them gracefully in components, and could not recover from them.

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

---

### **[Fiber Architecture](https://dzone.com/articles/understanding-of-react-fiber-architecture)**

React 16.0 was released with an update to the React core algorithm. This new core architecture is named “Fiber.” Facebook has completely rewritten the internals of React from the ground-up while keeping the public API essentially unchanged; in simple terms, it means only changing the engine of a running car.