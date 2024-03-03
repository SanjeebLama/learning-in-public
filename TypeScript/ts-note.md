# TypeScript Basics

TypeScript is like JavaScript but with extra features for type checking and static analysis.

- **Strongly Typed**: TypeScript is a strongly typed language, which means it enforces type safety.
- **Static Type Checking**: Types are checked at compile time, ensuring fewer errors in development.
- **Dynamically Typed**: JavaScript, on the other hand, is dynamically typed, where types are checked at runtime.

### Benefits of TypeScript:

- **Self-documenting**: Types make code more understandable and maintainable.
- **Error Detection**: Catch errors during development, reducing bugs in production.
- **Team-friendly**: Especially useful for teams working on large projects.

#### Basic Types:

1. **String**

```typescript
let name: string = "John";
```

2. **Number**

```typescript
let age: number = 30;
```

3. **Boolean**

```typescript
let isStudent: boolean = true;
```

4. **Union Types**: Allows a variable to have multiple types.

```typescript
let id: string | number = "ABC123";
```

5. **Any**: Represents any type.

```typescript
let data: any = "Hello";
data = 123;
```

#### Arrays and Objects:

1. **Array of Strings**:

```typescript
let names: string[] = ["John", "Jane", "Doe"];
```

2. **Array of Union Types**:

```typescript
let mixed: (string | number)[] = ["Alice", 25, "Bob", 30];
```

3. **Array of Mixed Types**:

```typescript
let mixed: (string | number | boolean)[] = ["Alice", 25, true];
```

4. **Tuple**: Fixed-length array with defined types for each element.

```typescript
let person: [string, number] = ["John", 30];
```

### Type vs Interface

| Aspect                  | Interface                                      | Type Alias (Type Declaration)                                                 |
| ----------------------- | ---------------------------------------------- | ----------------------------------------------------------------------------- |
| **Syntax**              | Uses the `interface` keyword                   | Uses the `type` keyword                                                       |
| **Extensibility**       | Can be extended with `extends`                 | Cannot be extended                                                            |
| **Declaration**         | Declares a new named type                      | Declares a new named type                                                     |
| **Object Shape**        | Mainly used for defining object shapes         | Can define various types including object shapes, unions, intersections, etc. |
| **Compatibility**       | Easier to understand and use for object shapes | Can be more flexible for creating complex types and combinations              |
| **Extensibility**       | Suitable for open-ended contracts              | Suitable for predefined contracts or complex types                            |
| **Polymorphism**        | Supports polymorphism and inheritance          | Supports polymorphism and inheritance                                         |
| **Declaration Merging** | Supports declaration merging                   | Does not support declaration merging                                          |

<details>

<summary>More Info</summary>

**When to Use:**

- **Interface**:

  - Use when defining the shape of an object or contract, especially when working with object-oriented principles like inheritance and polymorphism.
  - Use for open-ended contracts where future implementations might extend or implement the interface.
  - Use for clearer documentation and intention of defining object shapes.

- **Type Alias (Type Declaration)**:
  - Use when defining complex types that involve unions, intersections, or other advanced type operations.
  - Use for predefined contracts or scenarios where a specific shape or structure is required.
  - Use when flexibility in defining types is needed, such as composing multiple types into one.
  - Use for scenarios where declaration merging is necessary.

**Let's provide examples of use cases for both interfaces and type aliases:**

### Use Cases for Interfaces:

1. **Defining Object Shapes**:

   ```typescript
   interface Person {
     name: string;
     age: number;
   }

   const john: Person = { name: "John", age: 30 };
   ```

2. **Open-Ended Contracts**:

   ```typescript
   interface Shape {
     area(): number;
   }

   class Circle implements Shape {
     constructor(public radius: number) {}
     area() {
       return Math.PI * this.radius ** 2;
     }
   }

   class Square implements Shape {
     constructor(public sideLength: number) {}
     area() {
       return this.sideLength ** 2;
     }
   }
   ```

### Use Cases for Type Aliases (Type Declarations):

