
# Fundamentals of Next.js with TypeScript

A concise, hands-on guide to mastering the foundational concepts of Next.js paired with TypeScript, enabling scalable and type-safe React development.

---

## Table of Contents

- [Introduction to Next.js and TypeScript](#introduction-to-nextjs-and-typescript)  
  - [What is Next.js](#what-is-nextjs)  
  - [Why TypeScript with Next.js](#why-typescript-with-nextjs)  
- [Project Setup and Configuration](#project-setup-and-configuration)  
  - [Installing Next.js with TypeScript](#installing-nextjs-with-typescript)  
  - [Configuring tsconfig.json](#configuring-tsconfigjson)  
  - [Understanding Next.js File Structure](#understanding-nextjs-file-structure)  
- [Pages and Routing Basics](#pages-and-routing-basics)  
  - [Pages as Routes](#pages-as-routes)  
  - [Dynamic Routes](#dynamic-routes)  
  - [Nested Routes](#nested-routes)  
  - [Catch-all Routes](#catch-all-routes)  
- [Components and Props with TypeScript](#components-and-props-with-typescript)  
  - [Function Components with TypeScript](#function-components-with-typescript)  
  - [Typing Props and Children](#typing-props-and-children)  
  - [Default Props and Optional Props](#default-props-and-optional-props)  
- [Static Assets and Styling](#static-assets-and-styling)  
  - [Using CSS Modules](#using-css-modules)  
  - [Tailwind CSS Integration](#tailwind-css-integration)  
  - [Global Styles and Scoped Styles](#global-styles-and-scoped-styles)  
- [Basic Data Fetching](#basic-data-fetching)  
  - [getStaticProps](#getstaticprops)  
  - [getServerSideProps](#getserversideprops)  
  - [getStaticPaths](#getstaticpaths)  

---

## Introduction to Next.js and TypeScript

### What is Next.js  
A React framework for building production-grade applications with SSR, static generation, and hybrid rendering.

**Example:**
```bash
npx create-next-app my-app
```

### Why TypeScript with Next.js  
TypeScript adds static typing to improve code reliability and developer experience in large-scale applications.

**Example:**
```ts
const title: string = "Hello, Next.js + TS";
```

---

## Project Setup and Configuration

### Installing Next.js with TypeScript  
Start a TypeScript-enabled Next.js app using the CLI.

**Example:**
```bash
npx create-next-app@latest --typescript
```

### Configuring `tsconfig.json`  
Defines compiler options and type checking behavior for the project.

**Example:**
```json
{
  "compilerOptions": {
    "strict": true,
    "baseUrl": ".",
    "paths": { "@/*": ["src/*"] }
  }
}
```

### Understanding Next.js File Structure  
Next.js relies on a convention-based file structure.

**Example:**
```
/pages - Routes
/public - Static assets
/styles - Global CSS
```

---

## Pages and Routing Basics

### Pages as Routes  
Files in `/pages` automatically become routes.

**Example:**
```tsx
// pages/about.tsx
export default function About() {
  return <h1>About Page</h1>;
}
```

### Dynamic Routes  
Use `[param].tsx` to define dynamic segments.

**Example:**
```tsx
// pages/post/[id].tsx
export default function Post({ params }: any) {
  return <p>Post: {params.id}</p>;
}
```

### Nested Routes  
Create folder hierarchies in `/pages` for nested URLs.

**Example:**
```
/pages/blog/index.tsx → /blog  
/pages/blog/post.tsx → /blog/post
```

### Catch-all Routes  
Use `[...slug].tsx` for matching multiple path segments.

**Example:**
```tsx
// pages/docs/[...slug].tsx
```

---

## Components and Props with TypeScript

### Function Components with TypeScript  
Define types for props directly in the function signature.

**Example:**
```tsx
type Props = { title: string };
const Header: React.FC<Props> = ({ title }) => <h1>{title}</h1>;
```

### Typing Props and Children  
Type `children` explicitly when needed.

**Example:**
```tsx
type LayoutProps = { children: React.ReactNode };
const Layout = ({ children }: LayoutProps) => <main>{children}</main>;
```

### Default Props and Optional Props  
Use `?` for optional props and set defaults manually.

**Example:**
```tsx
type Props = { subtitle?: string };
const Header = ({ subtitle = "Default" }: Props) => <h2>{subtitle}</h2>;
```

---

## Static Assets and Styling

### Using CSS Modules  
Scoped styles with automatic class name hashing.

**Example:**
```tsx
import styles from './Button.module.css';
```

### Tailwind CSS Integration  
Utility-first CSS framework for rapid styling.

**Example:**
```tsx
<button className="bg-blue-500 text-white p-2 rounded">Click Me</button>
```

### Global Styles and Scoped Styles  
Global styles go in `pages/_app.tsx`.

**Example:**
```tsx
import '../styles/globals.css';
```

---

## Basic Data Fetching

### `getStaticProps`  
Fetch data at build time for static generation.

**Example:**
```tsx
export async function getStaticProps() {
  return { props: { data: 'static content' } };
}
```

### `getServerSideProps`  
Fetch data on every request, server-side.

**Example:**
```tsx
export async function getServerSideProps() {
  return { props: { data: 'server content' } };
}
```

### `getStaticPaths`  
Used with dynamic pages to pre-generate paths.

**Example:**
```tsx
export async function getStaticPaths() {
  return { paths: [{ params: { id: '1' } }], fallback: false };
}
```

---

## Conclusion

**Key Takeaways:**
- Next.js + TypeScript offers a powerful, scalable fullstack framework.
- Routing is file-based and dynamic routes are easy to implement.
- Static generation and SSR are first-class features.
- TypeScript improves safety and maintainability.
- Component typing and structured project setup are essential for growth.

---

## Practical Exercise

**Create a small blog homepage:**
1. Scaffold a new Next.js + TypeScript app.
2. Create a `/pages/index.tsx` file that fetches and displays mock post titles using `getStaticProps`.
3. Add a styled `Header` component with typed props.
4. Use CSS Modules or Tailwind CSS for styling.
