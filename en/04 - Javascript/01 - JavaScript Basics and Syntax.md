
# JavaScript Basics and Syntax

JavaScript is the foundational programming language for web development, used for creating interactive and dynamic websites. This course covers the essential syntax and concepts needed to get started with JavaScript.

## Table of Contents
1. [Introduction to JavaScript](#introduction-to-javascript)
2. [Variables and Data Types](#variables-and-data-types)
3. [Operators and Expressions](#operators-and-expressions)
4. [Control Flow: if, else, switch](#control-flow-if-else-switch)
5. [Loops: for, while, do-while](#loops-for-while-do-while)
6. [Functions: Declaration, Expression, Arrow Functions](#functions-declaration-expression-arrow-functions)
7. [Scope and Hoisting](#scope-and-hoisting)
8. [Error Handling: try, catch, throw](#error-handling-try-catch-throw)
9. [Debugging with console and DevTools](#debugging-with-console-and-devtools)

---

## Introduction to JavaScript
JavaScript is a versatile, high-level programming language used for creating dynamic web pages. It allows interaction with HTML elements, making websites more interactive.

Example:
```javascript
console.log("Hello, World!");
```

---

## Variables and Data Types
Variables store data values. JavaScript has several data types, including numbers, strings, booleans, and objects.

Example:
```javascript
let name = "John";   // String
let age = 30;        // Number
let isAdult = true;  // Boolean
```

---

## Operators and Expressions
Operators perform operations on variables and values, such as arithmetic or comparison. Expressions are combinations of values, variables, and operators that evaluate to a result.

Example:
```javascript
let sum = 10 + 5;    // Arithmetic operator
let isEqual = (10 == 10); // Comparison operator
```

---

## Control Flow: if, else, switch
Control flow determines the direction of program execution. `if`, `else`, and `switch` are conditional statements used to control the flow.

Example:
```javascript
if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

---

## Loops: for, while, do-while
Loops are used to repeatedly execute code as long as a condition is true. Common types are `for`, `while`, and `do-while`.

Example:
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

---

## Functions: Declaration, Expression, Arrow Functions
Functions are reusable blocks of code. They can be declared, defined as expressions, or written in arrow function syntax.

Example:
```javascript
// Function Declaration
function greet(name) {
    console.log("Hello, " + name);
}

// Function Expression
const square = function(x) {
    return x * x;
};

// Arrow Function
const add = (a, b) => a + b;
```

---

## Scope and Hoisting
Scope defines the visibility of variables. Hoisting refers to JavaScript's behavior of moving declarations to the top of their scope.

Example:
```javascript
console.log(a); // undefined due to hoisting
var a = 10;
```

---

## Error Handling: try, catch, throw
Error handling allows developers to manage runtime errors using `try`, `catch`, and `throw` to handle exceptions safely.

Example:
```javascript
try {
    let result = 10 / 0;
    if (result === Infinity) throw "Cannot divide by zero";
} catch (error) {
    console.log(error);
}
```

---

## Debugging with console and DevTools
`console.log()` helps print outputs for debugging. Browser DevTools provide advanced tools like breakpoints and step-through debugging to examine the code flow.

Example:
```javascript
let x = 5;
console.log("Value of x:", x);  // Debugging with console.log
```

---

## Conclusion

### Key Takeaways:
1. JavaScript is crucial for building interactive web pages.
2. Variables, data types, and operators are fundamental to programming in JavaScript.
3. Control flow and loops allow for flexible program execution.
4. Functions enable code reuse and organization.
5. Debugging tools and error handling improve code reliability.

### Practical Exercise:
1. Create a simple JavaScript program that:
   - Takes a user's age as input.
   - Checks if the user is an adult or minor using an `if` statement.
   - Displays a message in the console using `console.log()`.
2. Experiment with different types of loops (`for`, `while`, `do-while`) to display numbers from 1 to 10.
