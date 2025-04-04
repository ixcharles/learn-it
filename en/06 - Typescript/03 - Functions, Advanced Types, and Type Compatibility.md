
# Functions, Advanced Types, and Type Compatibility

This course covers advanced TypeScript concepts including function declarations, optional parameters, function overloading, advanced types like union and intersection, and type compatibility. You'll also learn about type assertions and type guards for improved type safety.

## Table of Contents

1. [Function Declaration, Expression, and Arrow Functions](#function-declaration-expression-and-arrow-functions)
2. [Optional and Default Parameters](#optional-and-default-parameters)
3. [Function Overloading in TypeScript](#function-overloading-in-typescript)
4. [Advanced Types: Union, Intersection, Literal, and Conditional Types](#advanced-types-union-intersection-literal-and-conditional-types)
5. [Type Compatibility and Structural Subtyping](#type-compatibility-and-structural-subtyping)
6. [Type Assertion and Type Guards](#type-assertion-and-type-guards)

---

## Function Declaration, Expression, and Arrow Functions

- **Function Declaration**: Standard function declaration.
- **Function Expression**: Functions assigned to variables.
- **Arrow Functions**: Shorter syntax for writing functions with lexical `this` binding.

### Function Declaration:

```typescript
function add(x: number, y: number): number {
  return x + y;
}
```

### Function Expression:

```typescript
const add = function(x: number, y: number): number {
  return x + y;
};
```

### Arrow Function:

```typescript
const add = (x: number, y: number): number => x + y;
```

---

## Optional and Default Parameters

- **Optional Parameters**: Parameters that can be omitted during function calls.
- **Default Parameters**: Parameters that have a default value if not provided.

### Optional Parameters:

```typescript
function greet(name: string, age?: number): string {
  return `Hello, ${name}${age ? ', Age: ' + age : ''}`;
}
```

### Default Parameters:

```typescript
function greet(name: string, age: number = 30): string {
  return `Hello, ${name}, Age: ${age}`;
}
```

---

## Function Overloading in TypeScript

Function overloading allows you to define multiple function signatures for a single function, offering flexibility based on different input types.

### Example:

```typescript
function greet(name: string): string;
function greet(name: string, age: number): string;
function greet(name: string, age?: number): string {
  return age ? `Hello, ${name}, Age: ${age}` : `Hello, ${name}`;
}

greet("Alice");
greet("Bob", 30);
```

---

## Advanced Types: Union, Intersection, Literal, and Conditional Types

- **Union Types**: A variable can hold one of several types.
- **Intersection Types**: Combines multiple types into one.
- **Literal Types**: Restricts a variable to a specific value.
- **Conditional Types**: Types based on a condition.

### Union Types:

```typescript
let value: string | number = "Hello";
value = 10;
```

### Intersection Types:

```typescript
interface Name {
  name: string;
}

interface Age {
  age: number;
}

type Person = Name & Age;

let person: Person = { name: "Alice", age: 25 };
```

### Literal Types:

```typescript
let status: "success" | "error" = "success";
```

### Conditional Types:

```typescript
type IsString<T> = T extends string ? "Yes" : "No";
type Result = IsString<string>;  // Result is "Yes"
```

---

## Type Compatibility and Structural Subtyping

Type compatibility in TypeScript is based on structural typing, meaning that types are compatible if their structures (i.e., properties and methods) match, not necessarily their names.

### Example:

```typescript
interface Animal {
  name: string;
  sound: string;
}

interface Dog extends Animal {
  breed: string;
}

let dog: Dog = { name: "Buddy", sound: "Bark", breed: "Golden Retriever" };
let animal: Animal = dog;  // Valid due to structural subtyping
```

---

## Type Assertion and Type Guards

- **Type Assertion**: Tells TypeScript to treat a variable as a specific type.
- **Type Guards**: Functions or conditions used to narrow down the type of a variable.

### Type Assertion:

```typescript
let value: any = "Hello, TypeScript!";
let strLength: number = (value as string).length;
```

### Type Guards:

```typescript
function isString(value: any): value is string {
  return typeof value === "string";
}

let value: string | number = "Hello";
if (isString(value)) {
  console.log(value.length);  // TypeScript knows value is a string here
}
```

---

## Conclusion

### Key Takeaways:
1. TypeScript supports multiple ways to declare functions: declaration, expression, and arrow functions.
2. You can use optional and default parameters to make functions more flexible.
3. Function overloading allows you to define multiple function signatures for the same function.
4. Advanced types like union, intersection, literal, and conditional types enhance TypeScript’s flexibility and safety.
5. Type compatibility is based on structural typing, and type assertions and guards help ensure accurate type handling.

### Practical Exercise:
1. Write a function with both optional and default parameters. Create a few test cases to validate its behavior.
2. Create a union type for different user roles (`"admin" | "user" | "guest"`) and use it in a function that performs different actions based on the role.
3. Implement a type guard function to check if a given value is an array and safely access array methods.
