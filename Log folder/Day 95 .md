# Day 95

Tags: Typescript
Date: November 17, 2023
Status: Done

Tasks of the day

- TypeScripts Interfaces
    - Types vs Interfaces
    - Extending Interfaces
    - Interface Declaration
    - Hybrid Types
- Classes
    - Constructor Params
    - Constructor Overloading
    - Access Modifiers
    - Abstract Classes
    - Inheritance vs Polymorphism
    - Method Overriding
- Generics
    - Generic Types
    - Generic Constraints
- Decorators

---

### Interfaces

Interfaces in TypeScript provide a way to define a contract for a type, which includes a set of properties, methods, and events. It’s used to enforce a structure for an object, class, or function argument. Interfaces are not transpiled to JavaScript and are only used by TypeScript at compile-time for type-checking purposes.

```tsx
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: 'John Doe',
  age: 30,
};
```

In this example, the `User` interface defines the structure of the `user`object with two properties, `name` and `age`. The object is then typed as User using a type-assertion: `User`.

**Types vs Interfaces**

In TypeScript, both types and interfaces can be used to define the structure of objects and enforce type checks. However, there are some differences between the two.
Types are used to create a new named type based on an existing type or to combine existing types into a new type. They can be created using the type keyword. 

For example:

```tsx
type Person = {
  name: string;
  age: number;
};

const person: Person = {
  name: 'John Doe',
  age: 30,
};
```

Interfaces, on the other hand, are used to describe the structure of objects and classes. They can be created using the interface keyword. For example:

```tsx
interface Person {
  name: string;
  age: number;
}

const person: Person = {
  name: 'John Doe',
  age: 30,
};
```

Learn more from the following links:

