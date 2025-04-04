
# Basic TypeScript Syntax and Data Types

This course introduces the core syntax and data types in TypeScript. It covers how TypeScript improves upon JavaScript with type annotations, type inference, and more.

## Table of Contents

1. [Understanding Basic Types](#understanding-basic-types)
2. [Type Inference vs. Explicit Typing](#type-inference-vs-explicit-typing)
3. [Tuples and Arrays in TypeScript](#tuples-and-arrays-in-typescript)
4. [Enum Types and Const Enums](#enum-types-and-const-enums)
5. [Type Aliases and Interfaces](#type-aliases-and-interfaces)
6. [Null and Undefined in TypeScript](#null-and-undefined-in-typescript)

---

## Understanding Basic Types

TypeScript supports basic data types that are common in JavaScript, but with the added benefit of type annotations for better safety.

- **number**: Represents both integer and floating-point numbers.
- **string**: Represents textual data.
- **boolean**: Represents true or false values.
- **undefined**: Represents an uninitialized variable.
- **null**: Represents a value that is explicitly empty.

### Example:

```typescript
let age: number = 30;
let name: string = "John Doe";
let isActive: boolean = true;
```

---

## Type Inference vs. Explicit Typing

TypeScript can infer the type of a variable from its value, or you can explicitly define the type.

- **Type Inference**: TypeScript automatically infers the type.
- **Explicit Typing**: You manually define the type.

### Example of Type Inference:

```typescript
let count = 10;  // TypeScript infers that count is a number
```

### Example of Explicit Typing:

```typescript
let count: number = 10;  // Explicitly defines the type as number
```

---

## Tuples and Arrays in TypeScript

- **Arrays**: Lists of values of the same type.
- **Tuples**: Arrays with fixed sizes and specific types for each element.

### Arrays:

```typescript
let numbers: number[] = [1, 2, 3];
```

### Tuples:

```typescript
let person: [string, number] = ["John", 30];
```

---

## Enum Types and Const Enums

- **Enums**: A way to define a set of named constants.
- **Const Enums**: A version of enums that removes extra runtime code by replacing them with inline values during compilation.

### Example of Enum:

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let direction: Direction = Direction.Up;
```

### Example of Const Enum:

```typescript
const enum Direction {
  Up,
  Down,
  Left,
  Right
}

let direction: Direction = Direction.Up;
```

The key difference is that with `const enum`, the compiler inlines the values directly, removing the need for runtime overhead.

---

## Type Aliases and Interfaces

- **Type Aliases**: Create a new name for a type.
- **Interfaces**: Define the structure of an object (properties and methods).

### Type Aliases:

```typescript
type Point = { x: number, y: number };
let point: Point = { x: 5, y: 10 };
```

### Interfaces:

```typescript
interface Point {
  x: number;
  y: number;
}

let point: Point = { x: 5, y: 10 };
```

Interfaces are generally used for objects and can be extended, while type aliases are more flexible (e.g., for unions, intersections, etc.).

---

## Null and Undefined in TypeScript

In TypeScript, `null` and `undefined` are distinct types, and their usage can be controlled using strict null checks.

- **undefined**: Indicates a variable that has been declared but not assigned a value.
- **null**: Represents a variable that has been explicitly set to "no value."

### Example:

```typescript
let uninitialized: undefined = undefined;
let noValue: null = null;
```

To enable strict null checks and make these types more predictable, you can use the `--strictNullChecks` flag in `tsconfig.json`.

---

## Conclusion

### Key Takeaways:
1. TypeScript provides enhanced type safety with basic types like `number`, `string`, `boolean`, `null`, and `undefined`.
2. Type inference allows TypeScript to automatically determine the type, but explicit typing ensures stronger guarantees.
3. Tuples and arrays help manage lists, with tuples offering fixed-length and type-specific arrays.
4. Enums and Const Enums simplify handling sets of constants with or without runtime overhead.
5. Type aliases and interfaces define custom types for objects and structures, improving code readability and maintainability.

### Practical Exercise:
1. Create a `Person` type using both `type alias` and `interface`. Use the `Person` type in an array of multiple people.
2. Create a simple enum for a traffic light (`Red`, `Yellow`, `Green`) and use it in a function to simulate traffic light changes.
3. Declare variables with explicit types and allow TypeScript to infer types, then compare the results.
