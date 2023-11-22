# Day 96

Tags: Typescript
Date: November 18, 2023
Status: Done

Tasks of the day

- Utility types
- Advanced Types
- TypeScript Modules
- Ecosystem

---

### Utility Types

TypeScript provides several utility types that can be used to manipulate and transform existing types. Here are some of the most common ones:

**Partial** 

The Partial type in TypeScript allows you to make all properties of a type optional. This is useful when you need to create an object with only a subset of the properties of an existing type.

Here’s an example of using the Partial type in TypeScript:

```tsx
interface User {
  name: string;
  age: number;
  email: string;
}

function createUser(user: Partial<User>): User {
  return {
    name: 'John Doe',
    age: 30,
    email: 'john.doe@example.com',
    ...user,
  };
}

const newUser = createUser({ name: 'Jane Doe' });

console.log(newUser);
// Output: { name: 'Jane Doe', age: 30, email: 'john.doe@example.com' }
```

**Pick**

Pick constructs a type by picking the set of properties Keys (string literal or union of string literals) from Type.

```tsx
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

type TodoPreview = Pick<Todo, 'title' | 'completed'>;

const todo: TodoPreview = {
  title: 'Clean room',
  completed: false,
};
```

**Omit**

Omit constructs a type by picking all properties from Type and then removing Keys (string literal or union of string literals).

```tsx
interface Todo {
  title: string;
  description: string;
  completed: boolean;
  createdAt: number;
}

type TodoPreview = Omit<Todo, 'description'>;

const todo: TodoPreview = {
  title: 'Clean room',
  completed: false,
  createdAt: 1615544252770,
};

type TodoInfo = Omit<Todo, 'completed' | 'createdAt'>;

const todoInfo: TodoInfo = {
  title: 'Pick up kids',
  description: 'Kindergarten closes at 5pm',
};
```

**Readonly**

Readonly constructs a type with all properties of Type set to readonly, meaning the properties of the constructed type cannot be reassigned.

```tsx
interface Todo {
  title: string;
}

const todo: Readonly<Todo> = {
  title: 'Delete inactive users',
};

// Cannot assign to 'title' because it is a read-only property.
todo.title = 'Hello';
```

**Record**

Record constructs an object type whose property keys are Keys and whose property values are Type. This utility can be used to map the properties of a type to another type.

```tsx
interface CatInfo {
  age: number;
  breed: string;
}

type CatName = 'miffy' | 'boris' | 'mordred';

const cats: Record<CatName, CatInfo> = {
  miffy: { age: 10, breed: 'Persian' },
  boris: { age: 5, breed: 'Maine Coon' },
  mordred: { age: 16, breed: 'British Shorthair' },
};
```

**Exclude**

Exclude constructs a type by excluding from UnionType all union members that are assignable to ExcludedMembers.

```tsx
type T0 = Exclude<'a' | 'b' | 'c', 'a'>; // "b" | "c"
type T1 = Exclude<'a' | 'b' | 'c', 'a' | 'b'>; // "c"
type T2 = Exclude<string | number | (() => void), Function>; // string | number
```

**Extract**

Extract constructs a type by extracting from Type all union members that are assignable to Union.

```tsx
type T0 = Extract<'a' | 'b' | 'c', 'a' | 'f'>;
//    ^ = type T0 = "a"
```

**Non Nullable**

Non-Nullable constructs a type by excluding **`null`** and **`undefined`**from Type.

```tsx
type T0 = NonNullable<string | number | undefined>;
// type T0 = string | number

type T1 = NonNullable<string[] | null | undefined>;
// type T1 = string[]
```

**Parameters**

Parameters constructs a tuple type from the types used in the parameters of a function type Type.

```tsx
type T0 = Parameters<() => string>;
// type T0 = []

type T1 = Parameters<(s: string) => void>;
// type T1 = [s: string]

type T2 = Parameters<<T>(arg: T) => T>;
// type T2 = [arg: unknown]

declare function f1(arg: { a: number; b: string }): void;
type T3 = Parameters<typeof f1>;

type T4 = Parameters<any>;

type T5 = Parameters<never>;
// type T5 = never

type T6 = Parameters<string>;
// ^ Type 'string' does not satisfy the constraint '(...args: any) => any'.

type T7 = Parameters<Function>;
// ^ Type 'Function' does not satisfy the constraint '(...args: any) => any'.
```