- **[Interfaces vs. Type Aliases](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces)**
- **[Interfaces vs Types in TypeScript](https://stackoverflow.com/questions/37233735/interfaces-vs-types-in-typescript)**

**Extending Interfaces**

In TypeScript, you can extend an interface by creating a new interface that inherits from the original interface using the “extends” keyword. The new interface can include additional properties, methods, or redefine the members of the original interface.

```tsx
interface Shape {
  width: number;
  height: number;
}

interface Square extends Shape {
  sideLength: number;
}

let square: Square = {
  width: 10,
  height: 10,
  sideLength: 10,
};
```

In this example, the **`Square`** interface extends the **`Shape`** interface and adds an additional property **`sideLength`**. A variable of type **`Square`**must have all the properties defined in both **`Shape`** and **`Square`**interfaces.

**Interface Declaration**

An **`interface`** in TypeScript is a blueprint for creating objects with specific structure. An **`interface`** defines a set of properties, methods, and events that a class or object must implement. The interface is a contract between objects and classes and can be used to enforce a specific structure for objects in your code.

Here is an example of an interface declaration in TypeScript:

```tsx
interface Person {
  firstName: string;
  lastName: string;
  age?: number;

  getFullName(): string;
}
```

In this example, the Person interface defines four properties: **`firstName`**, **`lastName`**, **`age`**, and a method **`getFullName()`**. The age property is optional, indicated by the **`?`** symbol. Any class or object that implements the **`Person`** interface must have these properties and method.

**Hybrid Types**

In TypeScript, a hybrid type is a type that combines multiple types into a single type. The resulting type is considered a union of those types. This allows you to specify that a value can have multiple types, rather than just one.

For example, you can create a hybrid type that can accept either a string or a number:

```tsx
type StringOrNumber = string | number;
```

You can also use hybrid types to create more complex types that can represent a combination of several different types of values. For example:

```tsx
type Education = {
  degree: string;
  school: string;
  year: number;
};

type User = {
  name: string;
  age: number;
  email: string;
  education: Education;
};
```

---

### Classes

Classes in TypeScript are a blueprint for creating objects (instances of a class), providing a way to structure objects and encapsulate data and behavior. Classes in TypeScript have a similar syntax to classes in other object-oriented programming languages, such as Java and C#.

A class in TypeScript is defined using the class keyword, followed by the name of the class. The class definition can include fields (also known as properties or attributes), methods (functions), and a constructor.

```tsx
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }

  makeSound(): void {
    console.log(`${this.name} is making a sound`);
  }
}

const dog = new Animal('Dog');
dog.makeSound(); // Output: Dog is making a sound
```

In this example, the **`Animal`** class has a name field, a constructor that sets the value of the **`name`** field, and a **`makeSound`** method. An instance of the **`Animal`** class can be created using the **`new`** keyword, and its methods and properties can be accessed using dot notation.

**Constructor Params**

In TypeScript, constructor parameters can be declared with access modifiers (e.g. `public`, `private`, `protected`) and/or type annotations. The parameters are then automatically assigned to properties of the same name within the constructor, and can be accessed within the class.

For example:

```tsx
class Example {
  constructor(private name: string, public age: number) {}
}
```

In this example, the constructor has two parameters: name and age. name has a private access modifier, so it can only be accessed within the Example class. age has a public access modifier, so it can be accessed from outside the class as well.

Learn more from the following links:

- **[TypeScript - Construct](https://www.typescriptlang.org/docs/handbook/2/classes.html#constructors)**

**Constructor Overloading**

In TypeScript, you can achieve constructor overloading by using multiple constructor definitions with different parameter lists in a single class. Given below is the example where we have multiple definitions for the constructor:

```tsx
class Point {
  // Overloads
  constructor(x: number, y: string);
  constructor(s: string);
  constructor(xs: any, y?: any) {
    // TBD
  }
}
```

Note that, similar to function overloading, we only have one implementation of the consructor and it’s the only the signature that is overloaded.

Learn more from the following resources:

- **[Constructors - TypeScript](https://www.typescriptlang.org/docs/handbook/2/classes.html#constructors)**

**Access Modifiers**

In TypeScript, access modifiers are keywords used to control the visibility and accessibility of class properties and methods. There are three access modifiers in TypeScript:

- `public:` This is the default access modifier. Properties and methods declared as public can be accessed from anywhere, both inside and outside the class.
- `private:` Properties and methods declared as private can only be accessed within the same class. They are not accessible from outside the class.
- `protected:` Properties and methods declared as protected can be accessed within the class and its subclasses. They are not accessible from outside the class and its subclasses.

Access modifiers in TypeScript allow you to define the level of visibility and accessibility of properties and methods in your class, making your code more maintainable and secure.

**Abstract Classes**

Abstract classes in TypeScript are classes that cannot be instantiated on their own and must be subclassed by other classes. Abstract classes provide a blueprint for other classes and can have abstract methods, which are methods without a body and must be overridden by the subclass. These classes are useful for defining a common interface or basic functionality that other classes can inherit and build upon.

```tsx
abstract class Animal {
  abstract makeSound(): void;

  move(): void {
    console.log('moving...');
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log('bark');
  }
}
```

### Inheritance vs Polymorphism

Inheritance and polymorphism are two fundamental concepts in object-oriented programming, and they are supported in TypeScript as well.

Inheritance refers to a mechanism where a subclass inherits properties and methods from its parent class. This allows a subclass to reuse the code and behavior of its parent class while also adding or modifying its own behavior. In TypeScript, inheritance is achieved using the extends keyword.

Polymorphism refers to the ability of an object to take on many forms. This allows objects of different classes to be treated as objects of a common class, as long as they share a common interface or inheritance hierarchy. In TypeScript, polymorphism is achieved through method overriding and method overloading.

```tsx
class Animal {
  makeSound(): void {
    console.log('Making animal sound');
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log('Bark');
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log('Meow');
  }
}

let animal: Animal;

animal = new Dog();
animal.makeSound(); // Output: Bark

animal = new Cat();
animal.makeSound(); // Output: Meow
```

Learn more from the following resources:

- **[Inheritance and Polymorphism In TypeScript](https://www.youtube.com/watch?v=Sn6K57YSuwU)**

**Method Overriding**

In TypeScript, method overriding is a mechanism where a subclass provides a new implementation for a method that is already defined in its parent class. This allows the subclass to inherit the behavior of the parent class, but change its behavior to fit its own needs.

To override a method in TypeScript the signature of the method in the subclass must match exactly with the signature of the method in the parent class.

```tsx
class Animal {
  makeSound(): void {
    console.log('Making animal sound');
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log('Bark');
  }
}

let animal: Animal;

animal = new Dog();
animal.makeSound(); // Output: Bark
```

In this example, the **`Dog`** class overrides the makeSound method defined in the Animal class and provides its own implementation. When the **`makeSound`** method is called on an instance of the **`Dog`** class, it will use the implementation in the **`Dog`** class rather than the implementation in the **`Animal`** class.

---

### Generics

Generics in TypeScript are a way to write code that can work with multiple data types, instead of being limited to a single data type. Generics allow you to write functions, classes, and interfaces that take one or more type parameters, which act as placeholders for the actual data types that will be used when the function, class, or interface is used.

For example, the following is a generic function that takes a single argument of any data type and returns the same data type:

```tsx
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>('Hello'); // type of output will be 'string'
```

In this example, the **`identity`** function takes a single argument of any data type and returns the same data type. The actual data type is specified when the function is called by using **`<string>`** before the argument **`"Hello"`**.

**Generic Types**

Generic types in TypeScript allow you to write objects, functions and classes that work with multiple data types, instead of being limited to a single data type. A generic type is defined using angle brackets **`<T>`** and can be used as a placeholder for a specific data type. The actual data type is specified when the function or class is used.

For example, the following is a generic function that takes a single argument of any data type and returns the same data type:

```tsx
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>('Hello'); // type of output will be 'string'
```

In this example, the **`identity`** function takes a single argument of any data type and returns the same data type. The actual data type is specified when the function is called by using **`<string>`** before the argument **`Hello`**.

Generics can also be used with classes, interfaces, and object types, allowing them to work with multiple data types as well.

For example:

```tsx
class GenericNumber<T> {
  zeroValue: T;
  add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function (x, y) {
  return x + y;
};
```

**Generic Constraints**

Generic constraints in TypeScript allow you to specify the requirements for the type parameters used in a generic type. These constraints ensure that the type parameter used in a generic type meets certain requirements.

Constraints are specified using the **`extends`** keyword, followed by the type that the type parameter must extend or implement.

```tsx
interface Lengthwise {
  length: number;
}

function loggingIdentity<T extends Lengthwise>(arg: T): T {
  // Now we know it has a .length property, so no more error
  console.log(arg.length);

  return arg;
}

loggingIdentity(3); // Error, number doesn't have a .length property
loggingIdentity({ length: 10, value: 3 }); // OK
```

In this example, the **`Lengthwise`** interface defines a **`length`** property. The **`loggingIdentity`** function uses a generic type parameter **`T`** that is constrained by the **`Lengthwise`** interface, meaning that the type parameter must extend or implement the **`Lengthwise`** interface. This constraint ensures that the length property is available on the argument passed to the **`loggingIdentity`** function.

**Decorators**

Decorators are a feature of TypeScript that allow you to modify the behavior of a class, property, method, or parameter. They are a way to add additional functionality to existing code, and they can be used for a wide range of tasks, including logging, performance optimization, and validation.

Here’s an example of how you might use a decorator in TypeScript:

```tsx
function log(
  target: Object,
  propertyKey: string | symbol,
  descriptor: PropertyDescriptor
) {
  const originalMethod = descriptor.value;

  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${propertyKey} with arguments: ${args}`);
    return originalMethod.apply(this, args);
  };

  return descriptor;
}

class Calculator {
  @log
  add(a: number, b: number): number {
    return a + b;
  }
}

const calculator = new Calculator();
calculator.add(1, 2);
// Output: Calling add with arguments: 1,2
// Output: 3
```

In this example, we use the **`@log`** decorator to modify the behavior of the **`add`** method in the **`Calculator`** class. The **`log`** decorator logs the arguments passed to the method before calling the original method. This allows us to see what arguments are being passed to the method, without having to modify the method’s code.