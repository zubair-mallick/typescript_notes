
# TypeScript Overview

# TypeScript Quick Overview

| **Topic**                  | **Description**                                               | **Link**                        |
|----------------------------|---------------------------------------------------------------|---------------------------------|
| [TypeScript Overview](#typescript-overview)         | Introduction to TypeScript and installation instructions.  | [Overview](#typescript-overview)        |
| [Basic Types](#basic-types)                 | Overview of TypeScript's basic types.                        | [Basic Types](#basic-types)                |
| [Functions](#functions)                  | Different ways to define functions in TypeScript.            | [Functions](#functions)                   |
| [Objects and Type Aliases](#objects-and-type-aliases)  | Defining object types and type aliases.                       | [Objects and Type Aliases](#objects-and-type-aliases)  |
| [Advanced Types](#advanced-types)              | Exploring advanced type features like Readonly and Partial. | [Advanced Types](#advanced-types)         |
| [Operators](#operators)                    | Explanation of TypeScript operators like `&`, `?`, and `|`.  | [Operators](#operators)                  |
| [Arrays](#arrays)                        | Various ways to work with arrays in TypeScript.               | [Arrays](#arrays)                      |
| [Union Types](#union-types)                  | Using union types for flexible type handling.                | [Union Types](#union-types)             |
| [Tuples](#tuples)                        | Understanding tuples and their applications.                 | [Tuples](#tuples)                     |
| [Enums](#enums)                          | Working with enums for better readability.                    | [Enums](#enums)                      |
| [Interfaces vs Type Aliases](#interfaces-vs-type-aliases) | Comparing interfaces and type aliases.                       | [Interfaces vs Type Aliases](#interfaces-vs-type-aliases) |
| [Classes](#classes)                        | Basics of defining and extending classes.                    | [Classes](#classes)                   |
| [Access Modifiers: `public`, `private`](#access-modifiers-public-private) | Controlling access to class members.                         | [Access Modifiers](#access-modifiers-public-private) |
| [Protected Modifier](#protected-modifier)    | Using the `protected` keyword for inheritance.                | [Protected Modifier](#protected-modifier) |
| [Interface and Extend](#interface-and-extend) | Extending interfaces to build upon existing structures.       | [Interface and Extend](#interface-and-extend) |
| [Abstract Class](#abstract-class)            | Creating abstract classes and methods.                       | [Abstract Class](#abstract-class)       |
| [Generics](#generics)                      | Using generics to create type-safe reusable components.       | [Generics](#generics)                  |
| [TypeScript Narrowing](#typescript-narrowing)   | Techniques for narrowing types, such as `in` and `instanceof`. | [Narrowing](#typescript-narrowing)     |
| [Advanced Types and Narrowing](#typescript-advanced-types-and-narrowing) | Using advanced types and narrowing with `never`.             | [Advanced Types and Narrowing](#typescript-advanced-types-and-narrowing) |



**TypeScript** is a statically typed superset of JavaScript that adds optional types to the language, enhancing code quality and maintainability. It compiles down to plain JavaScript, making it compatible with existing JavaScript projects.

## Installation

**Project Installation:**
To install TypeScript locally in a project, run:
```bash
npm install typescript --save-dev
```

**Global Installation:**
To install TypeScript globally, run:
```bash
npm install -g typescript
```

## Basic Types

- **Numbers:** `let num: number = 5;`
- **Booleans:** `let isTrue: boolean = true;`
- **Strings:** `let str: string = "Hello";`
- **Arrays:** `let arr: number[] = [1, 2, 3];`
- **Tuples:** `let tuple: [string, number] = ["hello", 10];`
- **Enums:** `enum Color { Red, Green, Blue }`

## Functions

**Normal Function:**
```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

**Arrow Function:**
```typescript
const add = (a: number, b: number): number => a + b;
```

## Objects and Type Aliases

**Object Types:**
```typescript
let obj: { name: string; age: number } = { name: "John", age: 30 };
```

**Type Aliases:**
```typescript
type Person = { name: string; age: number };
let person: Person = { name: "Jane", age: 25 };
```

## Advanced Types

- **Readonly:** `readonly number[]` - An array where elements cannot be modified.
- **Required:** Ensures all properties are required.
- **Partial:** Makes all properties optional.

## Operators

- **`&` (Intersection Type):** Combines multiple types into one, where the resulting type has all the properties of the intersected types.
  ```typescript
  type Admin = { admin: true };
  type User = { user: true };
  type AdminUser = Admin & User; // { admin: true; user: true }
  ```

- **`?` (Optional):** Marks a property or parameter as optional.
  ```typescript
  interface Person {
    name: string;
    age?: number; // age is optional
  }
  ```

- **`|` (Union Type):** Allows a value to be one of several types.
  ```typescript
  let value: string | number = "hello";
  value = 100; // OK
  ```

## Arrays

**Basic Array:**
```typescript
let numbers: number[] = [1, 2, 3];
```

**Array with Tuple Elements:**
```typescript
let mixedArray: [string, number][] = [["hello", 1], ["world", 2]];
```

**Readonly Array:**
```typescript
let readonlyArray: readonly number[] = [1, 2, 3];
```

**Array of Objects:**
```typescript
let people: { name: string; age: number }[] = [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 }
];
```

**Type Differences in Arrays:**
- **`(type1 | type2)[]`:** An array where each element can be either `type1` or `type2`.
  ```typescript
  let mixedArray: (string | number)[] = ["hello", 1];
  ```
- **`type1[] | type2[]`:** Either an array of `type1` or an array of `type2`, but not a mix of both.
  ```typescript
  let numbers: number[] = [1, 2, 3];
  let strings: string[] = ["a", "b", "c"];
  ```

## Union Types

**Example:**
```typescript
let value: string | number = "hello";
value = 100; // OK
```

**Using Union Types with Functions:**
```typescript
function format(value: string | number): string {
  return typeof value === "string" ? value.toUpperCase() : value.toFixed(2);
}
```

## Tuples

**Example:**
```typescript
let tuple: [string, number] = ["hello", 10];
```

**Tuple with Optional Elements:**
```typescript
let optionalTuple: [string, number?] = ["hello"]; // number is optional
```

**Tuple with Named Elements:**
```typescript
let namedTuple: [name: string, age: number] = ["John", 30];
```

## Enums

**Example:**
```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}
let move: Direction = Direction.Up;
```

**String Enums:**
```typescript
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT"
}
```

## Interfaces vs Type Aliases

**Interface:**
```typescript
interface Person {
  name: string;
  age: number;
}
```

**Type Alias:**
```typescript
type Person = {
  name: string;
  age: number;
};
```

**Key Differences:**
- **Extending Interfaces:** Interfaces can be extended with additional properties or methods.
  ```typescript
  interface Employee extends Person {
    position: string;
  }
  ```
- **Type Aliases for Complex Types:** Type aliases can be used for unions, intersections, and more complex structures.
  ```typescript
  type StringOrNumber = string | number;
  type Point = { x: number; y: number };
  ```

## Classes

**Example:**
```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }
}
```

**Class Inheritance:**
```typescript
class Employee extends Person {
  position: string;

  constructor(name: string, age: number, position: string) {
    super(name, age);
    this.position = position;
  }

  describe(): void {
    console.log(`${this.name} is a ${this.position}`);
  }
}
```

**Initializers in Classes:**

In TypeScript, it's important to initialize class properties either directly or through the constructor to avoid errors. Here’s what to do and what not to do:

**Correct Initialization:**

- **Direct Initialization:**
  ```typescript
  class Person {
    name: string = "Unknown";
    age: number = 0;

    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }
  }
  ```

- **Initialization in Constructor:**
  ```typescript
  class Person {
    name: string;
    age: number;

    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }
  }
  ```

**Incorrect Initialization:**

- **Uninitialized Properties:**
  ```typescript
  class Person {
    name: string; // Error: Property 'name' has no initializer and is not definitely assigned in the constructor.
    age: number;

    constructor(name: string, age: number) {
      this.age = age;
    }
  }
  ```

In the example above, `name` is declared but not initialized, which causes an error if strict class property initialization is enabled. Always ensure properties are initialized or provided through the constructor.




## Access Modifiers: `public`, `private`

TypeScript uses `public` (default) and `private` to control access to class members.

### Public Modifier (Default)
`public` members are accessible from anywhere, and it's the default in TypeScript.

```typescript
class Person {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  public greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }
}

let john = new Person("John", 30);
john.greet(); // Accessible
```

### Private Modifier
`private` members can only be accessed inside the class. They cannot be used from outside the class.

```typescript
class Person {
  private name: string;
  private age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  private greet(): void {
    console.log(`Hello, my name is ${this.name}`);
  }

  public showDetails(): void {
    this.greet(); // Can access private method within the class
  }
}

let john = new Person("John", 30);
// john.greet(); // Error: 'greet' is private
john.showDetails(); // OK
```

### Private Members in Constructor
You can declare and initialize private members directly in the constructor:

```typescript
class Person {
  constructor(private name: string, private age: number) {}

  public showDetails(): void {
    console.log(`Name: ${this.name}, Age: ${this.age}`);
  }
}

let jane = new Person("Jane", 25);
jane.showDetails(); // OK
```

### Getters and Setters
Getters and setters provide a way to access and update private properties.

#### Example:
```typescript
class Person {
  private _age: number;

  constructor(private name: string, age: number) {
    this._age = age;
  }

  // Getter
  public get age(): number {
    return this._age;
  }

  // Setter with validation
  public set age(value: number) {
    if (value < 0) {
      throw new Error("Age cannot be negative!");
    }
    this._age = value;
  }
}

let john = new Person("John", 30);
console.log(john.age); // 30
john.age = 25; // OK
console.log(john.age); // 25

// john.age = -5; // Throws error: Age cannot be negative!
```

**Note**: Setters cannot return values, and they are used only to assign or modify values.


## `protected` Modifier

The `protected` modifier allows a class member to be accessed within the class itself and by any class that extends it (inherited classes), but it cannot be accessed from outside these classes.

### Example: `User` and `SubUser` Classes

```typescript
class User {
  protected username: string;

  constructor(username: string) {
    this.username = username;
  }

  protected getUsername(): string {
    return this.username;
  }
}

class SubUser extends User {
  constructor(username: string) {
    super(username);
  }

  public displayUsername(): void {
    console.log(this.getUsername()); // Can access protected method
  }
}

const user = new SubUser("JohnDoe");
user.displayUsername(); // "JohnDoe"

// user.getUsername(); // Error: 'getUsername' is protected and can't be accessed outside the class
```

### Key Points:
- **Protected members** can be accessed within the class and in subclasses.
- They **cannot** be accessed outside of these classes.

In this example, the `SubUser` class can access the `protected` members of the `User` class, but they are not accessible from outside either class.



Here's a simple explanation of `interface` and `extend` in TypeScript:


## Interface and Extend

In TypeScript, **interfaces** define the structure of an object. You can use the `extends` keyword to inherit from one or more interfaces, allowing for reusability and a consistent structure.

### Extending an Interface

You can create a new interface that extends an existing one. This means the new interface inherits all properties and methods from the parent interface, and you can also add new ones.

### Syntax

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

interface Dog extends Animal {
  breed: string;
}
```

In this example, `Dog` extends the `Animal` interface, so any object of type `Dog` must have all the properties from `Animal` (`name`, `makeSound()`), plus any additional properties like `breed`.

### Example

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

interface Dog extends Animal {
  breed: string;
}

const myDog: Dog = {
  name: "Buddy",
  breed: "Golden Retriever",
  makeSound() {
    console.log("Woof!");
  }
};

console.log(myDog.name);   // Output: Buddy
console.log(myDog.breed);  // Output: Golden Retriever
myDog.makeSound();         // Output: Woof!
```

### Key Points:
- `Dog` inherits properties and methods from `Animal`.
- `extends` allows for reusable and extendable interfaces.
`

#### This helps you define more complex types by building on simpler ones.
- it can be use to define simpler structure and kinda like guideline
 


 
## Abstract Class

An **abstract class** in TypeScript is a class that `cannot be instantiated`(Initialized) directly. It is meant to be `inherited by other classes` and can contain both 
- concrete methods (with implementation) 
- abstract methods (without implementation).

### Key Points:
- You **cannot create an object** of an abstract class directly.
- It can contain **abstract methods**, which are declared but not defined. These methods must be implemented by the inheriting classes.
- Abstract methods must be marked with the `abstract` keyword, otherwise, they need a body.

### Syntax

```typescript
abstract class Animal {
  abstract makeSound(): void; // Abstract method (no implementation)

  move(): void {
    console.log("The animal moves.");
  }
}
```

### Example

```typescript
abstract class Animal {
  abstract makeSound(): void;

  move(): void {
    console.log("The animal moves.");
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("Woof!");
  }
}

const myDog = new Dog();
myDog.makeSound();  // Output: Woof!
myDog.move();       // Output: The animal moves.
```

### `extends` and `super`

- **`extends`** is used to create a new class that inherits properties and methods from an abstract class.
- **`super`** is used to call the parent class's constructor or methods inside the child class.

```typescript
class Dog extends Animal {
  constructor() {
    super();  // Calls the parent class's constructor
  }

  makeSound(): void {
    console.log("Woof!");
  }
}
```

### Difference Between Interface and Abstract Class

| **Interface**                       | **Abstract Class**                  |
|-------------------------------------|-------------------------------------|
| Cannot have any implementation.     | Can have both abstract and concrete methods (with implementation). |
| Supports multiple inheritance (a class can implement multiple interfaces). | Supports single inheritance (a class can extend only one abstract class). |
| All methods are by default abstract (no implementation). | Only methods marked with `abstract` are abstract, others can have implementations. |
| No constructor.                     | Can have a constructor.             |





# Generics

Generics allow you to create reusable code components that can work with any data type while maintaining type safety. They are a way to create **type-safe, reusable components**.

## Syntax for Functions

**Generic Function:**
```typescript
function identity<T>(value: T): T {
  return value;
}

let result = identity<string>("Hello");  // Output: "Hello"
let numResult = identity<number>(10);    // Output: 10
```

**Generic Arrow Function:**
```typescript
const identity = <T>(value: T): T => {
  return value;
};
```

## Simple Example of Definition and Use

**Generic with Array:**
```typescript
function getFirstElement<T>(items: T[]): T | undefined {
  return items[0]; // Returns the first element or undefined if the array is empty
}

let stringArray = ["apple", "banana", "cherry"];
let numberArray = [1, 2, 3, 4];

let firstString = getFirstElement<string>(stringArray); // Output: "apple"
let firstNumber = getFirstElement<number>(numberArray); // Output: 1

// If the array is empty, the function will return `undefined`
let emptyArray: string[] = [];
let firstEmpty = getFirstElement<string>(emptyArray); // Output: undefined
```

## `any` vs Generics

- **`any`:** Allows any type, but removes type safety.
  ```typescript
  function identity(value: any): any {
    return value;
  }
  ```

- **Generics:** Maintains type safety while being flexible.
  ```typescript
  function identity<T>(value: T): T {
    return value;
  }
  ```

## Using Interface with Generics

You can apply generics to interfaces as well:
```typescript
interface Box<T> {
  contents: T;
}

let stringBox: Box<string> = { contents: "Books" };
let numberBox: Box<number> = { contents: 100 };
```

## Cliff Notes with Array Example

- **`any[]`:** Flexible, but no type safety.
  ```typescript
  let anyArray: any[] = [1, "apple", true];
  ```

- **`T[]`:** Generic ensures type safety, but is flexible for different types.
  ```typescript
  function getFirstElement<T>(items: T[]): T | undefined {
    return items[0]; // Type-safe and returns first element
  }

  let numArray = getFirstElement<number>([1, 2, 3]); // Type-safe
  let strArray = getFirstElement<string>(["a", "b", "c"]);
  ```


# TypeScript Narrowing

Narrowing is a technique in TypeScript that refines the type of a variable within a specific scope, particularly when dealing with union types. This ensures type safety and allows you to handle different cases appropriately.

## Narrowing with multiple Interfaces as Parameters

**Problem Example:**

Suppose you have two interfaces, `Cat` and `Dog`, each with different properties. You may need to handle instances of these types differently. Using a property that both types have in common helps in narrowing down the type.

**Interfaces:**
```typescript
interface Cat {
  meow: () => void;
}

interface Dog {
  bark: () => void;
}
```

**Function Example:**
```typescript
function handleAnimal(animal: Cat | Dog) {
  if ("meow" in animal) {
    animal.meow(); // Narrowed to Cat
  } else {
    animal.bark(); // Narrowed to Dog
  }
}
```

**Explanation:**
- The `in` operator is used to check if the `meow` property exists in the `animal` object. This helps to determine whether the `animal` is of type `Cat` or `Dog`.
- If `meow` is present, TypeScript narrows the type to `Cat`. Otherwise, it assumes the type is `Dog`.

## The `in` Operator

The `in` operator is used for type guards in TypeScript. It checks whether a property exists on an object, which is useful for narrowing down types when working with unions.

**Example:**
```typescript
interface Cat {
  meow: () => void;
}

interface Dog {
  bark: () => void;
}

function handleAnimal(animal: Cat | Dog) {
  if ("meow" in animal) {
    animal.meow(); // Narrowed to Cat
  } else {
    animal.bark(); // Narrowed to Dog
  }
}
```

**Explanation:**
- By using `"meow" in animal`, TypeScript can determine that `animal` is a `Cat` and can safely call `animal.meow()`.
- Conversely, if `meow` is not present, TypeScript narrows the type to `Dog` and can call `animal.bark()`.

## Summary

- **Narrowing** refines types based on conditions and helps manage different types in union types.
- **Using the `in` operator** for type guards ensures safe and precise type checks by confirming property existence.





# TypeScript Advanced Types and Narrowing

## `instanceof` Operator

The `instanceof` operator checks if an object is an instance of a specific class or constructor function. It can only be used with classes or constructor functions and verifies if an object was created with a `new` keyword.

**Example:**

```typescript
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class Dog extends Animal {
  bark() {
    console.log("Woof!");
  }
}

const myDog = new Dog("Rex");

console.log(myDog instanceof Dog); // true
console.log(myDog instanceof Animal); // true
console.log(myDog instanceof Object); // true
```

**Explanation:**
- `myDog instanceof Dog` checks if `myDog` was constructed with the `Dog` class.
- `myDog instanceof Animal` checks if `myDog` is an instance of a superclass, `Animal`.

## Type Predicates and `is` Syntax

Type predicates help TypeScript understand the type of a variable within a specific scope. You can use the `is` keyword in a function to specify the type that the function narrows down to.

**Syntax:**

```typescript
function isCat(animal: Cat | Dog): animal is Cat {
  return (animal as Cat).meow !== undefined;
}
```

**Example:**

```typescript
interface Cat {
  meow: () => void;
}

interface Dog {
  bark: () => void;
}

function isCat(animal: Cat | Dog): animal is Cat {
  return "meow" in animal;
}

function handleAnimal(animal: Cat | Dog) {
  if (isCat(animal)) {
    animal.meow(); // Narrowed to Cat
  } else {
    animal.bark(); // Narrowed to Dog
  }
}
```

**Explanation:**
- The `isCat` function uses the `is` keyword to specify that if the function returns true, the `animal` is of type `Cat`.

## Discriminated Unions

Discriminated unions are a pattern where a common property (discriminant) is used to determine the type of an object among several possible types. This allows TypeScript to safely narrow down types.

**Example:**

```typescript
interface Circle {
  shape: "circle";
  radius: number;
}

interface Square {
  shape: "square";
  sideLength: number;
}

type Shape = Circle | Square;

function getArea(shape: Shape): number {
  switch (shape.shape) {
    case "circle":
      return Math.PI * shape.radius * shape.radius;
    case "square":
      return shape.sideLength * shape.sideLength;
    default:
      // This case should never be reached if all types are handled
      const _exhaustiveCheck: never = shape;
      throw new Error("Unhandled shape type");
  }
}
```

**Explanation:**
- The `shape` property acts as the discriminant to narrow down the type of `Shape` to either `Circle` or `Square`.
- The `never` type in the `default` case ensures that all possible `Shape` types are handled. If a new `Shape` type is added, TypeScript will generate an error if it's not handled in the `switch` statement.

## `instanceof` vs `in` Operator

- **`instanceof`** checks if an object is an instance of a class or constructor.
- **`in`** checks if a property exists on an object.

**Example using `instanceof`:**

```typescript
class Person {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

function greet(person: Person | string) {
  if (person instanceof Person) {
    console.log(`Hello, ${person.name}`);
  } else {
    console.log(`Hello, ${person}`);
  }
}
```

**Example using `in`:**

```typescript
interface Person {
  name: string;
}

interface Greeting {
  message: string;
}

function greet(entity: Person | Greeting) {
  if ("name" in entity) {
    console.log(`Hello, ${entity.name}`);
  } else {
    console.log(`Message: ${entity.message}`);
  }
}
```

**Explanation:**
- `instanceof` is used for checking instances of classes.
- `in` is used for checking properties and narrowing types in unions.

```

This updated Markdown file includes the `never` type for ensuring exhaustive checks in discriminated unions, and provides examples of both `instanceof` and `in` operators for narrowing types.