1. **Defining Complex Types**:

   ```typescript
   type Status = "idle" | "active" | "offline";

   interface User {
     id: number;
     name: string;
     status: Status;
   }

   const users: User[] = [
     { id: 1, name: "Alice", status: "active" },
     { id: 2, name: "Bob", status: "offline" },
     { id: 3, name: "Charlie", status: "idle" },
   ];
   ```

2. **Creating Composite Types**:

   ```typescript
   type Point = {
     x: number;
     y: number;
   };

   type Vector = Point & { magnitude: number };

   const vector: Vector = { x: 3, y: 4, magnitude: 5 };
   ```

3. **Customizing Function Signatures**:

   ```typescript
   type Comparator<T> = (a: T, b: T) => number;

   function compareLength(a: string, b: string): number {
     return a.length - b.length;
   }

   const compare: Comparator<string> = compareLength;
   ```

4. **Mapped Types**:

   ```typescript
   type Readonly<T> = {
     readonly [K in keyof T]: T[K];
   };

   type ReadonlyPerson = Readonly<Person>;

   const john: ReadonlyPerson = { name: "John", age: 30 };
   ```

**Difference:**

- **Interface**:

  - Can be extended using `extends`.
  - Supports declaration merging.
  - Primarily used for defining object shapes and contracts.

- **Type Alias (Type Declaration)**:

  - Cannot be extended.
  - Does not support declaration merging.
  - Offers more flexibility for creating complex types, including unions, intersections, and mapped types.

- In summary, interfaces are best suited for defining object shapes and contracts, especially when dealing with object-oriented concepts like inheritance and polymorphism.

- Type aliases, on the other hand, offer more flexibility for creating complex types and combinations, making them suitable for scenarios where specific shapes or advanced type operations are required.

</details>

<br/>

### Enums

Enums provide a way to define a set of named constants. They're useful when you have a fixed set of options or categories.

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

let direction: Direction = Direction.Up;
```

Enums make code more readable and maintainable, especially when dealing with options or states.

<details>
  <summary>More info</summary>
  Enums, short for enumerations, are a feature in TypeScript (and many other programming languages) that allow you to define a set of named constants. Each constant in an enum has an associated numeric value, but enums can also be backed by string or numeric values.

Here's a more detailed explanation of enums and their use cases:

1. **Defining Named Constants**: Enums allow you to define a set of named constants, making your code more readable and maintainable. Instead of using magic numbers or strings directly in your code, you can use descriptive names that convey the meaning of each constant.

   ```typescript
   enum Direction {
     Up,
     Down,
     Left,
     Right,
   }

   let direction: Direction = Direction.Up;
   ```

2. **Options and Categories**: Enums are particularly useful when you have a fixed set of options or categories. For example, consider a scenario where you need to represent the status of a task:

   ```typescript
   enum TaskStatus {
     Open,
     InProgress,
     Completed,
   }

   let status: TaskStatus = TaskStatus.InProgress;
   ```

   Using an enum in this case makes it clear that the `status` variable can only have one of the defined values: `Open`, `InProgress`, or `Completed`.

3. **Switch Statements**: Enums are commonly used with switch statements to handle different cases based on the value of an enum variable. This can make your code more organized and easier to understand.

   ```typescript
   enum LogLevel {
     Info,
     Warning,
     Error,
   }

   function logMessage(level: LogLevel) {
     switch (level) {
       case LogLevel.Info:
         console.log("Info message");
         break;
       case LogLevel.Warning:
         console.warn("Warning message");
         break;
       case LogLevel.Error:
         console.error("Error message");
         break;
     }
   }
   ```

4. **Enums with Associated Values**: Enums can also be backed by string or numeric values, allowing you to associate additional information with each enum constant.

   ```typescript
   enum ErrorCode {
     NotFound = 404,
     InternalServerError = 500,
   }

   console.log(ErrorCode.NotFound); // Output: 404
   ```

   In this example, `ErrorCode.NotFound` is associated with the numeric value `404`.

5. **Configuring Enums**: Enums can be configured with various options, such as specifying the starting numeric value or using string values. This gives you flexibility in how enums are represented in your code.

Overall, enums are a powerful feature in TypeScript that can improve the readability, maintainability, and organization of your code, especially in scenarios where you need to represent a fixed set of options or categories.

</details>
<br/>

## Never

`never` represents a type that should never occur. It is typically used to indicate that something cannot happen or that a function never returns.

<details>
  <summary>More info </summary>

`never` is a special type in TypeScript that represents the type of values that never occur. It is used to indicate that something cannot happen or that a function never returns normally.

Here are some key points about `never`:

1. **Unreachable Code**: If TypeScript determines that a certain branch of code will never be executed, it will infer the type of expressions in that branch as `never`.

2. **Function Return Type**: If a function never completes its execution (e.g., it always throws an error or has an infinite loop), TypeScript will infer the return type of that function as `never`.

3. **Incompatibility**: `never` is incompatible with all other types, except `any`. This means that a value of type `never` cannot be assigned to any other type, and vice versa.

4. **Bottom Type**: `never` is often referred to as the "bottom type" because it is a subtype of every other type. This means that `never` is assignable to every other type, but no other type is assignable to `never`.

5. **Use Cases**: `never` is commonly used in scenarios such as exhaustive type checking with discriminated unions, representing impossible states, and ensuring type safety in certain functions (e.g., error handling functions).

Here's a simple example demonstrating the use of `never`:

```typescript
function throwError(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {
    // Infinite loop
  }
}

