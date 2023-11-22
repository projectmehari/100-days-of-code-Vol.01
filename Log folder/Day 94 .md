# Day 94

Tags: Typescript
Date: November 16, 2023
Status: Done

**Tasks of the day**

- TypeScript Types
    - Other Types
    - Assertions
- Type Inference
- Type Compatibility
- Combining Types
    - Union Types
    - Intersection Types
    - Type Aliases
    - keyof operator
- Type guards / Narrowing
    - Equality
    - Truthiness
    - Type Predicates
    - typeof
    - instanceof
    
    TypeScript Functions
    
    - Typing Functions
    - Functions Overloading
    
    ---
    
    ### Other Types
    
    **Any**
    
    TypeScript has a special type, **`any`**, that you can use whenever you don’t want a particular value to cause typechecking errors.
    
    When a value is of type **`any`**, you can access any properties of it (which will in turn be of type **`any`**), call it like a function, assign it to (or from) a value of any type, or pretty much anything else that’s syntactically legal:
    
    ```tsx
    let obj: any = { x: 0 };
    obj.foo();
    obj();
    obj.bar = 100;
    obj = 'hello';
    const n: number = obj;
    ```
    
    **Object**
    
    To define an **`object`** type, we simply list its properties and their types.
    
    For example, here’s a function that takes a point-like object:
    
    ```tsx
    // The parameter's type annotation is an object type
    function printCoord(pt: { x: number; y: number }) {
      console.log("The coordinate's x value is " + pt.x);
      console.log("The coordinate's y value is " + pt.y);
    }
    
    printCoord({ x: 3, y: 7 });
    ```
    
    **Unknown**
    
    `unknown` is the type-safe counterpart of any. Anything is assignable to `unknown`, but `unknown` isn’t assignable to anything but itself and `any` without a type assertion or a control flow based narrowing. Likewise, no operations are permitted on an `unknown` without first asserting or narrowing to a more specific type.
    
    ```tsx
    function f1(a: any) {
      a.b(); // OK
    }
    
    function f2(a: unknown) {
      // Error: Property 'b' does not exist on type 'unknown'.
      a.b();
    }
    ```
    
    **Never**
    
    The **`never`** type represents the type of values that never occur. For instance, **`never`** is the return type for a function expression or an arrow function expression that always throws an exception or one that never returns. Variables also acquire the type never when narrowed by any type guards that can never be **`true`**.
    
    The never type is a subtype of, and assignable to, every type; however, no type is a subtype of, or assignable to, **`never`** (except **`never`** itself). Even any isn’t assignable to **`never`**.
    
    Examples of functions returning never:
    
    ```tsx
    // Function returning never must not have a reachable end point
    function error(message: string): never {
      throw new Error(message);
    }
    
    // Inferred return type is never
    function fail() {
      return error('Something failed');
    }
    
    // Function returning never must not have a reachable end point
    function infiniteLoop(): never {
      while (true) {}
    }
    ```
    

### Assertions

**As Const**

`as const` is a type assertion in TypeScript that allows you to assert that an expression has a specific type, and that its value should be treated as a read-only value.

**For example:**

```tsx
const colors = ['red', 'green', 'blue'] as const;

// colors is now of type readonly ['red', 'green', 'blue']
```

Using as const allows TypeScript to infer more accurate types for constants, which can lead to improved type checking and better type inference in your code.

**As [type]**

as is a type assertion in TypeScript that allows you to tell the compiler to treat a value as a specific type, regardless of its inferred type.

**For example:**

```tsx
let num = 42;
let str = num as string;

// str is now of type string, even though num is a number
```

It’s important to note that type assertions do not change the runtime type of a value, and do not cause any type of conversion. They simply provide a way for the programmer to override the type inference performed by the compiler.

**As Any**

`any` is a special type in TypeScript that represents a value of any type. When a value is declared with the any type, the compiler will not perform any type checks or type inference on that value.

For example:

```tsx
let anyValue: any = 42;

// we can assign any value to anyValue, regardless of its type
anyValue = 'Hello, world!';
anyValue = true;
```

**Non Null Assertion**

The non-null assertion operator (!) is a type assertion in TypeScript that allows you to tell the compiler that a value will never be null or undefined.

