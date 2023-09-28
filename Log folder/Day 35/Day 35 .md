# Day 35

Tags: Javascript
Date: August 8, 2023
Status: Done

Task of the day

- JavaScript Syntax Part 2
- ****[Optimism 🛠️ How to ship a dapp on OP Mainnet in less than 30 minutes - soyboy](https://www.youtube.com/watch?v=beqVxYb_fqY)****

---

### Notes

- [Optimism starter kit](https://github.com/ethereum-optimism/optimism-starter)

---

**ARRAYS**

## **Review Arrays**

Nice work! In this lesson, we learned these concepts regarding arrays:

- Arrays are lists that store data in JavaScript.
- Arrays are created with brackets `[]`.
- Each item inside of an array is at a numbered position, or index, starting at `0`.
- We can access one item in an array using its index, with syntax like: `myArray[0]`.
- We can also change an item in an array using its index, with syntax like `myArray[0] = 'new string'`;
- Arrays have a `length` property, which allows you to see how many items are in an array.
- Arrays have their own methods, including `.push()` and `.pop()`, which add and remove items from an array, respectively.
- Arrays have many methods that perform different tasks, such as `.slice()` and `.shift()`, you can find documentation at the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) website.
- Some built-in methods are mutating, meaning the method will change the array, while others are not mutating. You can always check the documentation.
- Variables that contain arrays can be declared with `let` or `const`. Even when declared with `const`, arrays are still mutable. However, a variable declared with `const` cannot be reassigned.
- Arrays mutated inside of a function will keep that change even outside the function.
- Arrays can be nested inside other arrays.
- To access elements in nested arrays chain indices using bracket notation.

---

**LOOPS**

## **The For Loop**

Instead of writing out the same code over and over, loops allow us to tell computers to repeat a given block of code on its own. One way to give computers these instructions is with a `[for`loop](https://www.codecademy.com/resources/docs/javascript/loops?page_ref=catalog).

The typical `for` loop includes an *iterator variable* that usually appears in all three expressions. The iterator variable is initialized, checked against the stopping condition, and assigned a new value on each loop iteration. Iterator variables can have any name, but it’s best practice to use a descriptive variable name.

A `for` loop contains three expressions separated by `;` inside the parentheses:

1. an *initialization* starts the loop and can also be used to declare the iterator variable.
2. a *stopping condition* is the condition that the iterator variable is evaluated against— if the condition evaluates to `true` the code block will run, and if it evaluates to `false`the code will stop.
3. an *iteration statement* is used to update the iterator variable on each loop.

The `for` loop syntax looks like this:

```jsx
for (let counter = 0; counter < 4; counter++) {
  console.log(counter);
}

```

## **Review**

Great job! In this lesson, we learned how to write cleaner code with loops. You now know:

- Loops perform repetitive actions so we don’t have to code that process manually every time.
- How to write `for` loops with an iterator variable that increments or decrements
- How to use a `for` loop to iterate through an array
- A nested `for` loop is a loop inside another loop
- `while` loops allow for different types of stopping conditions
- Stopping conditions are crucial for avoiding infinite loops.
- `do...while` loops run code at least once— only checking the stopping condition after the first execution
- The `break` keyword allows programs to leave a loop during the execution of its block

---

## **for loop vs for…of loop**

Here is an example of iterating over each element in an array using a traditional **`for`** loop with an index variable:

```jsx
const hobbies = ['singing', 'eating', 'quidditch', 'writing'];

for (let i = 0; i < hobbies.length; i++) {
  console.log(`I enjoy ${hobbies[i]}.`);
}

```

And here is an example of iterating through the same array using a **`for...of`**loop:

```jsx
const hobbies = ['singing', 'eating', 'quidditch', 'writing'];

for (const hobby of hobbies) {
  console.log(`I enjoy ${hobby}.`);
}

```

---

**OBJECTS**

## **Introduction to Objects**

It’s time to learn more about the basic structure that permeates nearly every aspect of JavaScript programming: objects.

You’re probably already more comfortable with objects than you think, because JavaScript loves objects! Many components of the language are actually objects under the hood, and even the parts that aren’t— like strings or numbers— can still act like objects in some instances.

There are only seven fundamental data types in JavaScript, and six of those are the primitive data types: string, number, boolean, null, undefined, and symbol. With the seventh type, objects, we open our code to more complex possibilities. We can use JavaScript objects to model real-world things, like a basketball, or we can use objects to build the data structures that make the web possible.

At their core, JavaScript objects are containers storing related data and functionality, but that deceptively simple task is extremely powerful in practice. You’ve been using the power of objects all along, but now it’s time to understand the mechanics of objects and start making your own!

## **Review**

Way to go! You’re well on your way to understanding the mechanics of objects in JavaScript. By building your own objects, you will have a better understanding of how JavaScript built-in objects work as well. You can also start imagining organizing your code into objects and modeling real world things in code.

Let’s review what we learned in this lesson:

- Objects store collections of *key-value* pairs.
- Each key-value pair is a property—when a property is a function it is known as a method.
- An object literal is composed of comma-separated key-value pairs surrounded by curly braces.
- You can access, add or edit a property within an object by using dot notation or bracket notation.
- We can add methods to our object literals using key-value syntax with anonymous function expressions as values or by using the new ES6 method syntax.
- We can navigate complex, nested objects by chaining operators.
- Objects are mutable—we can change their properties even when they’re declared with `const`.
- Objects are passed by reference— when we make changes to an object passed into a function, those changes are permanent.
- We can iterate through objects using the `For...in` syntax.

---

**OBJECTS**

## **Review**

Way to go! You’re well on your way to understanding the mechanics of objects in JavaScript. By building your own objects, you will have a better understanding of how JavaScript built-in objects work as well. You can also start imagining organizing your code into objects and modeling real world things in code.

Let’s review what we learned in this lesson:

- Objects store collections of *key-value* pairs.
- Each key-value pair is a property—when a property is a function it is known as a method.
- An object literal is composed of comma-separated key-value pairs surrounded by curly braces.
- You can access, add or edit a property within an object by using dot notation or bracket notation.
- We can add methods to our object literals using key-value syntax with anonymous function expressions as values or by using the new ES6 method syntax.
- We can navigate complex, nested objects by chaining operators.
- Objects are mutable—we can change their properties even when they’re declared with `const`.
- Objects are passed by reference— when we make changes to an object passed into a function, those changes are permanent.
- We can iterate through objects using the `For...in` syntax.

---

**ADVANCED OBJECTS**

## **Advanced Objects Introduction**

Remember, objects in JavaScript are containers that store data and functionality. In this lesson, we will build upon the fundamentals of creating objects and explore some advanced concepts.

So if there are no objections, let’s learn more about objects!

In this lesson we will cover these topics:

- how to use the `this` keyword.
- conveying privacy in JavaScript methods.
- defining getters and setters in objects.
- creating factory functions.
- using destructuring techniques.

## **Review**

Congratulations on finishing Advanced Objects!

Let’s review the concepts covered in this lesson:

- The object that a method belongs to is called the *calling object*.
- The `this` keyword refers to the calling object and can be used to access properties of the calling object.
- Methods do not automatically have access to other internal properties of the calling object.
- The value of `this` depends on where the `this` is being accessed from.
- We cannot use arrow functions as methods if we want to access other internal properties.
- JavaScript objects do not have built-in privacy, rather there are conventions to follow to notify other developers about the intent of the code.
- The usage of an underscore before a property name means that the original developer did not intend for that property to be directly changed.
- Setters and getter methods allow for more detailed ways of accessing and assigning properties.
- Factory functions allow us to create object instances quickly and repeatedly.
- There are different ways to use object destructuring: one way is the property value shorthand and another is destructured assignment.
- As with any concept, it is a good skill to learn how to use the documentation with objects!

You’re ready to start leveraging more elegant code for creating and accessing objects in your code!

---

## **Introduction**

We are often unaware of the number of assumptions we make when communicating in our native languages. If we told you to “count to three,” we would expect you to say the numbers “one”, “two”, and “three”. We assumed you would know to start with “one” and end with “three”. With programming, we need to be more explicit with our directions to the computer. Here’s how we might tell the computer to “count to three”:

```jsx
for (let i = 1; i <= 3; i++) {
  console.log(i);
}

```

When we speak to other humans, we share a vocabulary that provides quick ways to communicate complicated concepts. When we say the word “bake”, it calls to mind a familiar subroutine— preheating an oven, putting something into an oven for a set amount of time, and finally removing it. This allows us to *abstract* away a lot of the details and communicate key concepts more concisely. Instead of listing all those details, we can say, “We baked a cake,” and still impart all that meaning to you.

In this lesson, we’ll learn how to use “abstraction” in programming by writing functions. In addition to allowing us to reuse our code, functions help to make clear, readable programs. If you encounter `countToThree()` in a program, you might be able to quickly guess what the function does without having to stop and read the function’s body.

We’re also going to learn about a way to add another level of abstraction to our programming: *higher-order functions*. *Higher-order functions* are functions that accept other functions as arguments and/or return functions as output. This enables us to build abstractions on other abstractions, just like “We hosted a birthday party” is an abstraction that may build on the abstraction “We made a cake.”

---

**HIGHER-ORDER FUNCTIONS**

## **Review**

Great job! By thinking about functions as data, and learning about higher-order functions, you’ve taken important steps in learning to write clean, modular code that takes advantage of JavaScript’s flexibility.

Let’s review what we learned in this lesson:

- Abstraction allows us to write complicated code in a way that’s easy to reuse, debug, and understand for human readers.
- We can work with functions the same way we work with any other type of data, including reassigning them to new variables.
- JavaScript functions are first-class objects, so they have properties and methods like any other object.
- Functions can be passed into other functions as parameters.
- A higher-order function is a function that either accepts functions as parameters, returns a function, or both.

---

**ITERATORS**

## **Introduction to Iterators**

Imagine you had a grocery list and you wanted to know what each item on the list was. You’d have to scan through each row and check for the item. This common task is similar to what we have to do when we want to iterate over, or loop through, an array. One tool at our disposal is the `for` loop. However, we also have access to built-in array methods which make looping easier.

The built-in JavaScript array methods that help us iterate are called *iteration methods*, at times referred to as *iterators*. Iterators are methods called on arrays to manipulate elements and return values.

In this lesson, you will learn the syntax for these methods, their return values, how to use the documentation to understand them, and how to choose the right iterator method for a given task.

## **Review**

Awesome job on clearing the iterators lesson! You have learned a number of useful methods in this lesson as well as how to use the JavaScript documentation from the Mozilla Developer Network to discover and understand additional methods. Let’s review!

- `.forEach()` is used to execute the same code on every element in an array but does not change the array and returns `undefined`.
- `.map()` executes the same code on every element in an array and returns a new array with the updated elements.
- `.filter()` checks every element in an array to see if it meets certain criteria and returns a new array with the elements that return truthy for the criteria.
- `.findIndex()` returns the index of the first element of an array that satisfies a condition in the callback function. It returns `1` if none of the elements in the array satisfies the condition.
- `.reduce()` iterates through an array and takes the values of the elements and returns a single value.
- All iterator methods take a callback function, which can be a pre-defined function, a function expression, or an arrow function.
- You can visit the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) to learn more about iterator methods (and all other parts of JavaScript!)