// Unreachable code, inferred type is never
function unreachableBranch(x: string | number) {
  if (typeof x === "string") {
    console.log(x.toUpperCase());
  } else if (typeof x === "number") {
    console.log(x.toFixed(2));
  } else {
    // Inferred type of expression is never
    throwError("Unexpected type");
  }
}
```

In this example:

- The `throwError` function always throws an error, so its return type is `never`.
- The `infiniteLoop` function contains an infinite loop, so it never completes its execution, resulting in a return type of `never`.
- The `unreachableBranch` function has an unreachable branch, resulting in an inferred type of `never` for that branch.
</details>

### Functions and Arrow Functions

You can define types for functions and arrow functions, specifying parameter types and return types for better type safety.

```typescript
// Function type definition
type AddFunction = (a: number, b: number) => number;

// Arrow function with type definition
const add: AddFunction = (a, b) => a + b;

console.log(add(5, 3)); // Output: 8
```

### Type Assertions

Type assertions allow you to manually override the inferred type of a variable. This can be useful in cases where TypeScript's inference may not accurately determine the type.

```typescript
let userInput: any = "hello";
let strLength: number = (userInput as string).length;
```

### Generics

Generics enable writing reusable components and functions that work with a variety of data types while maintaining type safety.

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("hello");
console.log(output); // Output: hello
```

<details>
    <summary> More on Generics </summary>

Let's break down the example provided and explain how generics work in TypeScript.

In the given example:

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("hello");
console.log(output); // Output: hello
```

Here's what's happening:

1. **Function Declaration**: We declare a function named `identity`. This function takes a type parameter `T` enclosed in angle brackets `<>`. This `T` represents a placeholder for a specific type that will be provided when the function is called.

2. **Function Parameter**: The function `identity` takes a single parameter `arg` of type `T`. This parameter represents the value whose type we want to preserve.

3. **Function Return Type**: The return type of the `identity` function is also specified as `T`, indicating that the function returns the same type as its input parameter.

4. **Type Argument**: When invoking the `identity` function, we provide a type argument explicitly within angle brackets `<>`. In this case, we pass the type `string`, indicating that we want to preserve the type of the input value as `string`.

5. **Function Call**: We call the `identity` function with the argument `'hello'` and specify that we want to preserve its type as `string`.

6. **Output**: The `identity` function returns the input value `'hello'` of type `string`, which is then assigned to the variable `output`. Finally, we log the value of `output`, which prints `'hello'` to the console.

Now, let's discuss how generics work:

- **Type Parameter `T`**: The type parameter `T` serves as a placeholder for a specific type. It allows us to write flexible and reusable functions or components that can work with various data types.

- **Type Inference**: When we call a generic function like `identity`, TypeScript infers the type of `T` based on the type of the argument passed to the function. If we don't explicitly provide a type argument, TypeScript will try to infer the type based on the provided argument.

- **Type Safety**: Generics ensure type safety by preserving the type of the input value throughout the function or component. This helps prevent type errors and ensures that the output maintains the same type as the input.

- **Flexibility**: Generics provide flexibility by allowing us to write code that can handle different data types without sacrificing type safety. This makes our code more versatile and reusable across various scenarios.

In summary, generics in TypeScript enable us to write flexible and reusable code that maintains type safety while working with different data types. They are a powerful feature that contributes to the expressiveness and robustness of TypeScript codebases.

**One real-world example** of using generics in TypeScript is with data structures, such as arrays, linked lists, or stacks. Let's take the example of implementing a generic Stack data structure.

A stack is a collection of elements with two main operations: push (adding an element to the top of the stack) and pop (removing and returning the top element from the stack). Using generics, we can create a reusable Stack class that can work with any type of data.

Here's how we can implement a generic Stack class in TypeScript:

```typescript
class Stack<T> {
  private elements: T[];