```tsx
let name: string | null = null;

// we use the non-null assertion operator to tell the compiler that name will never be null
let nameLength = name!.length;
```

The non-null assertion operator is used to assert that a value is not null or undefined, and to tell the compiler to treat the value as non-nullable. However, it’s important to be careful when using the non-null assertion operator, as it can lead to runtime errors if the value is actually **`null`** or **`undefined`**.

**satisfies Keyword**

TypeScript developers are often faced with a dilemma: we want to ensure that some expression matches some type, but also want to keep the most specific type of that expression for inference purposes.

**For example:**

```tsx
// Each property can be a string or an RGB tuple.
const palette = {
  red: [255, 0, 0],
  green: '#00ff00',
  bleu: [0, 0, 255],
  //  ^^^^ sacrebleu - we've made a typo!
};

// We want to be able to use array methods on 'red'...
const redComponent = palette.red.at(0);

// or string methods on 'green'...
const greenNormalized = palette.green.toUpperCase();
```

Notice that we’ve written **`bleu`**, whereas we probably should have written **`blue`**. We could try to catch that **`bleu`** typo by using a type annotation on palette, but we’d lose the information about each property.

```tsx
type Colors = 'red' | 'green' | 'blue';
type RGB = [red: number, green: number, blue: number];

const palette: Record<Colors, string | RGB> = {
  red: [255, 0, 0],
  green: '#00ff00',
  bleu: [0, 0, 255],
  //  ~~~~ The typo is now correctly detected
};
// But we now have an undesirable error here - 'palette.red' "could" be a string.
const redComponent = palette.red.at(0);
```

The **`satisfies`** operator lets us validate that the type of an expression matches some type, without changing the resulting type of that expression. As an example, we could use **`satisfies`** to validate that all the properties of palette are compatible with **`string | number[]`**:

```tsx
type Colors = 'red' | 'green' | 'blue';
type RGB = [red: number, green: number, blue: number];

const palette = {
  red: [255, 0, 0],
  green: '#00ff00',
  bleu: [0, 0, 255],
  //  ~~~~ The typo is now caught!
} satisfies Record<Colors, string | RGB>;

// Both of these methods are still accessible!
const redComponent = palette.red.at(0);
const greenNormalized = palette.green.toUpperCase();
```

---

### Type Inference

Type inference in TypeScript refers to the process of automatically determining the type of a variable based on the value assigned to it. This allows you to write code that is more concise and easier to understand, as the TypeScript compiler can deduce the types of variables without you having to explicitly specify them.

Here’s an example of type inference in TypeScript:

```tsx
let name = 'John Doe';
```

In this example, the TypeScript compiler automatically infers that the type of the name variable is string. This means that you can use the name variable just like any other string in your code, and the TypeScript compiler will ensure that you don’t perform any invalid operations on it.

---

### Type Compatibility

TypeScript uses structural typing to determine type compatibility. This means that two types are considered compatible if they have the same structure, regardless of their names.

Here’s an example of type compatibility in TypeScript:

```tsx
interface Point {
  x: number;
  y: number;
}

let p1: Point = { x: 10, y: 20 };
let p2: { x: number; y: number } = p1;

console.log(p2.x); // Output: 10
```

In this example, `p1` has the type `Point`, while `p2` has the type `{ x: number; y: number }`. Despite the fact that the two types have different names, they are considered compatible because they have the same structure. This means that you can assign a value of type `Point`to a variable of type `{ x: number; y: number }`, as we do with `p1`and `p2` in this example.

## **Combining Types**

In TypeScript, you can combine types using type union and type intersection.

### **Type Union:**

The union operator **`|`** is used to combine two or more types into a single type that represents all the possible types. For example:

```tsx
type stringOrNumber = string | number;
let value: stringOrNumber = 'hello';

value = 42;
```

### **Type Intersection:**

The intersection operator **`&`** is used to intersect two or more types into a single type that represents the properties of all the types. For example:

```tsx
interface A {
  a: string;
}

interface B {
  b: number;
}

type AB = A & B;
let value: AB = { a: 'hello', b: 42 };
```

### Type Aliases

