# Day 41

Tags: React
Date: August 17, 2023
Status: Done

Task of the day

- React Components

---

**COMPONENTS RENDER OTHER COMPONENTS**

### **Components Interact**

A React application can contain dozens, or even hundreds, of components.

Each component might be small and relatively unremarkable on its own. When combined, however, they can form enormous, fantastically complex ecosystems of information.

In other words, React apps are made out of components, but what makes React special isn’t the components themselves. What makes React special is the ways in which components *interact*.

This lesson is an introduction to *components interacting*. After this lesson, you should be familiar with:

- how components can reference other components.
- how this allows us to separate our components into separate files.

![Screen Shot 2023-08-17 at 4.30.31 PM.png](Day%2041%202e57911b941c4b0db935a685d0be1f99/Screen_Shot_2023-08-17_at_4.30.31_PM.png)

---

**PROPS**

### **Render Different UI Based on props**

You can do more with props than just display them. You can also use props to make decisions.

```
function LoginMsg(props) {
  if (props.password === 'a-tough-password') {
    return <h2>Sign In Successful.</h2>
  } else {
    return <h2>Sign In Failed..</h2>
  }
}

```

In this example, we use the props passed in to make a decision rather than rendering the value to the screen.

If the `password` received is equal to `'a-tough-password'`, the resulting message in `<h2></h2>` will be different!

The passed-in `password` is not displayed in either case! The prop is used to *decide* what will be displayed. This is a common technique.

---

**PROPS**

### **Review**

That completes our lesson on props! Here are some of the skills that you’ve learned:

- Passing a prop by giving an *attribute* to a component instance.
- Accessing a passed-in prop via `props.propName`.
- Displaying a prop.
- Using a prop to make decisions about what to display.
- Defining an event handler in a function component.
- Passing an event handler as a prop.
- Receiving a prop event handler and attaching it to an event listener.
- Naming event handlers and event handler attributes according to a convention.
- Accessing `props.children`.
- Assigning default values to props.

That’s a lot! Don’t worry if it’s all a bit of a blur. You’ll soon get plenty of practice!