  constructor() {
    this.elements = [];
  }

  push(item: T): void {
    this.elements.push(item);
  }

  pop(): T | undefined {
    return this.elements.pop();
  }

  peek(): T | undefined {
    return this.elements[this.elements.length - 1];
  }

  isEmpty(): boolean {
    return this.elements.length === 0;
  }

  size(): number {
    return this.elements.length;
  }
}

// Usage example:
const numberStack = new Stack<number>();
numberStack.push(1);
numberStack.push(2);
numberStack.push(3);
console.log(numberStack.pop()); // Output: 3

const stringStack = new Stack<string>();
stringStack.push("hello");
stringStack.push("world");
console.log(stringStack.peek()); // Output: world
```

In this example:

- We define a `Stack` class with a type parameter `T`, indicating that the stack can hold elements of any type.
- The `push` method allows adding elements to the top of the stack, and the `pop` method removes and returns the top element from the stack.
- We can create instances of `Stack` for different types, such as `number` or `string`, and use them accordingly.

This example demonstrates how generics provide flexibility and reusability by allowing us to create data structures and functions that work with any data type while maintaining type safety. It shows how generics enable us to write more generic and versatile code that can be applied to various scenarios.

</details>

<br/>
<br/>

### Advanced Types

Advanced TypeScript features like intersection types, union types, conditional types, and mapped types provide powerful tools for creating complex type transformations and compositions.

1.  **Intersection Types**:

    - Intersection types allow you to combine multiple types into a single type. The resulting type will have all the properties of each of the constituent types.
    - Example:

      ```typescript
      interface Person {
        name: string;
        age: number;
      }

      interface Employee {
        id: number;
        department: string;
      }

      type EmployeePerson = Person & Employee;
      // or
      interface EmployeePerson extends Person, Employee {
        role: string;
      }
      ```

    - In this example, `EmployeePerson` is an intersection type that combines the properties of both `Person` and `Employee`.

2.  **Union Types**:

    - Union types enable a variable to have multiple types. It allows for flexibility when a value can be one of several types.
    - Example:
      ```typescript
      type Status = "success" | "error" | "pending";
      ```
    - Here, `Status` can only have one of the three specified string literal types.

3.  **Conditional Types**:

    - Conditional types allow you to define types based on conditions. They provide a way to create types that depend on other types.
    - Example:
      ```typescript
      type NonNullable<T> = T extends null | undefined ? never : T;
      ```
    - The `NonNullable` type ensures that the resulting type is not `null` or `undefined`.

    <details>
      <summary> More info </summary>
      Certainly! Let's break down the code and explain the concept of `never` in TypeScript:

```typescript
type NonNullable<T> = T extends null | undefined ? never : T;
```

This line of code defines a type alias `NonNullable<T>` that takes a type parameter `T`. The purpose of this type alias is to transform a type `T` into a type where `null` and `undefined` are excluded from the possible values.

Here's a detailed explanation:

- **`T extends null | undefined ? never : T`**:

  - This is a conditional type. It checks whether `T` extends (`T extends`) `null` or `undefined`. If it does, the type resolves to `never`; otherwise, it resolves to `T`.
  - If `T` extends `null` or `undefined`, it means that `T` can be assigned `null` or `undefined` as a value. In such cases, we want to exclude these values, so we use `never`.
  - `never` represents a type that should never occur. It is typically used to indicate that something cannot happen or that a function never returns.

- **Explanation**:
  - If `T` can be assigned `null` or `undefined`, the condition `T extends null | undefined` is true. In this case, the conditional type resolves to `never`. This means that `NonNullable<T>` will never allow `null` or `undefined` values.
  - If `T` does not extend `null` or `undefined`, the condition is false, and the type resolves to `T`. This means that `NonNullable<T>` will retain the original type `T`.

**Example Usage**:

```typescript
type NonNullableString = NonNullable<string | null | undefined>;
// Resolves to: string

