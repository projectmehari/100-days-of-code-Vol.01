# Day 37

Tags: Front-end, Javascript
Date: August 11, 2023
Status: Done

Task of the day

- Javascript Syntax, Part 3

---

# **Introduction: JavaScript Syntax, Part III**

**In this unit, you will learn intermediate JavaScript concepts.**

The goal of this unit is to understand intermediate JavaScript concepts, such as classes and modules. Knowing these concepts will improve your ability to write JavaScript programs and prepare you for creating web applications.

After this unit, you will be able to:

- Create classes in JavaScript
- Implement JavaScript Modules
- Create JavaScripts errors and handle them

Learning is social. Whatever you’re working on, be sure to connect with the Codecademy community in the [forums](https://discuss.codecademy.com/). Remember to check in with the community regularly, including for things like asking for code reviews on your project work and providing code reviews to others in the [projects category](https://discuss.codecademy.com/c/project/1833), which can help to reinforce what you’ve learned.

---

## **Review: Classes**

Way to go! Let’s review what you learned.

- *Classes* are templates for objects.
- Javascript calls a *constructor* method when we create a new instance of a class.
- *Inheritance* is when we create a parent class with properties and methods that we can extend to child classes.
- We use the `extends` keyword to create a subclass.
- The `super` keyword calls the `constructor()` of a parent class.
- Static methods are called on the class, but not on instances of the class.

[Classes - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

---

### ****Implementing Modules using ES6 Syntax****

## **Review**

In this article, you have learned the following:

- The benefits of implementing modular programs.
- How to use the ES6 **`export`** statement to *export* code from a file - meaning its functions and/or data can be used by other files/modules.
- How to use the ES6 **`import`** statement to *import* functions and/or data from another module.
- How to rename imported resources using the **`as`** keyword.
- How to export and import a default value.

Though this article covers the basics of using ES6 syntax to import and export modules, [MDN has an excellent article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) that provides an in-depth look at some additional features that ES6 has to offer.

---

**LEARN JAVASCRIPT: ERROR HANDLING**

## **Introduction to Error Handling**

There are two categories of programming mistakes: those that don’t prevent our code from running and those that do.

Sometimes, we’ve written code that successfully returns a value but a different value from what we expected. Our program continues running, and we might not even realize anything went wrong until much later. It’s like making soup and accidentally adding sugar instead of salt. In the end we still have soup, but it might not be soup that we want to eat. We will not be focusing on these mistakes.

Rather, we’re going to focus on the errors that pop up when we’ve written code that causes our program to stop running, e.g. trying to reassign a `const` variable. Instead of returning anything, our program will not execute any more code past where the error occurred. For example, what if we tried to move our soup to the table but dropped it because it was too hot? Then our soup-making process is over— there would be no soup.

We can’t always stop errors before they occur, but we can include a backup plan in our program to anticipate and respond to the errors to ensure that our program continues running. *Error handling* is the process of programmatically anticipating and addressing errors. In JavaScript, we handle errors using the keywords `try` and `catch`. We `try` to move the soup to the table, making sure there’s someone or something nearby to `catch` the soup in case we drop it.

In this lesson we’ll learn more about errors and how to create a backup plan to allow our program to continue running. When you’re ready, let’s *try* to get a *handle* on these JavaScript errors!

---

**LEARN JAVASCRIPT: ERROR HANDLING**

## **Error Handling Review**

Great job with handling errors!

In this lesson we went over:

- How mistakes in programming leads to errors.
- Why errors are useful for developers.
- Errors will prevent a program from executing unless it is handled.
- How to create an error using the `Error()` function.
- How to throw an error object using the `throw` keyword.
- How to use the `try...catch` statement to handle thrown errors.
- Evaluating code in a `try` block to anticipate errors.
- Catching the error in a `catch` block to allow our program to continue running.
- Why the `try...catch` statement would be useful in a program.

Now you have the ability to create code that doesn’t break when an error is thrown!