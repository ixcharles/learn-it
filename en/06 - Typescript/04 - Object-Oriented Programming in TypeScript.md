
# Object-Oriented Programming in TypeScript

This course covers the essential concepts of Object-Oriented Programming (OOP) in TypeScript, including classes, interfaces, inheritance, access modifiers, static members, abstract classes, and more. You'll learn how to leverage TypeScript's type system to design maintainable, scalable object-oriented applications.

## Table of Contents

1. [Classes and Interfaces](#classes-and-interfaces)
2. [Inheritance and Method Overriding](#inheritance-and-method-overriding)
3. [Access Modifiers (public, private, protected)](#access-modifiers-public-private-protected)
4. [Static Members and Methods](#static-members-and-methods)
5. [Abstract Classes and Methods](#abstract-classes-and-methods)
6. [Interfaces vs. Type Aliases for OOP](#interfaces-vs-type-aliases-for-oop)

---

## Classes and Interfaces

- **Classes**: Blueprints for creating objects that bundle data and methods.
- **Interfaces**: Contracts that define the structure of an object without implementation.

### Example of Class:

```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): string {
    return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
  }
}

const person = new Person("Alice", 30);
console.log(person.greet());
```

### Example of Interface:

```typescript
interface Greetable {
  name: string;
  greet(): string;
}

class Person implements Greetable {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  greet(): string {
    return `Hello, my name is ${this.name}.`;
  }
}
```

---

## Inheritance and Method Overriding

Inheritance allows one class to inherit properties and methods from another, promoting code reuse. Method overriding lets a subclass provide its own implementation of a method defined in the parent class.

### Example:

```typescript
class Animal {
  name: string;
  
  constructor(name: string) {
    this.name = name;
  }

  speak(): string {
    return `${this.name} makes a sound.`;
  }
}

class Dog extends Animal {
  speak(): string {
    return `${this.name} barks!`;
  }
}

const dog = new Dog("Buddy");
console.log(dog.speak());  // "Buddy barks!"
```

---

## Access Modifiers (public, private, protected)

Access modifiers control the visibility and accessibility of class members (properties and methods). TypeScript supports `public`, `private`, and `protected` access modifiers.

- **public**: Members are accessible from anywhere.
- **private**: Members are only accessible within the class itself.
- **protected**: Members are accessible within the class and its subclasses.

### Example:

```typescript
class Person {
  public name: string;
  private age: number;
  protected address: string;

  constructor(name: string, age: number, address: string) {
    this.name = name;
    this.age = age;
    this.address = address;
  }

  getAge(): number {
    return this.age;
  }
}

const person = new Person("Alice", 30, "123 Main St");
console.log(person.name);  // Accessible
console.log(person.getAge());  // Accessible via public method
// console.log(person.age);  // Error: 'age' is private
```

---

## Static Members and Methods

Static members belong to the class itself, not to instances of the class. These can be accessed without creating an instance of the class.

### Example:

```typescript
class MathUtility {
  static PI: number = 3.14;

  static area(radius: number): number {
    return MathUtility.PI * radius * radius;
  }
}

console.log(MathUtility.area(5));  // Accessing static method without an instance
```

---

## Abstract Classes and Methods

- **Abstract Classes**: Classes that cannot be instantiated directly but can be subclassed. They may contain abstract methods that must be implemented by subclasses.
- **Abstract Methods**: Methods that are declared in abstract classes but do not have implementation, forcing subclasses to provide their own implementation.

### Example:

```typescript
abstract class Shape {
  abstract area(): number;  // Abstract method

  printArea(): void {
    console.log(`The area is: ${this.area()}`);
  }
}

class Circle extends Shape {
  radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}

const circle = new Circle(5);
circle.printArea();  // Outputs: The area is: 78.53981633974483
```

---

## Interfaces vs. Type Aliases for OOP

- **Interfaces**: Primarily used for defining the structure of objects and classes. They can be extended, making them ideal for OOP.
- **Type Aliases**: More flexible than interfaces, allowing you to define unions, intersections, and other complex types.

### Example of Interface in OOP:

```typescript
interface Animal {
  name: string;
  sound(): string;
}

class Dog implements Animal {
  name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  sound(): string {
    return `${this.name} barks.`;
  }
}
```

### Example of Type Alias in OOP:

```typescript
type Animal = {
  name: string;
  sound(): string;
};

class Dog implements Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  sound(): string {
    return `${this.name} barks.`;
  }
}
```

In most OOP scenarios, interfaces are generally preferred, but type aliases can be helpful in more complex type compositions.

---

## Conclusion

### Key Takeaways:
1. TypeScript supports classes and interfaces for implementing Object-Oriented principles, with classes defining object blueprints and interfaces specifying contracts.
2. Inheritance allows code reuse, and method overriding enables subclasses to provide custom implementations.
3. Access modifiers (`public`, `private`, `protected`) control visibility and help encapsulate class logic.
4. Static members are accessible on the class itself without needing an instance.
5. Abstract classes and methods enforce a structure in subclasses, making sure they provide specific implementations.
6. Interfaces are better suited for OOP design, while type aliases offer more flexibility for complex types.

### Practical Exercise:
1. Create a base class `Shape` with an abstract method `area()` and subclass it into `Rectangle` and `Circle` classes.
2. Define an interface `Playable` with a method `play()`, and implement it in two classes, `Guitar` and `Piano`.
3. Experiment with static methods by creating a utility class for handling mathematical calculations (e.g., area of circle, volume of sphere).
