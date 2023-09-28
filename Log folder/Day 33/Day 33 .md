# Day 33

Tags: Docs, Front-end, Javascript
Date: August 7, 2023
Status: Done

Task of the day

- Builder DAO “working in public session #13
- Documentation
- Introduction: JavaScript Syntax, Part I

---

**DOCUMENTATION AND RESEARCH**

## **Review**

Awesome! With just a few simple searches and some research you completed the header for your portfolio site. Reading documentation and searching Google and Stack Overflow make it easy to solve development problems, even if you haven’t previously encountered the right tool for the job.

In summary:

1. Documentation is an easy way to view all of the information about a language or framework. The *[Mozilla Development Network](https://developer.mozilla.org/en-US/)* is the source of documentation for HTML, CSS, and JavaScript.
2. Investigating a new language feature is as easy as typing the problem and the language into [Google](https://google.com/) or [Stack Overflow](https://stackoverflow.com/).

Now that you know how to find any feature and read its documentation, the sky’s the limit on what you can do. Feel free to browse MDN and Stack Overflow to find new features and try incorporating them into your header to make it look even better. Great job!

---

# **Introduction: CSS Transitions and Animation**

**In this unit, you will create visually dynamic websites using CSS.**

The goal of this unit is to create visually dynamic websites using CSS. You will learn how to utilize transitions and animation to provide visual feedback to users.

After this unit, you will be able to:

- Use transitions between CSS properties
- Create multi-step animations using CSS

Learning is social. Whatever you’re working on, be sure to connect with the Codecademy community in the [forums](https://discuss.codecademy.com/). Remember to check in with the community regularly, including for things like asking for code reviews on your project work and providing code reviews to others in the [projects category](https://discuss.codecademy.com/c/project/1833), which can help to reinforce what you’ve learned.

---

**CSS TRANSITIONS**

## **Review**

*CSS Transitions* are a powerful tool for providing visual feedback to users. We’ve learned a lot about transitions, so let’s review:

CSS Transitions have 4 components:

- A *property* that will transition.
- The *duration* which describes how long the transition takes.
- The *delay* to pause before the transition will take place.
- The *timing function* that describes the transition’s acceleration.

A simple transition can be described with a property and a duration, which can be written like this:

```css
transition-property: color;
transition-duration: 1s;

```

Many properties’ *state changes* can be transitioned, including color, background color, font size, width, and height. `all` is also a valid transition property that causes every changing property to transition.

The shorthand property `transition` can be used to describe all four components of a transition at once. By using the comma (`,`) operator, many transitions can be described in one CSS rule.

If you want to learn more about CSS Transitions, we recommend MDN’s [Using CSS Transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions) doc.

Good work, you now have the tools to make your web pages come to life!

---

# **Review: CSS Transitions and Animation**

**In this unit, you learned how to create visually dynamic websites.**

Congratulations! The goal of this unit was to learn how to give visual feedback to your website’s users with transitions, transforms, and animations.

Having completed this unit, you are now able to:

- Use transitions between CSS properties
- Create multi-step animations using CSS

If you are interested in learning more about these topics, here are some additional resources:

- Article: [CSS Transitions and Transforms for Beginners](https://thoughtbot.com/blog/transitions-and-transforms)
- Article: [Web Animation at Work, Rachel Nabors](https://alistapart.com/article/web-animation-at-work/)
- Article: [Scaling Responsive Animations, Zach Saucier](https://css-tricks.com/scaling-responsive-animations/)
- Article: [The Facebook Loading Animation in CSS](https://css-tricks.com/the-facebook-loading-animation-in-css/)
- Resource: [keyframes.app](https://keyframes.app/)
- Resource: [animista.net](https://animista.net/)
- Resource: [cubic-bezier.com](https://cubic-bezier.com/#.17,.67,.83,.67)
- Resource: [easings.net](https://easings.net/)

Learning is social. Whatever you’re working on, be sure to connect with the Codecademy community in the [forums](https://discuss.codecademy.com/). Remember to check in with the community regularly, including for things like asking for code reviews on your project work and providing code reviews to others in the [projects category](https://discuss.codecademy.com/c/project/1833), which can help to reinforce what you’ve learned.

---

**INTRODUCTION TO JAVASCRIPT**

## **Review**

Let’s take one more glance at the concepts we just learned:

- Data is printed, or logged, to the console, a panel that displays messages, with `console.log()`.
- We can write single-line comments with `//` and multi-line comments between `/*` and `/`.
- There are 7 fundamental data types in JavaScript: strings, numbers, booleans, null, undefined, symbol, and object.
- Numbers are any number without quotes: `23.8879`
- Strings are characters wrapped in single or double quotes: `'Sample String'`
- The built-in arithmetic operators include `+`, ``, ``, `/`, and `%`.
- Objects, including instances of data types, can have properties, stored information. The properties are denoted with a `.` after the name of the object, for example: `'Hello'.length`.
- Objects, including instances of data types, can have methods which perform actions. Methods are called by appending the object or instance with a period, the method name, and parentheses. For example: `'hello'.toUpperCase()`.
- We can access properties and methods by using the `.`, dot operator.
- Built-in objects, including `Math`, are collections of methods and properties that JavaScript provides.

---

**VARIABLES**

## **Review Variables**

Nice work! This lesson introduced you to variables, a powerful concept you will use in all your future programming endeavors.

Let’s review what we learned:

- Variables hold reusable data in a program and associate it with a name.
- Variables are stored in memory.
- The `var` keyword is used in pre-ES6 versions of JS.
- `let` is the preferred way to declare a variable when it can be reassigned, and `const` is the preferred way to declare a variable with a constant value.
- Variables that have not been initialized store the primitive data type `undefined`.
- Mathematical assignment operators make it easy to calculate a new value and assign it to the same variable.
- The `+` operator is used to concatenate strings including string values held in variables.
- In ES6, template literals use backticks ``` and `${}` to interpolate values into a string.
- The `typeof` keyword returns the data type (as a string) of a value.