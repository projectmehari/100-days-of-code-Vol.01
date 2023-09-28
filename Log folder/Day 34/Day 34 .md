# Day 34

Tags: Javascript
Date: August 7, 2023
Status: Done

Tasks of the day

- JavaScript Syntax Part 1
- ****[How I Learned to Stop Worrying & Love Execution Sharding - Scott Sunarto](https://www.youtube.com/watch?v=A0OXif6r-Qk&list=PLJjIT2Nq6cvMk5AesMec_BwPj3Ccu1may&index=12&t=12s)****

---

[https://pitch.com/public/058f726e-d353-4151-a517-275d0def1410/734881be-37ac-4fa9-b37d-5e1b0a5e6ea3](https://pitch.com/public/058f726e-d353-4151-a517-275d0def1410/734881be-37ac-4fa9-b37d-5e1b0a5e6ea3)

**CONDITIONAL STATEMENTS**

## **What are Conditional Statements?**

In life, we make decisions based on circumstances. Think of an everyday decision as mundane as falling asleep — if we are tired, we go to bed, otherwise, we wake up and start our day.

These if-else decisions can be modeled in code by creating conditional statements. A [conditional statement](https://www.codecademy.com/resources/docs/javascript/conditionals?page_ref=catalog) checks a specific condition(s) and performs a task based on the condition(s).

In this lesson, we will explore how programs make decisions by evaluating conditions and introduce logic into our code!

We’ll be covering the following concepts:

- `if`, `else if`, and `else` statements
- comparison operators
- logical operators
- truthy vs falsy values
- ternary operators
- `switch` statement

So *if* you’re ready to learn these concepts go to the next lesson— *else*, read over the concepts, observe the diagram, and prepare yourself for this lesson!

## **Review**

Way to go! Here are some of the major concepts for conditionals:

- An `if` statement checks a condition and will execute a task if that condition evaluates to `true`.
- `if...else` statements make binary decisions and execute different code blocks based on a provided condition.
- We can add more conditions using `else if` statements.
- Comparison operators, including `<`, `>`, `<=`, `>=`, `===`, and `!==` can compare two values.
- The logical and operator, `&&`, or “and”, checks if both provided expressions are truthy.
- The logical operator `||`, or “or”, checks if either provided expression is truthy.
- The bang operator, `!`, switches the truthiness and falsiness of a value.
- The ternary operator is shorthand to simplify concise `if...else` statements.
- A `switch` statement can be used to simplify the process of writing multiple `else if` statements. The `break` keyword stops the remaining `case`s from being checked and executed in a `switch` statement.

---

**FUNCTIONS**

## **What are Functions?**

When first learning how to calculate the area of a rectangle, there’s a sequence of steps to calculate the correct answer:

1. Measure the width of the rectangle.
2. Measure the height of the rectangle.
3. Multiply the width and height of the rectangle.

With practice, you can calculate the area of the rectangle without being instructed with these three steps every time.

We can calculate the area of one rectangle with the following code:

```jsx
const width = 10;
const height = 6;
const area =  width * height;
console.log(area); // Output: 60

```

Imagine being asked to calculate the area of three different rectangles:

```jsx
// Area of the first rectangle
const width1 = 10;
const height1 = 6;
const area1 =  width1 * height1;

// Area of the second rectangle
const width2 = 4;
const height2 = 9;
const area2 =  width2 * height2;

// Area of the third rectangle
const width3 = 10;
const height3 = 10;
const area3 =  width3 * height3;

```

In programming, we often use code to perform a specific task multiple times. Instead of rewriting the same code, we can group a block of code together and associate it with one task, then we can reuse that block of code whenever we need to perform the task again. We achieve this by creating a *function*. A function is a reusable block of code that groups together a sequence of statements to perform a specific task.

In this lesson, you will learn how to create and use functions, and how they can be used to create clearer and more concise code.

---

## **Review Functions**

Give yourself a pat on the back, you just navigated through functions!

In this lesson, we covered some important concepts about functions:

- A *function* is a reusable block of code that groups together a sequence of statements to perform a specific task.
- A *function declaration* :
    
    ![https://content.codecademy.com/courses/learn-javascript-functions/Diagram/declaration.svg](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/declaration.svg)
    
- A parameter is a named variable inside a function’s block which will be assigned the value of the argument passed in when the function is invoked:
    
    ![https://content.codecademy.com/courses/learn-javascript-functions/Diagram/function_parameters.svg](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/function_parameters.svg)
    
- To *call* a function in your code:
    
    ![https://content.codecademy.com/courses/learn-javascript-functions/Diagram/name.svg](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/name.svg)
    
- ES6 introduces new ways of handling arbitrary parameters through *default parameters* which allow us to assign a default value to a parameter in case no argument is passed into the function.
- To return a value from a function, we use a *return statement*.
- To define a function using *function expressions*:
    
    ![https://content.codecademy.com/courses/learn-javascript-functions/Diagram/expression.svg](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/expression.svg)
    
- To define a function using *arrow function notation*:
    
    ![https://content.codecademy.com/courses/learn-javascript-functions/Diagram/arrow_notation.svg](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/arrow_notation.svg)
    
- Function definition can be made concise using concise arrow notation:
    
    ![https://content.codecademy.com/courses/learn-javascript-functions/Diagram/return.svg](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/return.svg)
    

It’s good to be aware of the differences between function expressions, arrow functions, and function declarations. As you program more in JavaScript, you’ll see a wide variety of how these function types are used.

---

**SCOPE**

## **Scope**

An important idea in programming is *scope*. Scope defines where variables can be accessed or referenced. While some variables can be accessed from anywhere within a program, other variables may only be available in a specific context.

You can think of scope like the view of the night sky from your window. Everyone who lives on the planet Earth is in the global scope of the stars. The stars are accessible *globally*. Meanwhile, if you live in a city, you may see the city skyline or the river. The skyline and river are only accessible *locally* in your city, but you can still see the stars that are available globally.

## **Review: Scope**

In this lesson, you learned about scope and how it impacts the accessibility of different variables.

Let’s review the following terms:

- **Scope** refers to where variables can be accessed throughout the program, and is determined by where and how they are declared.
- **Blocks** are statements that exist within curly braces `{}`.
- **Global scope** refers to the context within which variables are accessible to every part of the program.
- **Global variables** are variables that exist within global scope.
- **Block scope** refers to the context within which variables are accessible only within the block they are defined.
- **Local variables** are variables that exist within block scope.
- **Global namespace** is the space in our code that contains globally scoped information.
- **Scope pollution** is when too many variables exist in a namespace or variable names are reused.

---

### ****The Node Runtime Environment****

In 2009, the *Node runtime environment* was created for the purpose of executing JavaScript code without a browser, thus enabling programmers to create *full-stack* (front-end and back-end) applications using only the JavaScript language.

Node is an entirely different runtime environment, meaning that browser-environment data values and functions, like **`window.alert()`**, can’t be used. Instead, the Node runtime environment gives back-end applications access to a variety of features unavailable in a browser, such as access to the server’s file system, database, and network.

For example, suppose you created a file called **my-app.js**. We can check to see the directory that this file is located in using the Node runtime environment variable **`process`**:

```
// my-app.js
console.log(process.env.PWD);

```

> Notice that we are using console.log now instead of window.alert() since the window object isn’t available
> 

**`process`** is an object containing data relating to the JavaScript file being executed. **`process.env`** is an object containing environment variables such as **`process.env.PWD`** which contains the current working directory (and stands for “**P**rint **W**orking **D**irectory”).

To execute the JavaScript code in this file, first make sure that you have [set up Node on your computer](https://www.codecademy.com/articles/setting-up-node-locally). Then, open up a [terminal](https://www.codecademy.com/learn/learn-the-command-line) and run the following command:

```
$ node my-app.js
/path/to/working/directory

```

The **`node`** command tells your computer to execute the **`my-app.js`** file in the Node environment. You can also use the **`node`** command without a file argument to open up the Node **R**ead-**E**val-**P**rint-**L**oop (REPL):

```
$ node
> process.env.HOME
'/home/ccuser'

```

## **Summary**

A *runtime environment* is where your program will be executed. JavaScript code may be executed in one of two runtime environments:

1. a browser’s runtime environment
2. the Node runtime environment

In each of these environments, different data values and functions are available, and these differences help distinguish front-end applications from back-end applications.

- Front-end JavaScript applications are executed in a browser’s runtime environment and have access to the **`window`** object.
- Back-end JavaScript applications are executed in the Node runtime environment and have access to the file system, databases, and networks attached to the server.