**ReturnType**

Return type constructs a type consisting of the return type of function Type.

```tsx
type T0 = ReturnType<() => string>;
// type T0 = string

type T1 = ReturnType<(s: string) => void>;
// type T1 = void

type T2 = ReturnType<<T>() => T>;
// type T2 = unknown

type T3 = ReturnType<<T extends U, U extends number[]>() => T>;
// type T3 = number[]

declare function f1(): { a: number; b: string };
type T4 = ReturnType<typeof f1>;
// type T4 = {
//     a: number;
//     b: string;
// }

type T5 = ReturnType<any>;
// type T5 = any

type T6 = ReturnType<never>;
// type T6 = never

type T7 = ReturnType<string>;
// ^ Type 'string' does not satisfy the constraint '(...args: any) => any'.

type T8 = ReturnType<Function>;
// ^ Type 'Function' does not satisfy the constraint '(...args: any) => any'.
```

**InstanceType**

This type constructs a type consisting of the instance type of a constructor function in Type.

```tsx
class C {
  x = 0;
  y = 0;
}

type T0 = InstanceType<typeof C>;
// type T0 = C

type T1 = InstanceType<any>;
// type T1 = any

type T2 = InstanceType<never>;
// type T2 = never

type T3 = InstanceType<string>;
// ^ Type 'string' does not satisfy the constraint 'abstract new (...args: any) => any'.

type T4 = InstanceType<Function>;
// ^ Type 'Function' does not satisfy the constraint 'abstract new (...args: any) => any'.
```

**Awaited**

This type is meant to model operations like await in async functions, or the **`.then()`** method on Promises - specifically, the way that they recursively unwrap Promises.

```tsx
type A = Awaited<Promise<string>>;
// type A = string

type B = Awaited<Promise<Promise<number>>>;
// type B = number

type C = Awaited<boolean | Promise<number>>;
// type C = number | boolean
```

---

### Advanced Types

Advanced types in TypeScript are a set of advanced type constructs that allow for more complex and expressive type systems. Some of the most commonly used advanced types in TypeScript include:

**Mapped Types**

Mapped types in TypeScript are a way to create a new type based on an existing type, where each property of the existing type is transformed in some way. Mapped types are declared using a combination of the **`keyof`** operator and a type that maps each property of the existing type to a new property type.

For example, the following is a mapped type that takes an object type and creates a new type with all properties of the original type but with their type changed to **`readonly`**:

```tsx
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

let obj = { x: 10, y: 20 };
let readonlyObj: Readonly<typeof obj> = obj;
```

In this example, the `Readonly` mapped type takes an object type `T`and creates a new type with all properties of `T` but with their type changed to `readonly`. The keyof `T` operator is used to extract the names of the properties of `T`, and the `T[P]` syntax is used to access the type of each property of `T`. The `readonly` keyword is used to make the properties of the new type `readonly`.

**Conditional Types**

Conditional types in TypeScript are a way to select a type based on a condition. They allow you to write a type that dynamically chooses a type based on the types of its inputs. Conditional types are declared using a combination of the **`infer`** keyword and a type that tests a condition and selects a type based on the result of the test.

For example, the following is a conditional type that takes two types and returns the type of the first argument if it extends the second argument, and the type of the second argument otherwise:

```tsx
type Extends<T, U> = T extends U ? T : U;

type A = Extends<string, any>; // type A is 'string'
type B = Extends<any, string>; // type B is 'string'
```

In this example, the Extends conditional type takes two types T and U and returns the type of the first argument **`T`** if it extends the second argument **`U`**, and the type of the second argument **`U`** otherwise. The T extends **`U`** syntax is used to test whether **`T extends U`**, and the **`? T : U`** syntax is used to select the type **`T`** if the test passes and the type **`U`** otherwise.

**Literal Types**

Literal types in TypeScript are a way to specify a value exactly, rather than just a type. Literal types can be used to enforce that a value must be of a specific type and a specific value. Literal types are created by using a literal value, such as a string, number, or boolean, as a type.

For example, the following is a literal type that represents a value of 42:

```tsx
type Age = 42;

let age: Age = 42; // ok
let age: Age = 43; // error
```

