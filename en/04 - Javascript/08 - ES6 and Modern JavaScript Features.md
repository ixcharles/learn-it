
# ES6 and Modern JavaScript Features

This course introduces modern JavaScript features introduced in ES6 and beyond. These features help write cleaner, more efficient, and easier-to-maintain code. By mastering them, you'll be better equipped to write more powerful applications.

## Table of Contents
1. [Let and Const Declarations](#let-and-const-declarations)
2. [Arrow Functions and Lexical `this`](#arrow-functions-and-lexical-this)
3. [Template Literals](#template-literals)
4. [Default Parameters](#default-parameters)
5. [Rest and Spread Operators](#rest-and-spread-operators)
6. [Destructuring Assignment (Objects, Arrays)](#destructuring-assignment-objects-arrays)
7. [Modules: `import` and `export`](#modules-import-and-export)
8. [Enhanced Object Literals](#enhanced-object-literals)
9. [Iterators and Generators](#iterators-and-generators)
10. [Symbols and Iterables](#symbols-and-iterables)

---

## Let and Const Declarations
`let` and `const` are block-scoped variable declarations introduced in ES6. `let` allows you to reassign variables, whereas `const` defines constants that cannot be reassigned.

Example:
```javascript
let a = 5;
a = 10;  // Allowed

const b = 15;
b = 20;  // Error: Assignment to constant variable
```

---

## Arrow Functions and Lexical `this`
Arrow functions provide a concise syntax and lexically bind the `this` keyword, meaning they inherit the value of `this` from their surrounding context.

Example:
```javascript
let obj = {
  value: 42,
  getValue: function() {
    return () => this.value;  // Arrow function uses lexically bound 'this'
  }
};

let getVal = obj.getValue();
console.log(getVal());  // 42
```

---

## Template Literals
Template literals allow embedded expressions and multi-line strings, improving readability and reducing the need for string concatenation.

Example:
```javascript
let name = 'Alice';
let message = `Hello, ${name}!`;
console.log(message);  // Hello, Alice!

let multiline = `This is
a multiline string.`;
console.log(multiline);
```

---

## Default Parameters
You can assign default values to function parameters, which will be used if no value is provided when the function is called.

Example:
```javascript
function greet(name = 'Guest') {
  console.log(`Hello, ${name}!`);
}

greet('Alice');  // Hello, Alice!
greet();         // Hello, Guest!
```

---

## Rest and Spread Operators
- The **rest operator** (`...`) allows you to collect multiple values into a single array or object.
- The **spread operator** (`...`) allows you to unpack elements from arrays or objects.

Examples:
```javascript
// Rest Operator
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3));  // 6

// Spread Operator
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5];
console.log(arr2);  // [1, 2, 3, 4, 5]
```

---

## Destructuring Assignment (Objects, Arrays)
Destructuring allows you to unpack values from arrays or properties from objects into distinct variables.

Examples:
```javascript
// Array Destructuring
let arr = [1, 2, 3];
let [a, b] = arr;
console.log(a, b);  // 1 2

// Object Destructuring
let obj = { name: 'Alice', age: 25 };
let { name, age } = obj;
console.log(name, age);  // Alice 25
```

---

## Modules: `import` and `export`
Modules allow you to split your code into reusable parts. `export` makes parts of your code available for use in other files, and `import` allows you to bring them in.

Example:
```javascript
// math.js (module)
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// main.js (importing)
import { add, subtract } from './math.js';
console.log(add(2, 3));  // 5
```

---

## Enhanced Object Literals
ES6 introduced shorthand syntax for object literals, making it easier to define methods and properties.

Example:
```javascript
let name = 'Alice';
let age = 25;

let person = {
  name,
  age,
  greet() {
    console.log(`Hello, ${this.name}!`);
  }
};

person.greet();  // Hello, Alice!
```

---

## Iterators and Generators
- **Iterators** are objects that allow custom iteration behavior.
- **Generators** are functions that can yield multiple values over time, pausing their execution.

Example:
```javascript
// Iterator
let arr = [1, 2, 3];
let iterator = arr[Symbol.iterator]();
console.log(iterator.next());  // { value: 1, done: false }
console.log(iterator.next());  // { value: 2, done: false }

// Generator
function* count() {
  yield 1;
  yield 2;
  yield 3;
}

let gen = count();
console.log(gen.next());  // { value: 1, done: false }
console.log(gen.next());  // { value: 2, done: false }
```

---

## Symbols and Iterables
- **Symbols** are unique, immutable identifiers used to create object properties.
- **Iterables** are objects that define an iterator method, enabling them to be used in loops like `for...of`.

Example:
```javascript
// Symbol
let unique = Symbol('description');
let obj = { [unique]: 'value' };
console.log(obj[unique]);  // value

// Iterable
let iterable = {
  data: [1, 2, 3],
  [Symbol.iterator]: function() {
    let index = 0;
    let data = this.data;
    return {
      next: function() {
        if (index < data.length) {
          return { value: data[index++], done: false };
        } else {
          return { done: true };
        }
      }
    };
  }
};

for (let num of iterable) {
  console.log(num);  // 1, 2, 3
}
```

---

## Conclusion

### Key Takeaways:
1. **Let and Const**: Use `let` for variables that change, and `const` for constants.
2. **Arrow Functions**: Provide a concise syntax and lexically bind `this`.
3. **Template Literals**: Make string manipulation easier with embedded expressions.
4. **Rest and Spread Operators**: Simplify working with arrays and objects.
5. **Destructuring**: Easily unpack values from arrays and objects.
6. **Modules**: Use `import` and `export` to organize code into reusable units.
7. **Generators**: Create functions that can pause and resume execution.
8. **Symbols**: Provide unique identifiers for object properties.

### Practical Exercise:
1. Use destructuring to extract values from an object and an array.
2. Write a generator function that yields an infinite sequence of numbers.
3. Create a module that exports functions for basic arithmetic operations (addition, subtraction) and import it in another file.
4. Use the spread operator to merge two arrays, then use the rest operator to create a function that sums an unknown number of arguments.
5. Write a program that uses `let`, `const`, and `arrow functions` for a small project, such as a task manager or calculator.