type NonNullableNumber = NonNullable<number | null | undefined>;
// Resolves to: number
```

In these examples, `NonNullableString` and `NonNullableNumber` are type aliases that ensure the exclusion of `null` and `undefined` from the possible values of `string` and `number`, respectively. This ensures that variables of these types can never be assigned `null` or `undefined`.

</details>
<br/>

4.  **Mapped Types**:

    - Mapped types allow you to transform each property in an existing type into a new property with potentially different characteristics.
    - Example:

      ```typescript
      interface Person {
        name: string;
        age: number;
      }

      type ReadonlyPerson = {
        readonly [K in keyof Person]: Person[K];
      };
      ```

    - The `ReadonlyPerson` type makes all properties of `Person` readonly.

These advanced TypeScript features provide powerful capabilities for creating complex and expressive type definitions. They enable you to build more robust and maintainable codebases by enforcing stricter type checking, enabling better code documentation, and facilitating code reuse through generic and conditional types.

# Custom Type Guard vs use `never` type as an alternative

- Let's first define a simple example of a custom type guard using the `instanceof` operator, and then we'll discuss using `never` type as an alternative.

- Both approaches have their use cases, and the choice between them depends on the specific requirements of your codebase.

### Custom Type Guard Example:

```typescript
// Define a custom type guard function
function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}

// Define types
interface Fish {
  swim(): void;
}

interface Bird {
  fly(): void;
}

// Example usage
function move(pet: Fish | Bird) {
  if (isFish(pet)) {
    pet.swim();
  } else {
    pet.fly();
  }
}
```

In this example:

- We define a custom type guard function `isFish` that checks if the provided `pet` parameter is a `Fish`.
- The `isFish` function returns `true` if the `pet` has a `swim` method, indicating that it's a `Fish`.
- We use the `isFish` function inside the `move` function to conditionally call the `swim` method if the `pet` is a `Fish`.

### Using `never` Type as an Alternative:

Alternatively, we can use the `never` type to handle situations where TypeScript cannot determine a specific type within a conditional block:

```typescript
// Define types
interface Fish {
  swim(): void;
}

interface Bird {
  fly(): void;
}

