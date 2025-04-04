
# Generics in TypeScript

This course dives into TypeScript generics—a powerful feature that allows you to write reusable, type-safe code. You’ll learn how to use generics in functions, interfaces, classes, and advanced patterns to make your code more flexible and robust.

## Table of Contents

1. [Introduction to Generics](#introduction-to-generics)
2. [Generic Functions and Constraints](#generic-functions-and-constraints)
3. [Generic Interfaces and Classes](#generic-interfaces-and-classes)
4. [Using Multiple Type Parameters](#using-multiple-type-parameters)
5. [Advanced Generic Patterns: Default Types and Conditional Types](#advanced-generic-patterns-default-types-and-conditional-types)
6. [Type Inference with Generics](#type-inference-with-generics)

---

## Introduction to Generics

Generics provide a way to define reusable components that work with a variety of types without losing type safety.

### Example:

```typescript
function identity<T>(value: T): T {
  return value;
}

const numberResult = identity<number>(42);
const stringResult = identity("hello"); // inferred as string
```

---

## Generic Functions and Constraints

You can constrain generic types to ensure they meet certain criteria using `extends`.

### Example (with constraint):

```typescript
function getLength<T extends { length: number }>(value: T): number {
  return value.length;
}

getLength("hello"); // valid
getLength([1, 2, 3]); // valid
// getLength(123); // error: number doesn't have a length property
```

---

## Generic Interfaces and Classes

Generics can be applied to interfaces and classes to define reusable structures.

### Generic Interface:

```typescript
interface Box<T> {
  value: T;
}

const stringBox: Box<string> = { value: "TypeScript" };
```

### Generic Class:

```typescript
class Container<T> {
  private content: T;

  constructor(value: T) {
    this.content = value;
  }

  get(): T {
    return this.content;
  }
}

const numberContainer = new Container<number>(123);
```

---

## Using Multiple Type Parameters

You can define functions, classes, or interfaces with more than one type parameter.

### Example:

```typescript
function merge<T, U>(a: T, b: U): T & U {
  return { ...a, ...b };
}

const merged = merge({ name: "Alice" }, { age: 30 });
// merged is inferred as { name: string; age: number }
```

---

## Advanced Generic Patterns: Default Types and Conditional Types

You can assign default types and use conditional logic within generic types.

### Default Type Parameters:

```typescript
type ApiResponse<T = any> = {
  data: T;
  error?: string;
};

const response: ApiResponse<string> = { data: "Success" };
```

### Conditional Types:

```typescript
type IsArray<T> = T extends any[] ? "array" : "not array";

type A = IsArray<number[]>; // "array"
type B = IsArray<number>;   // "not array"
```

---

## Type Inference with Generics

TypeScript can often infer generic types from provided arguments, reducing the need to explicitly annotate them.

### Example:

```typescript
function wrap<T>(value: T): { value: T } {
  return { value };
}

const wrapped = wrap("inferred"); // inferred as string
```

You can still provide types explicitly when needed:

```typescript
const explicit = wrap<number>(42);
```

---

## Conclusion

### Key Takeaways:
1. Generics enable reusable and type-safe components that work across multiple types.
2. You can constrain generic types to ensure certain structure or behavior.
3. Interfaces and classes can be generic, enabling powerful data modeling.
4. Multiple type parameters allow combining and merging different type values.
5. Advanced generic features include default types, conditional types, and inference mechanisms.

### Practical Exercise:
1. Write a generic function `firstElement<T>` that returns the first element of an array of type `T[]`.
2. Create a generic interface `Result<T>` with properties `success: boolean` and `data: T | null`.
3. Use a conditional type to create `IsString<T>` that resolves to `true` if `T` is a `string`, otherwise `false`. Try it with multiple types.