In this example, the **`Age`** literal type is created by using the number **`42`**as a type. This type can then be used to enforce that a value must be of type **`number`** and have the value **`42`**.

**Template Literal Types**

Template literal types in TypeScript are a way to manipulate string values as types. They allow you to create a type based on the result of string manipulation or concatenation. Template literal types are created using the backtick (“) character and string manipulation expressions within the type.

For example, the following is a template literal type that concatenates two strings:

```tsx
type Name = `Mr. ${string}`;

let name: Name = `Mr. Smith`;  // ok
let name: Name = `Mrs. Smith`;  // error
```

In this example, the **`Name`** template literal type is created by concatenating the string **`"Mr. "`** with the type **`string`**. This type can then be used to enforce that a value must be a string that starts with **`"Mr. "`**.

**Recursive Types**

Recursive types in TypeScript are a way to define a type that references itself. Recursive types are used to define complex data structures, such as trees or linked lists, where a value can contain one or more values of the same type.

For example, the following is a recursive type that represents a linked list:

```tsx
type LinkedList<T> = {
  value: T;
  next: LinkedList<T> | null;
};

let list: LinkedList<number> = {
  value: 1,
  next: { value: 2, next: { value: 3, next: null } },
};
```

In this example, the **`LinkedList`** type is defined as a type that extends **`T`** and contains a property **`next`** of the same type **`LinkedList<T>`**. This allows us to create a linked list where each node contains a value of type **`T`** and a reference to the next node in the list.

These advanced types allow for more complex and expressive type systems, and enable you to write code that is safer, more maintainable, and easier to understand. By leveraging these advanced types, you can write code that is more robust, less prone to errors, and easier to maintain.

---

### TypeScript Modules

In TypeScript, modules are used to organize and reuse code. There are two types of modules in TypeScript:

- Internal
- External

Internal modules are used to organize code within a file and are also referred to as namespaces. They are defined using the “namespace” keyword.

External modules are used to organize code across multiple files. They are defined using the “export” keyword in one file and the “import” keyword in another file. External modules in TypeScript follow the CommonJS or ES modules standards.

Here is an example of how you can use internal modules in TypeScript:

```tsx
// myModule.ts
namespace MyModule {
  export function doSomething() {
    console.log('Doing something...');
  }
}

// main.ts
/// <reference path="myModule.ts" />
MyModule.doSomething(); // Output: "Doing something..."
```

**Namespaces**

In TypeScript, namespaces are used to organize and share code across multiple files. Namespaces allow you to group related functionality into a single unit and prevent naming conflicts.

Here’s an example of how you can use namespaces in TypeScript:

```tsx
// myNamespace.ts
namespace MyNamespace {
  export function doSomething() {
    console.log('Doing something...');
  }
}

// main.ts
/// <reference path="myNamespace.ts" />
MyNamespace.doSomething(); // Output: "Doing something..."
```

In this example, we use the **`namespace`** keyword in the “myNamespace.ts” file to define a namespace “MyNamespace”. Within the namespace, we export a function “doSomething”.

**Ambient Modules**

Ambient modules in TypeScript are used to declare external modules or third-party libraries in a TypeScript program. Ambient modules provide type information for modules that have no TypeScript declarations, but are available in the global scope.

Here’s an example of how you can use ambient modules in TypeScript:

```tsx
// myModule.d.ts
declare module 'my-module' {
  export function doSomething(): void;
}

// main.ts
import * as myModule from 'my-module';
myModule.doSomething();
```

In this example, we declare an ambient module “my-module” in the **`myModule.d.ts`** file. This declaration provides type information for the “my-module” module, including the “doSomething” function that is exported from the module.

**External Modules**

In TypeScript, external modules allow you to organize and share code across multiple files. External modules in TypeScript follow the CommonJS or ES modules standards.

Here’s an example of how you can use external modules in TypeScript:

```tsx
// myModule.ts
export function doSomething() {
  console.log('Doing something...');
}

// main.ts
import { doSomething } from './myModule';
doSomething(); // Output: "Doing something..."
```

In this example, we use the “export” keyword in the “myModule.ts” file to export the “doSomething” function, making it available for other files to use.

**Namespace Augmentation**

In TypeScript, namespace augmentation is a way to extend or modify existing namespaces. This is useful when you want to add new functionality to existing namespaces or to fix missing or incorrect declarations in third-party libraries.

