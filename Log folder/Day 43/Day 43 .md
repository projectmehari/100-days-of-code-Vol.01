# Day 43

Tags: React
Date: August 22, 2023
Status: Done

Task of the day 

- React Styles
- React Forms

---

**REACT FORMS**

### **React Forms**

Think about how forms work in a typical, non-React environment. A user types some data into a form’s input fields, and the server doesn’t know about it. The server remains clueless until the user hits a “submit” button, which sends all of the form’s data over to the server simultaneously.

In React, as in many other JavaScript environments, this is not the best way of doing things.

The problem is the period of time during which a form thinks that a user has typed one thing, but the server thinks that the user has typed a different thing. What if, during that time, a *third* part of the website needs to know what a user has typed? It could ask the form or the server and get two different answers. In a complex JavaScript app with many moving, interdependent parts, this kind of conflict can easily lead to problems.

In a React form, you want the server to know about every new character or deletion, *as soon as it happens*. That way, your screen will always be in sync with the rest of your application

---

**REACT FORMS**

### **Controlled vs Uncontrolled**

There are two terms that will probably come up when you talk about React forms: **controlled component** and **uncontrolled component**.

An *uncontrolled component* is a component that maintains its own internal state. A *controlled component* is a component that does not maintain any internal state. Since a controlled component has no state, it must be *controlled* by someone else.

Think of a typical `<input type='text' />` element. It appears on the screen as a text box. If you need to know what text is currently in the box, then you can ask the `<input>` element, possibly with some code like this:

```
let input = document.querySelector('input[type="text"]');

let typedText = input.value; // input.value will be equal to whatever text is currently in the text box.

```

The important thing here is that the `<input>` element *keeps track of* its own text. You can access what its text is at any time.

The fact that `<input>` keeps track of information makes it an *uncontrolled component*. It maintains its own internal state by remembering data about itself.

A controlled component, on the other hand, has no memory. If you ask it for information about itself, then it will have to get that information through `props`. Most React components are *controlled*.

In React, when you give an `<input>` element a `value` attribute, then something strange happens: the `<input>` element *becomes controlled*. It stops using its internal storage. This is a more “React” way of doing things.

Recall that in our exercises, the page updated every time we typed into the input. React controlled the input’s value with the state. We’ve been demonstrating the idea of a controlled component all along!

You can find more information about [controlled and uncontrolled components](https://react.dev/learn/sharing-state-between-components#controlled-and-uncontrolled-components) in the React documentation.

---

**REACT FORMS**

### **Review**

Great work! You just wrote your first React form.

Here’s a review:

- The state of a React form is managed by the component, and updates are triggered by the `onChange` event.
- The `onChange` event uses an event handler to capture changes and determine what actions to take.
- A **React form uses the State hook** to store the value of the input field in the component’s state. The state can then be updated with the state setter.
- React components can be controlled or uncontrolled. Most React forms are controlled, as they control the input’s value with the state.

That marks the end of this lesson! The skills you’ve learned with React forms will be invaluable as you continue to build out more React apps!

---