// Example usage
function move(pet: Fish | Bird) {
  if ("swim" in pet) {
    pet.swim();
  } else if ("fly" in pet) {
    pet.fly();
  } else {
    const exhaustiveCheck: never = pet;
    throw new Error(`Unhandled pet: ${exhaustiveCheck}`);
  }
}
```

In this example:

- We use the `in` operator to check if the `swim` or `fly` properties exist on the `pet` object.
- If `swim` exists, TypeScript narrows the type of `pet` to `Fish`, allowing us to call `pet.swim()`.
- If `fly` exists, TypeScript narrows the type of `pet` to `Bird`, allowing us to call `pet.fly()`.
- If neither `swim` nor `fly` exists, TypeScript infers that `pet` is of type `never`, indicating that this branch should never be reached. We throw an error to handle this scenario.

### Best Practices:

- **Custom Type Guards**:
  Custom type guards using `instanceof` or property checks (`in` operator) are best suited when you need to discriminate between specific types and perform different actions based on their properties.

- **Using `never` Type**: The `never` type can be useful when handling exhaustive checks to ensure all possible cases are covered. It helps catch unintended cases at compile-time and is considered a best practice for ensuring type safety and code correctness.

In summary, both approaches have their use cases, and the choice between them depends on the specific requirements of your codebase. Custom type guards are useful for discriminating between specific types, while the `never` type is useful for handling exhaustive checks and ensuring type safety.

## TypeScript Casting or Type Assertions

- TypeScript casting, also known as type assertion in TypeScript, refers to the _process of explicitly telling the TypeScript compiler that a value is of a specific type, overriding its default inference or providing additional type information to improve type safety_.

**There are two ways to perform type casting or type assertions in TypeScript:**

1. **Angle Bracket Syntax**:

   ```typescript
   let someValue: any = "this is a string";
   let strLength: number = (<string>someValue).length;
   ```

2. **As Syntax**:
   ```typescript
   let someValue: any = "this is a string";
   let strLength: number = (someValue as string).length;
   ```

In both cases, we are telling the TypeScript compiler that `someValue` is of type `string`, overriding its default `any` type.

**Use Cases and Considerations:**

1. **Working with Union Types**:
   Type assertions are often used when working with union types to narrow down the possible types of a value.

   ```typescript
   interface Cat {
     meow(): void;
   }

   interface Dog {
     bark(): void;
   }

   function makeSound(animal: Cat | Dog) {
     if ((animal as Cat).meow) {
       (animal as Cat).meow();
     } else {
       (animal as Dog).bark();
     }
   }
   ```

2. **DOM Manipulation**:
   Type assertions are commonly used when interacting with the DOM to access specific properties or methods.

   ```typescript
   const element = document.getElementById("myElement") as HTMLInputElement;
   element.value = "Hello, TypeScript!";
   ```

3. **Overriding Inference**:
   Type assertions can be used to provide additional type information to the compiler when it cannot infer the correct type.

   ```typescript
   let userInput: unknown;
   let userName: string = (userInput as string).toUpperCase();
   ```

4. **Be Careful with Type Assertions**:
   While type assertions can be useful, they bypass the type checking performed by the TypeScript compiler. _Be cautious when using them, as incorrect type assertions can lead to runtime errors if the actual type of the value does not match the asserted type._

In summary, type casting or type assertions in TypeScript are a way to tell the compiler the intended type of a value, providing more control over type inference and improving type safety in certain scenarios.

However, it's essential to use them judiciously and ensure that the asserted types are correct to avoid runtime errors.

# Classes with visibility modifiers

Visibility modifiers in TypeScript classes control the accessibility of class members (properties and methods) from outside the class. There are three visibility modifiers available: `public`, `private`, and `protected`.

**Here's an example to illustrate each visibility modifier:**

```typescript
class Animal {
  public name: string; // Public member (default visibility)
  private age: number; // Private member
  protected color: string; // Protected member

  constructor(name: string, age: number, color: string) {
    this.name = name;
    this.age = age;
    this.color = color;
  }

  public displayInfo() {
    console.log(`Name: ${this.name}, Age: ${this.age}, Color: ${this.color}`);
  }
}

class Dog extends Animal {
  constructor(name: string, age: number, color: string) {
    super(name, age, color);
  }

  public showColor() {
    // Accessible because 'color' is protected and Dog extends Animal
    console.log(`The color of the dog is ${this.color}`);
  }
}

// Usage
const dog = new Dog("Buddy", 3, "Brown");

// Accessible outside the class
console.log(dog.name); // Output: Buddy

// Error: 'age' is private and cannot be accessed from outside the class
console.log(dog.age); // Error

// Error: 'color' is protected and cannot be accessed from outside the class
console.log(dog.color); // Error

dog.displayInfo(); // Output: Name: Buddy, Age: 3, Color: Brown

dog.showColor(); // Output: The color of the dog is Brown
```

- **`public`**: Members with `public` visibility are accessible from outside the class.
- **`private`**: Members with `private` visibility are only accessible within the class where they are declared.
- **`protected`**: Members with `protected` visibility are accessible within the class where they are declared and any _subclasses (child classes)_ that extend the class.

In the example above:

- `name` is `public`, so it can be accessed from outside the class.
- `age` is `private`, so it can only be accessed within the `Animal` class.
- `color` is `protected`, so it can be accessed within the `Animal` class and its subclasses (like `Dog`).

Visibility modifiers help enforce encapsulation and improve the maintainability and security of your code by controlling access to class members. It's a crucial aspect of object-oriented programming in TypeScript.

# Index Signature and Keyof Assertions

Index signatures and `keyof` assertions are powerful features in TypeScript that allow you to work with dynamic object shapes and access properties in a type-safe manner. Let's explore each concept with a real-world use case example:

### Index Signature:

Index signatures enable you to define the types for accessing properties of objects using square bracket notation. This is useful when working with objects that have dynamic property names.

```typescript
interface Car {
  brand: string;
  model: string;
  year: number;
  // Define an index signature for dynamic properties
  [key: string]: any;
}

