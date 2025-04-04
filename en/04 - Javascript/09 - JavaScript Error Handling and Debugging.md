
# JavaScript Error Handling and Debugging

This course focuses on handling errors in JavaScript and debugging techniques. Learn how to manage errors, use debugging tools, and optimize performance for building robust JavaScript applications.

## Table of Contents
1. [Types of Errors in JavaScript](#types-of-errors-in-javascript)
2. [Handling Synchronous Errors](#handling-synchronous-errors)
3. [Handling Asynchronous Errors](#handling-asynchronous-errors)
4. [Using `try`, `catch`, `finally`](#using-try-catch-finally)
5. [Debugging with Breakpoints](#debugging-with-breakpoints)
6. [Using DevTools to Debug](#using-devtools-to-debug)
7. [Logging with `console`](#logging-with-console)
8. [Profiling and Performance Optimization](#profiling-and-performance-optimization)
9. [Creating Custom Errors](#creating-custom-errors)
10. [Writing Unit Tests for JavaScript](#writing-unit-tests-for-javascript)

---

## Types of Errors in JavaScript
JavaScript has three main types of errors:
1. **Syntax Errors**: Errors in code structure (e.g., missing parentheses).
2. **Runtime Errors**: Errors that occur while the script is running (e.g., undefined variables).
3. **Logical Errors**: Errors in the logic of the code, where the program runs without crashing but produces incorrect results.

Example:
```javascript
// Syntax Error
let x = (10 + 5;  // Missing closing parenthesis

// Runtime Error
let y;
console.log(y.someMethod());  // TypeError: Cannot read property 'someMethod' of undefined
```

---

## Handling Synchronous Errors
Synchronous errors occur during the execution of code. These are typically handled using `try`, `catch`, and `finally`.

Example:
```javascript
try {
  let result = 10 / 0;
  console.log(result);
} catch (error) {
  console.log('Caught an error:', error);
} finally {
  console.log('This will run no matter what');
}
```

---

## Handling Asynchronous Errors
Asynchronous errors occur in promises or callbacks. Handle them using `.catch()` for promises or `try...catch` with `async/await`.

Example with Promises:
```javascript
fetch('https://api.example.com')
  .then(response => response.json())
  .catch(error => console.log('Error fetching data:', error));
```

Example with Async/Await:
```javascript
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.log('Error:', error);
  }
}
```

---

## Using `try`, `catch`, `finally`
The `try...catch` block is used for handling errors in both synchronous and asynchronous code. The `finally` block executes code after the `try` or `catch` block, regardless of the outcome.

Example:
```javascript
try {
  let value = JSON.parse('invalid JSON');
} catch (error) {
  console.log('Parsing error:', error);
} finally {
  console.log('This always runs');
}
```

---

## Debugging with Breakpoints
Breakpoints allow you to pause code execution at a specific line to inspect variables and flow. You can set breakpoints in the browser DevTools.

Steps:
1. Open DevTools (F12 or Right-click > Inspect).
2. Navigate to the "Sources" tab.
3. Find the desired line of code.
4. Click on the line number to set a breakpoint.
5. Reload the page and the execution will stop at the breakpoint, allowing inspection.

---

## Using DevTools to Debug
DevTools provides powerful features to debug JavaScript code:
1. **Console**: View errors, warnings, and log statements.
2. **Debugger**: Pause code at breakpoints and step through execution.
3. **Watch Variables**: Monitor variables' values in real-time.
4. **Call Stack**: View the sequence of function calls leading to an error.
5. **Network Tab**: Check network requests and responses.

---

## Logging with `console`
The `console` object helps with debugging by logging information to the console.

Examples:
```javascript
console.log('Hello, World!');
console.warn('This is a warning');
console.error('An error occurred');
console.table([{ name: 'Alice', age: 25 }, { name: 'Bob', age: 30 }]);
```

---

## Profiling and Performance Optimization
Use DevTools' **Performance Tab** to analyze the runtime performance of your application. It helps identify bottlenecks like memory leaks, long task durations, or inefficient rendering.

Steps:
1. Open DevTools > Performance Tab.
2. Click "Start profiling" and interact with your app.
3. Click "Stop" to analyze the recorded data.

Optimize performance by reducing DOM manipulations, using `requestAnimationFrame` for animations, and minimizing synchronous tasks.

---

## Creating Custom Errors
You can create custom error types by extending the built-in `Error` class, which allows you to provide more specific error messages and stack traces.

Example:
```javascript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = 'ValidationError';
  }
}

try {
  throw new ValidationError('Invalid input');
} catch (error) {
  console.log(error.name);  // ValidationError
  console.log(error.message);  // Invalid input
}
```

---

## Writing Unit Tests for JavaScript
Unit tests verify that individual parts of your code behave as expected. Frameworks like Jest, Mocha, and Jasmine help automate testing.

Example with Jest:
```javascript
function sum(a, b) {
  return a + b;
}

test('sum adds two numbers correctly', () => {
  expect(sum(1, 2)).toBe(3);
});
```

Steps:
1. Install Jest: `npm install --save-dev jest`
2. Run tests: `npx jest`

---

## Conclusion

### Key Takeaways:
1. **Types of Errors**: Know the difference between syntax, runtime, and logical errors.
2. **Error Handling**: Use `try`, `catch`, and `finally` to handle errors, and handle asynchronous errors with `.catch()` or `async/await`.
3. **DevTools**: Utilize breakpoints, the console, and the performance tab for efficient debugging and optimization.
4. **Custom Errors**: Create custom error types by extending the `Error` class for better error handling.
5. **Unit Testing**: Write unit tests using frameworks like Jest to ensure your code works as expected.

### Practical Exercise:
1. Write a function that fetches data from an API and handles errors using `async/await` and `try...catch`.
2. Use DevTools to debug a simple JavaScript function, setting breakpoints and inspecting variables.
3. Create a custom error class, `DataNotFoundError`, and use it to throw and catch errors in a function that searches for data in an array.
4. Write a simple unit test for a function that calculates the area of a rectangle.
