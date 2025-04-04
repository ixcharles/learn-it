
# Introduction to TypeScript and Setup

TypeScript is a statically typed superset of JavaScript that enhances the language by adding optional type annotations, interfaces, and other features that improve developer experience and maintainability. This course will walk you through the initial setup and basic understanding of TypeScript.

## Table of Contents

1. [What is TypeScript?](#what-is-typescript)
2. [Installing TypeScript and Setting Up a Project](#installing-typescript-and-setting-up-a-project)
3. [TypeScript Configuration (tsconfig.json)](#typescript-configuration-tsconfigjson)
4. [Understanding TypeScript Compilation Process](#understanding-typescript-compilation-process)
5. [Working with TypeScript in Editors (VS Code, etc.)](#working-with-typescript-in-editors-vs-code-etc)
6. [Running TypeScript Code: tsc vs. ts-node](#running-typescript-code-tsc-vs-ts-node)

---

## What is TypeScript?

TypeScript is a superset of JavaScript that adds static typing, which can help detect errors during development. It compiles down to plain JavaScript that runs in any JavaScript environment.

### Example:

```typescript
let message: string = "Hello, TypeScript!";
console.log(message);
```

---

## Installing TypeScript and Setting Up a Project

To get started with TypeScript, you need to install it globally or locally using npm.

### Installation (Global):

```bash
npm install -g typescript
```

### Installation (Local in Project):

```bash
npm install --save-dev typescript
```

You also need to initialize a new project by creating a `tsconfig.json` file (covered in the next section).

---

## TypeScript Configuration (tsconfig.json)

The `tsconfig.json` file contains TypeScript compiler options. It helps you configure how the TypeScript code is compiled.

### Example of `tsconfig.json`:

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist"
  },
  "include": ["src/**/*.ts"]
}
```

- `target`: Specifies the JavaScript version to compile to.
- `module`: Defines the module system.
- `strict`: Enables strict type-checking options.
- `outDir`: Specifies the output directory for compiled JS files.
- `include`: Files or directories to include in the compilation.

---

## Understanding TypeScript Compilation Process

TypeScript needs to be compiled into JavaScript before running. This process is done using the `tsc` (TypeScript Compiler) command.

### Example Command:

```bash
tsc
```

This command reads the `tsconfig.json` file and compiles the TypeScript files into JavaScript based on the configuration.

---

## Working with TypeScript in Editors (VS Code, etc.)

Using an editor like VS Code with TypeScript support helps with code completion, linting, and inline type checking.

1. Install VS Code.
2. Install the TypeScript plugin (though VS Code often supports TypeScript out of the box).
3. Open the TypeScript project folder and start coding!

VS Code offers features like IntelliSense and integrated terminal support to run TypeScript directly.

---

## Running TypeScript Code: tsc vs. ts-node

- `tsc`: Compiles TypeScript files into JavaScript.
- `ts-node`: A runtime that directly runs TypeScript files without compiling them first.

### Example using `tsc`:

```bash
tsc index.ts
```

This will compile `index.ts` to `index.js`.

### Example using `ts-node`:

```bash
npx ts-node index.ts
```

`ts-node` is faster for development as it eliminates the need for manual compilation.

---

## Conclusion

### Key Takeaways:
1. TypeScript is a statically typed superset of JavaScript that improves code quality and developer experience.
2. You can install TypeScript globally or locally in a project via npm.
3. The `tsconfig.json` file configures TypeScript compilation options.
4. TypeScript code needs to be compiled to JavaScript using `tsc`, or run directly with `ts-node`.
5. Editors like VS Code provide features like IntelliSense for efficient TypeScript development.

### Practical Exercise:
1. Install TypeScript locally in a project.
2. Create a `tsconfig.json` with the default settings.
3. Write a simple TypeScript file that logs a string and compile it using `tsc` and run it with `ts-node`.
