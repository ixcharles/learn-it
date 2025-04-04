
# Modules and Namespaces in TypeScript

This course focuses on how to organize and modularize code in TypeScript using ES Modules and Namespaces. You'll also learn how to work with third-party libraries and explore advanced concepts like declaration merging.

## Table of Contents

1. [Working with ES Modules in TypeScript](#working-with-es-modules-in-typescript)  
2. [Import and Export Statements](#import-and-export-statements)  
3. [Namespace vs Module: Key Differences](#namespace-vs-module-key-differences)  
4. [Declaration Merging](#declaration-merging)  
5. [Using TypeScript with Third-Party Libraries (DefinitelyTyped, etc.)](#using-typescript-with-third-party-libraries-definitelytyped-etc)

---

## Working with ES Modules in TypeScript

TypeScript supports ECMAScript modules (`import`/`export`) to split code across files and promote reusability and organization.

### Example:

```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

// main.ts
import { add } from './math';

console.log(add(2, 3));
```

Make sure `tsconfig.json` includes `"module": "esnext"` or `"module": "commonjs"` depending on your environment.

---

## Import and Export Statements

Modules can export values (functions, classes, objects) using named or default exports, and these can be imported elsewhere.

### Named Export:

```typescript
// utils.ts
export const PI = 3.14;

// app.ts
import { PI } from './utils';
```

### Default Export:

```typescript
// logger.ts
export default function log(msg: string): void {
  console.log(msg);
}

// app.ts
import log from './logger';
```

---

## Namespace vs Module: Key Differences

- **Modules**: File-based; rely on `import`/`export`. Used in modern codebases.
- **Namespaces**: Internal module pattern using `namespace` keyword; useful when not using a module loader.

### Namespace Example:

```typescript
namespace Utils {
  export function greet(name: string): string {
    return `Hello, ${name}`;
  }
}

console.log(Utils.greet("Alice"));
```

**Note:** Avoid namespaces when using ES Modules—prefer module syntax for scalability.

---

## Declaration Merging

TypeScript allows interfaces and namespaces with the same name to merge into a single declaration, enhancing flexibility.

### Example:

```typescript
interface User {
  name: string;
}

namespace User {
  export function create(name: string): User {
    return { name };
  }
}

const newUser = User.create("Bob");
```

---

## Using TypeScript with Third-Party Libraries (DefinitelyTyped, etc.)

For libraries without built-in types, TypeScript uses **@types/** packages from [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

### Install and Use:

```bash
npm install lodash
npm install --save-dev @types/lodash
```

### Example:

```typescript
import _ from 'lodash';

const nums = [1, 2, 3];
console.log(_.reverse(nums));  // [3, 2, 1]
```

If no types are available, you can use a `*.d.ts` file with custom declarations.

---

## Conclusion

### Key Takeaways:
1. Use ES Modules (`import`/`export`) to structure modern TypeScript projects.
2. Named and default exports provide flexible ways to expose and use code across files.
3. Avoid `namespace` in favor of modules unless working in a non-module environment.
4. Declaration merging enhances flexibility, especially with interfaces and namespaces.
5. TypeScript integrates easily with third-party JS libraries using `@types`.

### Practical Exercise:
1. Create two separate files and export a function from one, importing and using it in the other.
2. Define a namespace with a function and an interface, then merge them.
3. Install and use a third-party library like `lodash` and use TypeScript to call one of its methods with type safety.
