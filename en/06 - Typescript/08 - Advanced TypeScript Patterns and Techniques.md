
# Advanced TypeScript Patterns and Techniques

This course explores advanced patterns in TypeScript, focusing on conditional logic, type transformations, and metaprogramming capabilities. These tools enable scalable, expressive, and reusable type-safe code in complex applications.

## Table of Contents

1. [Conditional and Mapped Types](#conditional-and-mapped-types)  
2. [Utility Types: Partial, Pick, Omit, etc.](#utility-types-partial-pick-omit-etc)  
3. [Advanced Inference and Type Manipulation](#advanced-inference-and-type-manipulation)  
4. [Decorators in TypeScript](#decorators-in-typescript)  
5. [Mixins and Composition Patterns](#mixins-and-composition-patterns)  
6. [Template Literal Types and Infer Keyword](#template-literal-types-and-infer-keyword)  

---

## Conditional and Mapped Types

Conditional types allow branching based on type logic, and mapped types iterate over properties to transform them.

### Example:

```typescript
type IsString<T> = T extends string ? true : false;

type ReadonlyProps<T> = {
  readonly [K in keyof T]: T[K];
};

type Example = ReadonlyProps<{ a: number; b: string }>;
// { readonly a: number; readonly b: string }
```

---

## Utility Types: Partial, Pick, Omit, etc.

TypeScript includes built-in helpers for common transformations like making properties optional or selecting specific fields.

### Examples:

```typescript
type User = { id: number; name: string; email: string };

type PartialUser = Partial<User>;
type UserPreview = Pick<User, "id" | "name">;
type WithoutEmail = Omit<User, "email">;
```

---

## Advanced Inference and Type Manipulation

The `infer` keyword extracts types from structures dynamically, useful in generic constraints and conditional types.

### Example:

```typescript
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

type Result = ReturnType<() => number>;  // number
```

---

## Decorators in TypeScript

Decorators are functions that apply metadata or behavior to classes, methods, properties, etc. Requires `"experimentalDecorators": true` in `tsconfig.json`.

### Example:

```typescript
function Log(target: any, key: string) {
  console.log(`Decorated: ${key}`);
}

class Person {
  @Log
  sayHello() {
    console.log("Hello");
  }
}
```

---

## Mixins and Composition Patterns

Mixins enable sharing behavior across multiple classes without classical inheritance.

### Example:

```typescript
type Constructor<T = {}> = new (...args: any[]) => T;

function Timestamped<TBase extends Constructor>(Base: TBase) {
  return class extends Base {
    timestamp = Date.now();
  };
}

class Note {}
const TimestampedNote = Timestamped(Note);
```

---

## Template Literal Types and Infer Keyword

Template literal types allow construction of string types dynamically. Combined with `infer`, they create powerful type logic.

### Example:

```typescript
type EventName = `on${Capitalize<string>}`;

type ExtractValue<T> = T extends { value: infer V } ? V : never;

type Test = ExtractValue<{ value: number }>;  // number
```

---

## Conclusion

### Key Takeaways:
1. Conditional and mapped types allow flexible, reusable type definitions.
2. Utility types simplify common object transformations.
3. `infer` enables extraction of inner types for dynamic logic.
4. Decorators provide metadata and behavioral enhancements in OOP.
5. Mixins and composition patterns help build modular, reusable classes.
6. Template literal types bring compile-time string manipulation into the type system.

### Practical Exercise:
1. Create a conditional type `IsNumber<T>` that returns `"yes"` if `T` is `number`, otherwise `"no"`.
2. Write a mapped type `Mutable<T>` that removes `readonly` from each property.
3. Use a class decorator to log a message when a class is instantiated.
4. Implement a mixin that adds an `id` property to any class.
5. Use a template literal type to define valid event names like `onClick`, `onHover`.
