
# Testing, Debugging, and Best Practices in TypeScript

This course focuses on practical strategies for testing, debugging, and writing maintainable TypeScript code. It covers essential tooling like Jest, ESLint, and Prettier, along with best practices for type safety, error handling, and formatting.

## Table of Contents

1. [Unit Testing with TypeScript (Jest, Mocha)](#unit-testing-with-typescript-jest-mocha)  
2. [TypeScript Type Checking during Development](#typescript-type-checking-during-development)  
3. [Debugging TypeScript Code in IDEs](#debugging-typescript-code-in-ides)  
4. [Writing TypeScript with ESLint and Prettier](#writing-typescript-with-eslint-and-prettier)  
5. [TypeScript Code Linting and Formatting Best Practices](#typescript-code-linting-and-formatting-best-practices)  
6. [Error Handling Best Practices in TypeScript](#error-handling-best-practices-in-typescript)  

---

## Unit Testing with TypeScript (Jest, Mocha)

Use test runners like **Jest** or **Mocha** with TypeScript to write unit tests and ensure code correctness.

### Example with Jest:

```bash
npm install --save-dev jest ts-jest @types/jest
npx ts-jest config:init
```

```typescript
// sum.ts
export function sum(a: number, b: number): number {
  return a + b;
}

// sum.test.ts
import { sum } from './sum';

test('adds 1 + 2 = 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

---

## TypeScript Type Checking during Development

Enable `strict` mode in `tsconfig.json` for full type safety and early error detection.

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true
  }
}
```

Run the TypeScript compiler with:

```bash
tsc --noEmit
```

---

## Debugging TypeScript Code in IDEs

Modern IDEs like **VS Code** offer powerful TypeScript debugging tools with source maps.

### Debug Setup in VS Code:

```json
// .vscode/launch.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Debug TS",
      "program": "${workspaceFolder}/src/index.ts",
      "preLaunchTask": "tsc: build - tsconfig.json",
      "outFiles": ["${workspaceFolder}/dist/**/*.js"]
    }
  ]
}
```

Enable source maps in `tsconfig.json`:

```json
"sourceMap": true
```

---

## Writing TypeScript with ESLint and Prettier

Use **ESLint** for catching code issues and **Prettier** for automatic formatting.

### Setup:

```bash
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin prettier eslint-config-prettier eslint-plugin-prettier
```

### Sample `.eslintrc.js`:

```javascript
module.exports = {
  parser: '@typescript-eslint/parser',
  plugins: ['@typescript-eslint', 'prettier'],
  extends: ['plugin:@typescript-eslint/recommended', 'plugin:prettier/recommended'],
};
```

---

## TypeScript Code Linting and Formatting Best Practices

- Enable `noImplicitAny`, `strictNullChecks`, and `alwaysStrict`.
- Use Prettier to enforce consistent formatting (e.g., spacing, semicolons).
- Set up pre-commit hooks with **lint-staged** and **husky** for code quality.

### Example:

```json
"lint-staged": {
  "*.ts": ["eslint --fix", "prettier --write"]
}
```

---

## Error Handling Best Practices in TypeScript

- Always narrow error types using type guards.
- Avoid using `any` for `catch` blocks—use `unknown` and refine.
- Use custom error classes for clarity and structure.

### Example:

```typescript
try {
  throw new Error("Oops!");
} catch (err: unknown) {
  if (err instanceof Error) {
    console.error(err.message);
  }
}
```

---

## Conclusion

### Key Takeaways:
1. Use Jest or Mocha with ts-jest for effective TypeScript testing.
2. Enable strict type checking for safer and more predictable code.
3. Debug efficiently using source maps in modern IDEs like VS Code.
4. Use ESLint and Prettier to enforce consistent and clean code.
5. Handle errors using `unknown`, `instanceof`, and custom error types.

### Practical Exercise:
1. Create a simple function and write a unit test for it using Jest.
2. Enable strict mode in your `tsconfig.json` and refactor code to comply.
3. Add ESLint and Prettier to your project and run them on a sample file.
4. Write a try/catch block using `unknown` in error handling and log the message safely.