const myCar: Car = {
  brand: "Toyota",
  model: "Camry",
  year: 2020,
  color: "blue", // Valid property due to index signature
};

console.log(myCar.color); // Output: blue
```

In this example:

- The `Car` interface defines properties `brand`, `model`, and `year`.
- The index signature `[key: string]: any;` allows the addition of any other property with a string key.
- We can add the `color` property to `myCar`, and TypeScript doesn't raise an error because of the index signature.

### keyof Assertion:

The `keyof` keyword in TypeScript is used to obtain the union of keys (property names) of a given type. It helps to create type-safe operations when working with objects.

```typescript
interface Person {
  name: string;
  age: number;
  email: string;
}

// Create a function to get the value of a specific property
function getProperty(obj: Person, key: keyof Person): any {
  return obj[key];
}

const person: Person = {
  name: "Alice",
  age: 30,
  email: "alice@example.com",
};

console.log(getProperty(person, "name")); // Output: Alice
console.log(getProperty(person, "age")); // Output: 30
console.log(getProperty(person, "email")); // Output: alice@example.com
```

In this example:

- The `getProperty` function accepts an object `obj` and a key `key` of type `keyof Person`.
- It returns the value of the property corresponding to the given key.
- We can safely pass keys `"name"`, `"age"`, or `"email"` to the `getProperty` function without worrying about mistyped or nonexistent keys.

### Loop over object's properties that have an index signature using `keyof`

```ts
interface Car {
  brand: string;
  model: string;
  year: number;
  [key: string]: any;
}

const myCar: Car = {
  brand: "Toyota",
  model: "Camry",
  year: 2020,
  color: "blue",
};

// Solution 1: Loop over properties using Object.keys()
Object.keys(myCar).forEach((key: keyof Car) => {
  const value = myCar[key]; // Type-safe access using keyof
  console.log(`${key}: ${value}`);
});

// Solution 2: Loop over properties using keyof
for (const key in myCar) {
  if (Object.prototype.hasOwnProperty.call(myCar, key)) {
    const value = myCar[key as keyof Car]; // Use keyof to ensure type safety
    console.log(`${key}: ${value}`);
  }
}

// Solution 3:
for (const [key, value] of Object.entries(myCar)) {
  console.log(`${key}: ${value}`);
}
```

# Loop over object's properties in TS

To loop over an object's properties in TypeScript, you can use various methods, including `for...in` loop, `Object.keys()`, `Object.entries()`, or `Object.getOwnPropertyNames()`.

**Here's how you can loop over an object's properties using these methods:**

### Using `for...in` Loop:

```typescript
const person = {
  name: "Alice",
  age: 30,
  email: "alice@example.com",
};