A Type Alias in TypeScript allows you to create a new name for a type.
Here’s an example:

```tsx
type Name = string;
type Age = number;
type User = { name: Name; age: Age };

const user: User = { name: 'John', age: 30 };
```

In the example above, `Name` and `Age` are type aliases for `string`and `number` respectively. And `User` is a type alias for an object with properties `name` of type `Name` and `age` of type `Age`.

### keyof operator

The `keyof` operator in TypeScript is used to get the union of keys from an object type. Here’s an example of how it can be used:

```tsx
interface User {
  name: string;
  age: number;
  location: string;
}

type UserKeys = keyof User; // "name" | "age" | "location"
const key: UserKeys = 'name';
```

In this example, **`UserKeys`** is a type that represents the union of keys from the **`User`** interface, which is **`"name"`** | **`"age"`** | **`"location"`**. And a constant named **`key`** with the type **`UserKeys`** is declared with the value **`"name"`**.

---

### Type Guards / Narrowing

**typeof Operator**

The **`typeof`** operator is used to check the type of a variable. It returns a string value representing the type of the variable.

```tsx
let value: string | number = 'hello';

if (typeof value === 'string') {
  console.log('value is a string');
} else {
  console.log('value is a number');
}
```

**Instanceof**

The **`instanceof`** operator is a way to narrow down the type of a variable. It is used to check if an object is an instance of a class.

```tsx
class Bird {
  fly() {
    console.log('flying...');
  }
  layEggs() {
    console.log('laying eggs...');
  }
}

const pet = new Bird();

// instanceof
if (pet instanceof Bird) {
  pet.fly();
} else {
  console.log('pet is not a bird');
}
```

**Equality**

TypeScript also uses switch statements and equality checks like **`===`**, **`!==`**, **`==`**, and **`!=`** to narrow types. 

For example:

```tsx
function example(x: string | number, y: string | boolean) {
  if (x === y) {
    // We can now call any 'string' method on 'x' or 'y'.
    x.toUpperCase();
    y.toLowerCase();
  } else {
    console.log(x);
    console.log(y);
  }
}
```

When we checked that **`x`** and **`y`** are both equal in the above example, TypeScript knew their types also had to be equal. Since string is the only common type that both **`x`** and **`y`** could take on, TypeScript knows that **`x`** and **`y`** must be a string in the first branch.

**Truthiness**

Truthiness might not be a word you’ll find in the dictionary, but it’s very much something you’ll hear about in JavaScript.

In JavaScript, we can use any expression in conditionals, **`&&`**s, **`||`**s, **`if`** statements, Boolean negations (**`!`**), and more. As an example, if statements don’t expect their condition to always have the type boolean.

```tsx
function getUsersOnlineMessage(numUsersOnline: number) {
  if (numUsersOnline) {
    return `There are ${numUsersOnline} online now!`;
  }

  return "Nobody's here. :(";
}
```

---

### TypeScript Functions

Functions are a core building block in TypeScript. Functions allow you to wrap a piece of code and reuse it multiple times. Functions in TypeScript can be either declared using function declaration syntax or function expression syntax.

Function Declaration Syntax:

```tsx
function name(param1: type1, param2: type2, ...): returnType {
  return value;
}
```

Function Expression Syntax

```tsx
let name = function(param1: type1, param2: type2, ...): returnType {
  return value;
};
```

**Typing Functions**

In TypeScript, functions can be typed in a few different ways to indicate the input parameters and return type of the function.

Function declaration with types:

```tsx
function add(a: number, b: number): number {
  return a + b;
}
```

Arrow function with types:

```tsx
const multiply = (a: number, b: number): number => {
  return a * b;
};
```

Function type:

```tsx
let divide: (a: number, b: number) => number;

divide = (a, b) => {
  return a / b;
};
```

**Function Overloading**

Function Overloading in TypeScript allows multiple functions with the same name but with different parameters to be defined. The correct function to call is determined based on the number, type, and order of the arguments passed to the function at runtime.

```tsx
function add(a: number, b: number): number;
function add(a: string, b: string): string;

function add(a: any, b: any): any {
  return a + b;
}

console.log(add(1, 2)); // 3
console.log(add('Hello', ' World')); // "Hello World"
```