Here’s an example of how you can use namespace augmentation in TypeScript:

```tsx
// myModule.d.ts
declare namespace MyModule {
  export interface MyModule {
    newFunction(): void;
  }
}

// main.ts
/// <reference path="myModule.d.ts" />
namespace MyModule {
  export class MyModule {
    public newFunction() {
      console.log('I am a new function in MyModule!');
    }
  }
}

const obj = new MyModule.MyModule();
obj.newFunction(); // Output: "I am a new function in MyModule!"
```

In this example, we use namespace augmentation to add a new function “newFunction” to the “MyModule” namespace. This is done in the declaration file **`myModule.d.ts`** by declaring a new interface “MyModule” within the “MyModule” namespace and adding the “newFunction” function to it.

**Global Augmentation**

In TypeScript, global augmentation is a way to add declarations to the global scope. This is useful when you want to add new functionality to existing libraries or to augment the built-in types in TypeScript.

Here’s an example of how you can use global augmentation in TypeScript:

```tsx
// myModule.d.ts
declare namespace NodeJS {
  interface Global {
    myGlobalFunction(): void;
  }
}

// main.ts
global.myGlobalFunction = function () {
  console.log('I am a global function!');
};

myGlobalFunction(); // Output: "I am a global function!"
```

In this example, we declare a new namespace “NodeJS” and add an interface “Global” to it. Within the “Global” interface, we declare a new function “myGlobalFunction”.

---

### Ecosystem

**Formatting**

Prettier is an opinionated code formatter with support for JavaScript, HTML, CSS, YAML, Markdown, GraphQL Schemas. By far the biggest reason for adopting Prettier is to stop all the on-going debates over styles.

Visit the following resources to learn more:

- **[Prettier Website](https://prettier.io/)**
- **[Why Prettier](https://prettier.io/docs/en/why-prettier.html)**

**Linting**

With ESLint you can impose the coding standard using a certain set of standalone rules.

Visit the following resources to learn more:

- **[ESLint Official Website](https://eslint.org/)**
- **[Introduction to ESLint](https://dev.to/shivambmgupta/eslint-what-why-when-how-5f1d)**
- **[ESLint Quickstart - find errors automatically](https://www.youtube.com/watch?v=qhuFviJn-es)**

**Useful Packages**

TypeScript has a large ecosystem of packages that can be used to extend the language or to add functionality to your project. Here is the list of some of the most useful packages.

- **[zod](https://zod.dev/)**: A TypeScript-first data validation library
- **[ts-morph](https://github.com/dsherret/ts-morph)**: A TypeScript-first API for manipulating TypeScript code
- **[ts-node](https://typestrong.org/ts-node/)**: A TypeScript execution and REPL for node.js
- **[ts-jest](https://github.com/kulshekhar/ts-jest)**: A Jest transformer with source map support that lets you use Jest to test projects written in TypeScript.
- **[typesync](https://github.com/jeffijoe/typesync)**: Install missing TypeScript typings for dependencies in your package.json.
- **[tsd](https://github.com/SamVerschueren/tsd)** - TypeScript Definition Manager
- **[type-fest](https://github.com/sindresorhus/type-fest)** - A collection of essential TypeScript types

**Build Tools**

Task runners automatically execute commands and carry out processes behind the scenes. This helps automate your workflow by performing mundane, repetitive tasks that you would otherwise waste an egregious amount of time repeating yourself.

Common usages of task runners include numerous development tasks such as: spinning up development servers, compiling code (ex. SCSS to CSS), running linters, serving files up from a local port on your computer, and many more!

Visit the following resources to learn more:

- **[webpack is a static module bundler for modern JavaScript applications](https://webpack.js.org/)**
- **[Vite Next Generation Frontend Tooling](https://vitejs.dev/)**
- **[Parcel is a zero configuration build tool for the web](https://parceljs.org/)**
- **[esbuild is an extremely fast JavaScript bundler and minifier](https://esbuild.github.io/)**
- **[swc is a super-fast compiler written in Rust](https://swc.rs/)**
- **[tsup is a zero-config TypeScript build tool](https://tsup.egoist.sh/)**
- **[Rollup is a module bundler for JavaScript](https://rollupjs.org/guide/en/)**
- **[tsdx is a zero-config CLI for TypeScript package development](https://tsdx.io/)**