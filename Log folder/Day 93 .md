# Day 93

Tags: Typescript
Date: November 15, 2023
Status: Done

Tasks of the day 

- Introduction
- Running Typescript
    - tsc
    - ts-node
    - TS Playground
- TypeScript vs Javascript
- TS and JS Interoperability
- Installation and Configuration
    - tsconfig.json
    - Compiler options
- Typescript Types
    - Primitives
    - Objects

---

### Introduction

TypeScript is a statically-typed programming language that is a superset of JavaScript. It was developed and is maintained by Microsoft. TypeScript was created to address the challenges of building large-scale JavaScript applications and adds optional type annotations, classes, interfaces, and other features to the language.

The main benefits of using TypeScript include:

- Type Safety
- Improved Tooling
- Improved Maintainability
- Backwards Compatibility

Learn more from the folowing links:

- **[Overview of TypeScript](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html)**
- **[TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html)**
- **[What Is TypeScript?](https://thenewstack.io/what-is-typescript/)**
- **[Video: Where TypeScript Excels](https://youtu.be/BUo7B6UuoJ4)**

---

### Running Typescript

To run TypeScript code, you’ll need to have a TypeScript compiler installed. Here’s a general process to run TypeScript code:

- Write TypeScript code in a `.ts` file (e.g. `app.ts`)
- Compile the TypeScript code into JavaScript using the TypeScript compiler:

```tsx
tsc app.ts
```

- Run the generated JavaScript code using a JavaScript runtime environment such as Node.js:

```tsx
node app.js
```

Learn more from the following link:

- **[Running your TypeScript](https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html)**

---

### tsc

**`tsc`** is the command line tool for the TypeScript compiler. It compiles TypeScript code into JavaScript code, making it compatible with the browser or any JavaScript runtime environment.

You can use the **`tsc`** command to compile your TypeScript code by running the following command in your terminal or command prompt:

```
tsc
```

This command will compile all TypeScript files in your project that are specified in your **`tsconfig.json`** file. If you want to compile a specific TypeScript file, you can specify the file name after the **`tsc`** command, like this:

```
tsc index.ts
```

The **`tsc`** command has several options and flags that you can use to customize the compilation process. For example, you can use the **`--target`** option to specify the version of JavaScript to compile to, or the **`--outDir`** option to specify the output directory for the compiled JavaScript files.

You can run **`tsc --help`** to see a list of all the available options and flags.

Learn more from the following links:

- **[tsc CLI Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html#using-the-cli)**

---

### ts-node

ts-node is a TypeScript execution and REPL for node.js, with source map and native ESM support. Learn more from the following links:

- **[ts-node - GitHub Project](https://github.com/TypeStrong/ts-node)**
- **[How To Run TypeScript Scripts with ts-node](https://www.digitalocean.com/community/tutorials/typescript-running-typescript-ts-node)**

---

### TS Playground

The TypeScript Playground is a great tool to learn TypeScript. It allows you to write TypeScript code and see the JavaScript output. It also allows you to share your code with others.

Learn more from the following links:

- **[TypeScript - Playground](https://www.typescriptlang.org/play)**

---

### TypeScript vs JavaScript

TypeScript is a superset of JavaScript that adds optional type annotations and other features such as interfaces, classes, and namespaces. JavaScript is a dynamically-typed language that is primarily used for client-side web development and can also be used for server-side development.

Here are a few key differences between TypeScript and JavaScript:

- **Types**: TypeScript has optional type annotations while JavaScript is dynamically-typed. This means that in TypeScript, you can specify the data type of variables, parameters, and return values, which can help catch type-related errors at compile-time.
- **Syntax**: TypeScript extends JavaScript syntax with features like interfaces, classes, and namespaces. This provides a more robust and organized structure for large-scale projects.
- **Tooling**: TypeScript has better tooling support, such as better editor integration, type checking, and code refactoring.
- **Backwards Compatibility**: TypeScript is fully compatible with existing JavaScript code, which means you can use TypeScript in any JavaScript environment.

Learn more from the following links:

- **[Learning JavaScript and TypeScript](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html#learning-javascript-and-typescript)**
- **[TypeScript vs. JavaScript](https://thenewstack.io/typescript-vs-javascript/)**

---

### TS/JS Interoperability

TypeScript and JavaScript have full interoperability, meaning you can use TypeScript code in JavaScript projects and vice versa. TypeScript is a superset of JavaScript, which means that any valid JavaScript code is also valid TypeScript code.
You can use JavaScript libraries in TypeScript projects by either including the JavaScript files directly or using type definitions for the library. Type definitions provide type information for JavaScript libraries, making it easier to use them in TypeScript.
On the other hand, you can use TypeScript code in JavaScript projects by simply compiling the TypeScript code into JavaScript. The generated JavaScript code can be used in any JavaScript environment, and it will work the same way as regular JavaScript code.

---

# **Install and Configure**

To install and configure TypeScript in your project, you need to perform the following steps:

- Initialize npm in your project directory by running the following command:

```jsx
npm init
```

- Install TypeScript as a project dependency by running the following command:

```jsx
npm install --save-dev typescript
```

- Create a `tsconfig.json` file in your project directory to specify the compiler options for building your project. For example:

```jsx
{  "compilerOptions": {   
 "target": "es5",   
 "module": "commonjs", 
   "strict": true, 
   "outDir": "./dist",  
  "rootDir": "./src"  
}, 
 "exclude": ["node_modules"]
}
```

- Compile your TypeScript code using the following command:

```jsx
tsc
```

Note: You can also compile individual TypeScript files by specifying the file name after the tsc command.For example:

```jsx
tsc index.ts
```

And you’re all set! You can now start writing TypeScript code in your project.

Learn more from the following links:

- **[Install and Configure TypeScript](https://www.typescriptlang.org/download)**
- **[TypeScript Getting Started](https://thenewstack.io/typescript-tutorial-a-guide-to-using-the-programming-language/)**

---

### Tsconfig.json

tsconfig.json is a configuration file in TypeScript that specifies the compiler options for building your project. It helps the TypeScript compiler understand the structure of your project and how it should be compiled to JavaScript. Some common options include:

- `target`: the version of JavaScript to compile to.
- `module`: the module system to use.
- `strict`: enables/disables strict type checking.
- `outDir`: the directory to output the compiled JavaScript files.
- `rootDir`: the root directory of the TypeScript files.
- `include`: an array of file/directory patterns to include in the compilation.
- `exclude`: an array of file/directory patterns to exclude from the compilation.

Given below is the sample **`tsconfig.json`** file:

```tsx
{  "compilerOptions": {  
  "target": "es5",   
 "module": "commonjs", 
   "strict": true,   
 "outDir": "./dist",   
 "rootDir": "./src",  }, 
 "exclude": ["node_modules"], 
 "include": ["src"]
}
```

Learn more from the following links:

- **[What is a tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#handbook-content)**

---

### Compiler Options

TypeScript compiler accepts a number of command line options that allow you to customize the compilation process. These options can be passed to the compiler using the **`--`** prefix, for example:

```tsx
tsc --target ES5 --module commonjs
```

---

### TypeScript Types

TypeScript has several built-in types, including:

**Primitives**

1. **Number**

It is a primitive data type in TypeScript that represents numeric values. It includes both integer and floating-point values.

```tsx
let intValue: number = 42;let floatValue: number = 3.14;
```

1. **String**

It is a primitive data type in TypeScript that represents textual data. It is a set of elements of the 16-bit Unicode character set.

```tsx
let name: string = 'John Doe';
```

1. **Boolean**

**`boolean`** is a primitive data type in TypeScript that represents a boolean value i.e. either true or false. Given below is an example of a boolean variable declaration:

```tsx
let isTrue: boolean = true;let isFalse: boolean = false;
```

4. **Undefined**

JavaScript has two primitive values used to signal absent or uninitialized value: **`null`** (absent) and **`undefined`** (unintialized).

TypeScript has two corresponding *types* by the same names. How these types behave depends on whether you have the **`strictNullChecks`**option on.

With **`strictNullChecks`** off, values that might be **`null`** or **`undefined`** can still be accessed normally, and the values **`null`** and **`undefined`** can be assigned to a property of any type. This is similar to how languages without **`null`** checks (e.g. C#, Java) behave. The lack of checking for these values tends to be a major source of bugs; TypeScript always recommend people turn **`strictNullChecks`** on if it’s practical to do so in the codebase.

With **`strictNullChecks`** on, when a value is **`null`** or **`undefined`**, you will need to test for those values before using methods or properties on that value. Just like checking for **`undefined`** before using an optional property, we can use narrowing to check for values that might be **`null`**:

```tsx
function doSomething(x: string | null) { 
 if (x === null) {  
  // do nothing 
 } else { 
   console.log('Hello, ' + x.toUpperCase());  
}
}
```

1. **Void**

**`void`** represents the return value of functions which don’t return a value. It’s the inferred type any time a function doesn’t have any **`return`**statements, or doesn’t return any explicit value from those return statements:

```tsx
// The inferred return type is void
function noop() {
  return;
}
```

In JavaScript, a function that doesn’t return any value will implicitly return the value **`undefined`**. However, **`void`** and **`undefined`** are not the same thing in TypeScript.

1. **Null**

JavaScript has two primitive values used to signal absent or uninitialized value: **`null`** (absent) and **`undefined`** (unintialized).

TypeScript has two corresponding *types* by the same names. How these types behave depends on whether you have the **`strictNullChecks`**option on.

With **`strictNullChecks`** off, values that might be **`null`** or **`undefined`** can still be accessed normally, and the values **`null`** and **`undefined`** can be assigned to a property of any type. This is similar to how languages without **`null`** checks (e.g. C#, Java) behave. The lack of checking for these values tends to be a major source of bugs; TypeScript always recommend people turn **`strictNullChecks`** on if it’s practical to do so in the codebase.

With **`strictNullChecks`** on, when a value is **`null`** or **`undefined`**, you will need to test for those values before using methods or properties on that value. Just like checking for **`undefined`** before using an optional property, we can use narrowing to check for values that might be **`null`**:

```tsx
function doSomething(x: string | null) { 
 if (x === null) {  
  // do nothing  
} else {   
 console.log('Hello, ' + x.toUpperCase()); 
 }
}
```

**Object Types**

1. **Interface**
TypeScript allows you to specifically type an object using an interface that can be reused by multiple objects.

```tsx
interface Person {
  name: string; 
 age: number;
}

function greet(person: Person) { 
 return 'Hello ' + person.name;
}
```

1. **Class**

In TypeScript, a class is a blueprint for creating objects with specific properties and methods. Classes are a fundamental concept in object-oriented programming. Here is an example of a simple class in TypeScript:

```tsx
class Car {
  make: string;
  model: string;
  year: number;

  constructor(make: string, model: string, year: number) {
    this.make = make;
    this.model = model;
    this.year = year;
  }

  drive() {
    console.log(`Driving my ${this.year} ${this.make} ${this.model}`);
  }
}
```

1. **Enum**
Enums is not a type-level extension of JavaScript. It allow a developer to define a set of named constants. Using enums can make it easier to document intent, or create a set of distinct cases. TypeScript provides both numeric and string-based enums.
    
    Here is an example of a numeric enum in TypeScript:
    

```tsx
enum Direction {
  Up = 1,
  Down,
  Left,
  Right,
}
```

Above, we have a numeric enum where **`Up`** is initialized with **`1`**. All of the following members are auto-incremented from that point on. In other words, **`Direction.Up`** has the value **`1`**, **`Down`** has **`2`**, **`Left`** has **`3`**, and **`Right`** has **`4`**.

If we left off the initializer for **`Up`**, it would have the value **`0`** and the rest of the members would be auto-incremented from there.

1. **Arrays**
To specify the type of an array like **`[1, 2, 3]`**, you can use the syntax **`number[]`**; this syntax works for any type (e.g. **`string[]`** is an array of strings, and so on). You may also see this written as **`Array<number>`**, which means the same thing.

```tsx
const numbers: number[] = [1, 2, 3];
```

1. **Tuples**
A tuple type is another sort of Array type that knows exactly how many elements it contains, and exactly which types it contains at specific positions.

```tsx
type StringNumberPair = [string, number];

const pair: StringNumberPair = ['hello', 42];

const first = pair[0];
const second = pair[1];

// Error: Index out of bounds
const third = pair[2];
```

---