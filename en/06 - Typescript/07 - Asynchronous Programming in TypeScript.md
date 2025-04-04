
# Asynchronous Programming in TypeScript

This course explores how TypeScript enhances asynchronous programming through strong typing of callbacks, Promises, and `async/await`. You'll also learn how to handle errors effectively and integrate TypeScript with APIs like Fetch and Axios.

## Table of Contents

1. [Callbacks, Promises, and async/await in TypeScript](#callbacks-promises-and-asyncawait-in-typescript)  
2. [Working with TypeScript's Promise Types](#working-with-typescripts-promise-types)  
3. [Typing async functions and Promise chains](#typing-async-functions-and-promise-chains)  
4. [Error Handling in Asynchronous Code](#error-handling-in-asynchronous-code)  
5. [Using TypeScript with Fetch API or Axios](#using-typescript-with-fetch-api-or-axios)  

---

## Callbacks, Promises, and async/await in TypeScript

TypeScript supports multiple async patterns: callbacks, Promises, and `async/await`, with full type safety.

### Example: Promises with async/await

```typescript
function fetchData(): Promise<string> {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Data loaded"), 1000);
  });
}

async function load() {
  const result = await fetchData();
  console.log(result);
}

load();
```

---

## Working with TypeScript's Promise Types

Promise-returning functions should have return types like `Promise<Type>` for clarity and type inference.

### Example:

```typescript
function getUser(): Promise<{ name: string; age: number }> {
  return Promise.resolve({ name: "Alice", age: 30 });
}

getUser().then(user => console.log(user.name));
```

---

## Typing async functions and Promise chains

Async functions automatically return a `Promise<Type>`. Explicit typing ensures clarity and consistency.

### Example:

```typescript
async function getMessage(): Promise<string> {
  return "Hello, world!";
}

getMessage().then((msg: string) => console.log(msg));
```

---

## Error Handling in Asynchronous Code

Use `try/catch` for async/await and `.catch()` for Promises to manage errors.

### Example:

```typescript
async function riskyTask(): Promise<void> {
  try {
    const result = await fetchData();
    console.log(result);
  } catch (error) {
    console.error("Error occurred:", error);
  }
}
```

---

## Using TypeScript with Fetch API or Axios

Both Fetch and Axios work seamlessly with TypeScript. You can define response types to ensure safe data access.

### Example with Fetch:

```typescript
interface Post {
  id: number;
  title: string;
}

async function getPost(): Promise<Post> {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts/1");
  const data: Post = await res.json();
  return data;
}
```

### Example with Axios:

```typescript
import axios from "axios";

interface Post {
  id: number;
  title: string;
}

async function getPost(): Promise<Post> {
  const res = await axios.get<Post>("https://jsonplaceholder.typicode.com/posts/1");
  return res.data;
}
```

---

## Conclusion

### Key Takeaways:
1. TypeScript supports multiple async paradigms with type safety.
2. Use `Promise<Type>` to clearly express return types for async operations.
3. Always handle errors in async code with `try/catch` or `.catch()`.
4. Typing async functions helps prevent runtime errors.
5. Fetch and Axios integrate smoothly with TypeScript for safe API handling.

### Practical Exercise:
1. Write an `async` function `getUserData` that returns a typed `User` object after 1 second using a `Promise`.
2. Use both `.then()` and `async/await` to call it.
3. Add a simulated failure and handle the error properly with a `try/catch` block.