for (const key in person) {
  if (Object.prototype.hasOwnProperty.call(person, key)) {
    const value = person[key];
    console.log(`${key}: ${value}`);
  }
}
```

### Using `Object.keys()`:

```typescript
Object.keys(person).forEach((key) => {
  const value = person[key];
  console.log(`${key}: ${value}`);
});
```

### Using `Object.entries()`:

```typescript
Object.entries(person).forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});
```

### Using `Object.getOwnPropertyNames()`:

```typescript
Object.getOwnPropertyNames(person).forEach((key) => {
  const value = person[key];
  console.log(`${key}: ${value}`);
});
```

### Note:

- In the `for...in` loop, it's essential to use `Object.prototype.hasOwnProperty.call()` to ensure that only own properties of the object are iterated over.
- `Object.keys()`, `Object.entries()`, and `Object.getOwnPropertyNames()` return an array of keys, which you can then iterate over using `forEach()` or other array iteration methods.

Choose the method that best fits your specific use case and coding style preferences. Each method offers similar functionality for looping over an object's properties, but the syntax may vary slightly.

# Utility Types

- Utility types in TypeScript are _built-in generic types_ that provide convenient ways to transform and manipulate existing types.

- These utility types help simplify common type transformations, such as making properties optional, creating read-only properties, mapping types, and more.

**Here are some commonly used utility types in TypeScript:**

1.  **Partial<T>**: Constructs a type with all properties of `T` set to optional.

    ```typescript
    interface Person {
      name: string;
      age: number;
    }

    type PartialPerson = Partial<Person>;

    // Example usage
    const partialPerson: PartialPerson = { name: "Alice" };
    ```

2.  **Readonly\<T\>**: Constructs a type with all properties of `T` set to read-only.

    ```typescript
    interface Person {
      name: string;
      age: number;
    }

    type ReadonlyPerson = Readonly<Person>;

    // Example usage
    const readonlyPerson: ReadonlyPerson = { name: "Bob", age: 30 };
    // readonlyPerson.name = "Charlie"; // Error: Cannot assign to 'name' because it is a read-only property
    ```

3.  **Required<T>**: Constructs a type with all properties of `T` set to required.

    ```typescript
    interface PartialPerson {
      name?: string;
      age?: number;
    }

    type RequiredPerson = Required<PartialPerson>;

    // Example usage
    const requiredPerson: RequiredPerson = { name: "Alice", age: 25 };
    ```

4.  **Record<K, T>**: Constructs an object type whose keys are of type `K` and values are of type `T`.

    ```typescript
    type PhoneNumbers = Record<string, string>;

    // Example usage
    const phoneNumbers: PhoneNumbers = {
      Alice: "123-456-7890",
      Bob: "987-654-3210",
    };
    ```

5.  **Pick<T, K>**: Constructs a type by picking the set of properties `K` from `T`.

    ```typescript
    interface Person {
      name: string;
      age: number;
      email: string;
    }

    type PersonBasicInfo = Pick<Person, "name" | "email">;

    // Example usage
    const personBasicInfo: PersonBasicInfo = {
      name: "Alice",
      email: "alice@example.com",
    };
    ```

6.  **Omit<T, K>**: Constructs a type by omitting specific properties `K` from `T`.

    ```typescript
    interface Person {
      name: string;
      age: number;
      email: string;
    }

    type PersonWithoutEmail = Omit<Person, "email">;

    // Example usage
    const person: PersonWithoutEmail = { name: "Alice", age: 30 };
    ```

7.  **Exclude<T, U>**: Constructs a type by excluding all types from `T` that are assignable to `U`.

    ```typescript
    type Numbers = 1 | 2 | 3 | 4 | 5;
    type EvenNumbers = Exclude<Numbers, 1 | 3 | 5>;

    // Example usage
    const evenNumber: EvenNumbers = 2;
    ```

8.  **Extract<T, U>**: Constructs a type by extracting all types from `T` that are assignable to `U`.

    ```typescript
    type Numbers = 1 | 2 | 3 | 4 | 5;
    type OddNumbers = Extract<Numbers, 1 | 3 | 5>;

    // Example usage
    const oddNumber: OddNumbers = 3;
    ```

9.  **NonNullable<T>**: Constructs a type by excluding `null` and `undefined` from `T`.

    ```typescript
    type NullableString = string | null | undefined;
    type NonNullableString = NonNullable<NullableString>;

    // Example usage
    const nonNullableString: NonNullableString = "Hello";
    // const invalidString: NonNullableString = null; // Error: Type 'null' is not assignable to type 'NonNullableString'
    ```

10. **ReturnType<T>**: Obtains the return type of a function type `T`.

        ```typescript
        type MyFunction = () => number;
        type MyFunctionReturnType = ReturnType<MyFunction>;

        // Example usage
        const result: MyFunctionReturnType = 10;

    // const message: Greeting = "Hello"; // Invalid

        ```

These utility types offer powerful tools for manipulating types in TypeScript, improving type safety and code readability. By leveraging utility types, you can write more expressive and concise code while benefiting from TypeScript's strong type system.
