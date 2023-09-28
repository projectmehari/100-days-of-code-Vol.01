# Day 50

Tags: Typescript
Date: September 3, 2023
Status: Done

Task of the day 

- TypeScript
    - Fundamentals
    - Functions
    - Custom types
    - Unions
    - Type narrowing
    - Object Types

---

### TypeScript introduction

[Learn TypeScript: Fundamentals | Codecademy](https://www.codecademy.com/learn/learn-typescript-fundamentals)

### **What is TypeScript?**

So now that we know *why* TypeScript exists, let’s talk about how we use it:

- First, we write TypeScript code in files with the extension **.ts**.
- Next, we run our code through the TypeScript [transpiler](https://en.wikipedia.org/wiki/Source-to-source_compiler). The transpiler will check that the code adheres to TypeScript’s standards, and it will display errors when it does not.
- If the TypeScript code can be converted into working JavaScript, the transpiler will output a JavaScript version of the file (**.js**).

TypeScript code is a *super set* of JavaScript code—it has all the features of traditional JavaScript but adds some new features.

### **Type Inferences**

JavaScript allows us to assign any value to any variable. That makes it very flexible to use, which can be good for getting started quickly in coding. In practice, variables that are assigned values of multiple types throughout a program can be very confusing or lead to bugs.

One of the first things we’ll discover with TypeScript is that when we declare a variable with an initial value, the variable can never be reassigned a value of a different data type. This is an example of *type inference*: everywhere in our program, TypeScript expects the data type of the variable to match the type of the value initially assigned to it at declaration.

### **Type Shapes**

Because TypeScript knows what *types* our objects are, it also knows what *shapes* our objects adhere to. An object’s shape describes, among other things, what properties and methods it does or doesn’t contain.

The built-in types in JavaScript each have known properties and methods that always exist. All `string`s, for example, are known to have a `.length` property and `.toLowerCase()`method.

### **Review**

All right! You’ve taken some first steps into the wonderful world of type safety with TypeScript. 💪

To recap, you’ve learned:

- *TypeScript* is a superset of JavaScript that adds types.
- The *type system* refers to TypeScript’s understanding of how your code is meant to function: mainly what data types should be stored under your variables.
- TypeScript expects the data type of the variable to match the type of the value initially assigned to it at its declaration—this is known as *type inference*.
- An object’s *shape* describes, among other things, what properties and methods it does or doesn’t contain. TypeScript knows not only what type something is but also what shape that type has.
- When it isn’t able to infer a type, TypeScript will consider a variable to be of type `any`.
- *Type annotations* are little pieces of code that indicate what type a variable is meant to be.

---

# **The tsconfig.json File**

**Let’s explore what the tsconfig.json file is for.**

TypeScript features are extremely useful: for one, it allows us to add types to regular JavaScript code. It also checks for syntax errors even before run time. It even provides tooltips that show you why some code might throw an error. There are so many great features that come by default. Even with all these great features, TypeScript recognizes the need for flexibility.

Sometimes, you don’t want all the [default rules](https://www.typescriptlang.org/docs/handbook/compiler-options.html) that TypeScript is trying to enforce — and that’s fine. That’s one reason why providing a **tsconfig.json** file is useful. Additionally, you get perks like telling the TypeScript compiler what files to run on and more! So, let’s explore what this file looks like and how it helps.

---

### Typescript Functions

### **Review**

We learned all about how to use TypeScript to specify the types of function parameters and return types. Now we know how to:

- Give type annotations to function parameters.
- Deal with type annotations for optional parameters, which may have default values.
- Understand how TypeScript determines the return type of a function.
- Explicitly specify return types for functions, including for functions that don’t return anything.
- Use the above skills to diagnose and fix bugs in our code.

Great job!

---

### Functions Arrays

Beautiful! Array types may seem like a monster topic, but now you’ve got it tamed. You learned:

- The type annotations for arrays.
- What tuples are, and how to do their type annotations.
- How type inference works with arrays and tuples.
- How to use the rest and spread operators with TypeScript.

Arrays types are a crucial component of TypeScript, so great job!

---

### Custom types

### **Enums**

Our first example of a complex type is also one of the most useful: *enums*. We use enums when we’d like to **enum**erate all the possible values that a variable could have. This is in contrast to most of the other types we have studied. A variable of the `string` type can have any string as a value; there are infinitely many possible strings, and it would be impossible to list them all. Similarly, a variable of the `boolean[]` type can have any array of booleans as its value; again, the possibilities are infinite.

```tsx
enum Direction {
  North,
  South,
  East,
  West
}
```

### **Review**

Upon completion of this lesson you have officially* become a TypeScript Hero. No longer are you limited to TypeScript’s pre-defined types; you have now learned how to create your own custom types! These include:

- Enums (both string and numeric)
- Object types
- Function types

Furthermore, you learned how to refer to complex types using type aliases. And you even learned to master generics, which are like doubly-custom types. Impressive!

---

### **Union types**

TypeScript lets us type variables with different levels of *type specificity*. If we want to enforce that a variable is a `string`, we can type it as a `string`. This type is very specific since TypeScript will only allow the variable to have a string value.

On the other end of the specificity spectrum, we could type a variable as `any`. This type is very unspecific. TypeScript will allow a value of any type to be assigned without complaining and throwing an error.

These two levels of type specificity work for many parts of our programs. However, sometimes we need to strike a balance between extreme specificity and being totally unspecific with our types. Imagine that we have to write a program that takes in an employee’s ID, then prints the ID to the console. The catch is that an employee’s ID could be a string or a number. Since we need our ID variable to allow more than one type, we could use an `any` type, like this:

```tsx
let ID: any;

console.log(`The ID is ${ID}.`);

```

The problem with the `any` type is that any value might not work with our program. To solve this problem, TypeScript allows us to be flexible with how specific our types are by combining different types. When we combine types, it is called a *union*.

![Screen Shot 2023-09-03 at 4.00.42 PM.png](Day%2050%2004cab4d749a649f38d31f24ca4d88237/Screen_Shot_2023-09-03_at_4.00.42_PM.png)

### **Review Unions**

🙌 Way to go! We’ve learned a variety of ways to create types that are as specific as we need with unions. To recap, we’ve learned:

- We can combine multiple types with a vertical bar character `|`. This is the syntax for defining a *union*. Each type in a union is called a *type member*.
- We can narrow down what methods and properties are available in a program with *type narrowing*. Type narrowing allows us to type a variable as a union, then narrow down the union with a *type guard* to call type member specific methods and properties.
- If a function can return multiple types, TypeScript will infer all possible return types as a union.
- We can use unions to allow arrays to have multiple types of values.
- To call a method or property on a variable typed as a union, we can only call methods or properties that are identical on all members of the union.
- We can define states within our program by using literal types and unions.

---

### **Type Narrowing**

When compiling TypeScript code to JavaScript, the compiler will throw any errors related to variable types. This process of compilation involves giving the TypeScript compiler the information it needs to perform type checks. Therefore, when we give our variables specific types, these types are reinforced by the compiler/TypeScript.

If TypeScript could only check types at compile-time, that would still be useful, but it turns out that TypeScript can do so much more. TypeScript has the ability to evaluate how our runtime code will perform, and then infer variable types for us. When the compiler notices an error, it will complain when running `tsc` and also by showing a red squiggly line below the code in the editor.

Evaluating runtime code can be really useful when our programs have variables of multiple types. In the case of unions, TypeScript can hone in on a more narrow type by evaluating our runtime code. For example:

```tsx
function formatDate(date: string | number) {
  // date can be a number or string here

  if (typeof date === 'string') {
    // date must be a string here
  }
}

```

In the example above, the `date` parameter has a union type of `string | number`. Inside the body of `formatDate()`, there’s a conditional that checks if `date` is a `'string'`. If the condition is met, then TypeScript can infer that `date` must be a `string`type within the conditional. It will allow us to call methods and properties that are allowed on `string` types. This is called *type narrowing*. Type narrowing is when TypeScript can infer more specific types based on the variable’s surrounding code.

### **Review Type Narrowing**

You’re the *type* of person that finishes lessons! Nice work on completing Type Narrowing. You’re now equipped to utilize TypeScript’s powers of inference through type guards and type narrowing. Let’s review what we learned:

- TypeScript can understand how our code will execute at runtime so that it can infer more specific types while we write code. This is called *type narrowing*.
- An expression that checks if a variable is a specific type is called a *type guard*. Type guard’s allow TypeScript to recognize when it can type narrow.
- The `typeof` operator is useful when writing type guards. It can check if a variable is a `'string'`, `'number'`, `'boolean'`, or `'symbol'`.
- The `in` operator is useful for checking if a specific property exists on an object. `in` is especially helpful when we have data represented as objects.
- TypeScript can type narrow after a type guard with an `else`block. TypeScript understands that the `else` block of an `if` statement must be the inverse condition of the `if`statement’s conditional.
- TypeScript can go even further and type narrow after a type guard if the type guard has a `return` or another terminal statement within its block, no `else` required.

---

**ADVANCED OBJECT TYPES**

### **Review**

🙌 Way to go! You have *advanced* through this entire lesson. No one will *object* to your superior TypeScript knowledge. Here’s an overview of what we learned:

- We can use both `interface` and `type` keywords to declare types.
- `interface` is great for typing objects, especially within object-oriented programs.
- We can apply an `interface` on a `class` using the `implements` keyword.
- Object types can be nested infinitely.
- We can define multiple types and compose them together to organize our code and make it more flexible.
- We can copy the type members of one `interface` into another using the `extends` keyword.
- We can define variable property names within an object type with an *index signature*. An index signature uses syntax like: `[propertyName: string]: string`.
- It’s possible to make some type members optional, using the `?` operator. The syntax looks like `name?: string`.

Use the code editor to polish your understanding of typing objects in TypeScript.