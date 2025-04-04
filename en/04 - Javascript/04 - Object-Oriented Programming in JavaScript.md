
# Object-Oriented Programming in JavaScript

JavaScript is an object-oriented language, and understanding object-oriented programming (OOP) concepts is key to writing efficient, reusable, and maintainable code. This course covers the fundamental OOP principles in JavaScript, including objects, inheritance, and ES6 features.

## Table of Contents
1. [Objects: Creation, Properties, and Methods](#objects-creation-properties-and-methods)
2. [Prototypal Inheritance](#prototypal-inheritance)
3. [Constructors and the `new` Keyword](#constructors-and-the-new-keyword)
4. [ES6 Classes and Inheritance](#es6-classes-and-inheritance)
5. [Static Methods and Properties](#static-methods-and-properties)
6. [Getter and Setter Methods](#getter-and-setter-methods)
7. [Object Destructuring](#object-destructuring)
8. [Object.freeze and Immutability](#objectfreeze-and-immutability)
9. [`this` Keyword and Its Context](#this-keyword-and-its-context)

---

## Objects: Creation, Properties, and Methods
Objects are key-value pairs in JavaScript. They can hold various data types, including arrays, functions, and other objects.

Example:
```javascript
let car = {
  make: 'Toyota',
  model: 'Corolla',
  year: 2020,
  startEngine: function() { console.log("Engine started!"); }
};

console.log(car.make);  // Toyota
car.startEngine();  // Engine started!
```

---

## Prototypal Inheritance
In JavaScript, objects can inherit properties and methods from other objects through the prototype chain.

Example:
```javascript
let animal = { species: 'dog' };
let dog = Object.create(animal);
dog.bark = function() { console.log("Woof!"); };

console.log(dog.species);  // dog (inherited from animal)
dog.bark();  // Woof!
```

---

## Constructors and the `new` Keyword
Constructors are special functions used to create objects. The `new` keyword instantiates a new object based on the constructor function.

Example:
```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

let john = new Person('John', 25);
console.log(john.name);  // John
```

---

## ES6 Classes and Inheritance
ES6 introduces the `class` syntax, which simplifies object creation and inheritance.

Example:
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);  // Calls the parent class constructor
  }

  speak() {
    console.log(`${this.name} barks`);
  }
}

let dog = new Dog('Buddy');
dog.speak();  // Buddy barks
```

---

## Static Methods and Properties
Static methods and properties are defined on the class itself, not on instances of the class.

Example:
```javascript
class MathUtil {
  static add(a, b) {
    return a + b;
  }
}

console.log(MathUtil.add(2, 3));  // 5
```

---

## Getter and Setter Methods
Getters and setters allow you to define custom behavior for reading and setting object properties.

Example:
```javascript
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  get area() {
    return Math.PI * this._radius * this._radius;
  }

  set radius(value) {
    if (value > 0) {
      this._radius = value;
    }
  }
}

let circle = new Circle(5);
console.log(circle.area);  // 78.53981633974483
circle.radius = 10;
console.log(circle.area);  // 314.1592653589793
```

---

## Object Destructuring
Object destructuring allows you to extract values from an object and assign them to variables in a concise way.

Example:
```javascript
let person = { name: 'Alice', age: 30 };
let { name, age } = person;
console.log(name);  // Alice
console.log(age);   // 30
```

---

## Object.freeze and Immutability
The `Object.freeze()` method prevents new properties from being added to an object and makes existing properties immutable.

Example:
```javascript
let user = { name: 'Alice' };
Object.freeze(user);

user.name = 'Bob';  // This won't work
console.log(user.name);  // Alice
```

---

## `this` Keyword and Its Context
The `this` keyword refers to the object that is calling a function. Its value can change depending on the context in which the function is called.

Example:
```javascript
let person = {
  name: 'Alice',
  greet: function() {
    console.log(`Hello, ${this.name}`);
  }
};

person.greet();  // Hello, Alice

let greetFunc = person.greet;
greetFunc();  // Hello, undefined (context lost)
```

---

## Conclusion

### Key Takeaways:
1. JavaScript objects are collections of key-value pairs that can contain other objects, functions, and arrays.
2. Prototypal inheritance allows objects to inherit properties and methods from other objects.
3. ES6 classes simplify object creation and inheritance, making code more readable.
4. Static methods belong to the class itself, not its instances.
5. The `this` keyword’s value is determined by the function’s invocation context.

### Practical Exercise:
1. Create a class `Book` with properties like title, author, and pages. Add methods to get and set those properties using getters and setters.
2. Use object destructuring to extract properties from an object and log them in the console.
3. Create a function to clone an object and freeze it, ensuring that it cannot be modified.
