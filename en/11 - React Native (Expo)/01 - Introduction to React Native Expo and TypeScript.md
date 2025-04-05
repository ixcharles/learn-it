
# Introduction to React Native Expo and TypeScript

React Native with Expo and TypeScript is a powerful combination for building scalable, performant mobile apps using a type-safe, modern development stack. This course introduces the core tools and practices required to get started efficiently.

## Table of Contents
- [Overview of React Native and Expo](#overview-of-react-native-and-expo)
- [Setting Up the Development Environment](#setting-up-the-development-environment)
- [Understanding TypeScript Fundamentals](#understanding-typescript-fundamentals)
- [Creating a New Expo Project with TypeScript](#creating-a-new-expo-project-with-typescript)
- [Directory Structure and Best Practices](#directory-structure-and-best-practices)

---

## Overview of React Native and Expo

**Definition:**  
React Native is a framework for building native apps using React. Expo is a managed workflow that simplifies React Native development with a set of tools and services.

**Example:**  
With Expo, you can write one codebase in React and TypeScript and deploy it to iOS and Android instantly.

```bash
npx create-expo-app MyApp
```

Expo provides fast development, over-the-air updates, and access to device APIs without native code setup.

---

## Setting Up the Development Environment

**Definition:**  
To develop with Expo and TypeScript, you need Node.js, Expo CLI, and a code editor like VS Code.

**Example:**

```bash
npm install -g expo-cli
npx create-expo-app MyApp -t
cd MyApp
npm start
```

Use a mobile simulator or Expo Go app on your phone to preview your app instantly.

---

## Understanding TypeScript Fundamentals

**Definition:**  
TypeScript is a typed superset of JavaScript that enables static type-checking and better tooling.

**Example:**

```ts
type User = {
  name: string;
  age: number;
};

const greet = (user: User): string => `Hello, ${user.name}`;
```

TypeScript improves code safety and developer productivity in React Native projects.

---

## Creating a New Expo Project with TypeScript

**Definition:**  
Expo supports TypeScript out of the box with the `-t` flag when initializing a new project.

**Example:**

```bash
npx create-expo-app MyApp -t
```

This sets up TypeScript with a `tsconfig.json` file and `.tsx` entry points ready to go.

---

## Directory Structure and Best Practices

**Definition:**  
Organizing your project structure promotes maintainability and scalability.

**Example:**

```
MyApp/
├── assets/         # Images, fonts, etc.
├── components/     # Reusable UI components
├── screens/        # Navigation screens
├── types/          # Global TypeScript types
├── utils/          # Helpers and utility functions
├── App.tsx         # Entry point
└── tsconfig.json   # TypeScript configuration
```

Follow modular folder structures and keep concerns separated by domain or feature.

---

## Conclusion

**Key Takeaways:**
1. React Native + Expo simplifies cross-platform app development.
2. TypeScript enforces strong typing and reduces runtime errors.
3. Expo CLI provides instant setup with built-in TypeScript support.
4. A well-organized directory structure enhances project scalability.
5. Expo Go enables fast iteration and testing on real devices.

**Practical Exercise:**
- Set up a new Expo project with TypeScript.
- Create a `UserCard` component in the `components/` folder using a typed `User` prop.
- Display a sample user on the screen using a `HomeScreen` in the `screens/` folder.
