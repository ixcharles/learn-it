
# Advanced Functions and Functional Programming

This course explores advanced concepts in JavaScript functions and functional programming, providing you with powerful tools for writing clean, efficient, and reusable code. Topics range from higher-order functions to asynchronous programming with promises.

## Table of Contents
1. [Higher-Order Functions](#higher-order-functions)
2. [Closures](#closures)
3. [Function Currying](#function-currying)
4. [Recursion](#recursion)
5. [`bind`, `call`, and `apply` Methods](#bind-call-and-apply-methods)
6. [The Module Pattern](#the-module-pattern)
7. [IIFE (Immediately Invoked Function Expressions)](#iife-immediately-invoked-function-expressions)
8. [Async Functions and Promises](#async-functions-and-promises)

---

## Higher-Order Functions
Higher-order functions are functions that either take other functions as arguments or return a function as a result.

Example:
```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

function sayHello(func, name) {
  return func(name);
}

console.log(sayHello(greet, 'Alice'));  // Hello, Alice!
```

---

## Closures
A closure is a function that retains access to its lexical environment, even after the outer function has finished executing.

Example:
```javascript
function outer() {
  let counter = 0;
  return function inner() {
    counter++;
    console.log(counter);
  };
}

let counterFunction = outer();
counterFunction();  // 1
counterFunction();  // 2
```

---

## Function Currying
Currying is the process of transforming a function that takes multiple arguments into a sequence of functions that each take one argument.

Example:
```javascript
function multiply(a) {
  return function(b) {
    return a * b;
  };
}

let multiplyBy2 = multiply(2);
console.log(multiplyBy2(3));  // 6
```

---

## Recursion
Recursion occurs when a function calls itself to solve a smaller instance of the same problem. It is typically used for problems that can be broken down into smaller subproblems.

Example:
```javascript
function factorial(n) {
  if (n === 0) return 1;
  return n * factorial(n - 1);
}

console.log(factorial(5));  // 120
```

---

## `bind`, `call`, and `apply` Methods
These methods allow you to control the context (`this`) of a function.

- `bind`: Returns a new function with a specified `this` value.
- `call`: Calls a function with a specified `this` value and arguments.
- `apply`: Similar to `call`, but arguments are passed as an array.

Example:
```javascript
let person = { name: 'Alice' };

function greet(greeting) {
  console.log(`${greeting}, ${this.name}!`);
}

let greetAlice = greet.bind(person);
greetAlice('Hello');  // Hello, Alice!

greet.call(person, 'Hi');  // Hi, Alice!
greet.apply(person, ['Good evening']);  // Good evening, Alice!
```

---

## The Module Pattern
The module pattern is a way to organize code in JavaScript by creating private and public methods within a single object or function. It helps with encapsulation and avoiding global scope pollution.

Example:
```javascript
let counterModule = (function() {
  let count = 0;

  return {
    increment: function() {
      count++;
      console.log(count);
    },
    decrement: function() {
      count--;
      console.log(count);
    }
  };
})();

counterModule.increment();  // 1
counterModule.decrement();  // 0
```

---

## IIFE (Immediately Invoked Function Expressions)
An IIFE is a function expression that is executed immediately after its creation, often used to create a new scope to avoid polluting the global namespace.

Example:
```javascript
(function() {
  let message = 'I am an IIFE!';
  console.log(message);
})();  // I am an IIFE!
```

---

## Async Functions and Promises
Async functions allow you to write asynchronous code in a synchronous style using the `async` and `await` keywords. Promises represent the eventual completion (or failure) of an asynchronous operation.

Example:
```javascript
// Using Promise
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve('Data fetched!'), 1000);
  });
}

fetchData().then(data => console.log(data));  // Data fetched!

// Using Async/Await
async function fetchDataAsync() {
  let data = await fetchData();
  console.log(data);  // Data fetched!
}

fetchDataAsync();
```

---

## Conclusion

### Key Takeaways:
1. Higher-order functions enable functional programming paradigms by passing functions as arguments or returning functions.
2. Closures allow inner functions to retain access to variables from their outer function.
3. Function currying breaks down functions into smaller, reusable parts.
4. Recursion is a powerful technique for solving problems that can be divided into smaller subproblems.
5. The `bind`, `call`, and `apply` methods are essential for controlling the `this` context of functions.
6. The module pattern encapsulates code, providing privacy and avoiding polluting the global scope.
7. IIFE enables immediate execution of functions, useful for creating isolated scopes.
8. Async/await simplifies working with asynchronous code, making it easier to read and maintain.

### Practical Exercise:
1. Write a function using recursion to calculate the nth Fibonacci number.
2. Implement a currying function that calculates the sum of multiple numbers.
3. Create a module that manages a to-do list, with methods for adding, removing, and listing tasks.
4. Refactor an existing callback-based asynchronous function using `async/await`.
