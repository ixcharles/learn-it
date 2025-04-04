
# Real-World Project Architecture

This guide dives into structuring large, maintainable Next.js projects with TypeScript, focusing on modular architecture, monorepos, reusability, scalability, and best practices for managing large codebases.

---

## Table of Contents

- [Modular Project Structure](#modular-project-structure)  
  - [Organizing Files and Folders](#organizing-files-and-folders)  
  - [Domain-Driven Design Patterns](#domain-driven-design-patterns)  
- [Monorepos with TurboRepo](#monorepos-with-turborepo)  
  - [Setting Up TurboRepo with Next.js](#setting-up-turborepo-with-nextjs)  
  - [Shared Types and Utils](#shared-types-and-utils)  
- [Reusability and Scalability](#reusability-and-scalability)  
  - [Design Systems with TypeScript](#design-systems-with-typescript)  
  - [Creating Internal Libraries](#creating-internal-libraries)  
- [Maintaining and Scaling Large Codebases](#maintaining-and-scaling-large-codebases)  
  - [Managing Types in Large Projects](#managing-types-in-large-projects)  
  - [Documentation and Type Safety Practices](#documentation-and-type-safety-practices)  

---

## Modular Project Structure

### Organizing Files and Folders  
Organizing your project files and folders into logical modules helps maintain a scalable architecture, reducing complexity as the project grows.

**Example:**
```
/src
  /components
    /Button
      index.tsx
      Button.styles.ts
      Button.test.tsx
  /pages
    /api
      /posts.ts
    index.tsx
  /utils
    dateUtils.ts
  /hooks
    useFetch.ts
```

### Domain-Driven Design Patterns  
Adopting domain-driven design (DDD) patterns enables you to break the project into bounded contexts, making it easier to manage complex logic and focus on domain-specific features.

**Example:**
```
/src
  /domain
    /user
      /models
        User.ts
      /services
        UserService.ts
      /repositories
        UserRepository.ts
```

---

## Monorepos with TurboRepo

### Setting Up TurboRepo with Next.js  
TurboRepo is a powerful tool for managing monorepos, allowing you to scale your Next.js app across multiple packages while maintaining a single codebase.

**Example:**
1. Install TurboRepo:
```bash
npx create-turbo@latest
```

2. Configure TurboRepo in the root directory:
```json
// turbo.json
{
  "pipeline": {
    "build": {
      "outputs": ["dist/**"]
    }
  }
}
```

3. Structure your monorepo:
```
/apps
  /web (Next.js app)
  /admin (Next.js app)
/packages
  /ui (UI library)
  /utils (Shared utilities)
```

### Shared Types and Utils  
In a monorepo, you can share types and utilities between different apps and packages to maintain consistency and reduce duplication.

**Example:**
```tsx
// packages/utils/dateUtils.ts
export function formatDate(date: Date): string {
  return date.toISOString().slice(0, 10);
}

// apps/web/pages/index.tsx
import { formatDate } from '@my-monorepo/utils/dateUtils';

const HomePage = () => {
  const today = formatDate(new Date());
  return <div>Today's date: {today}</div>;
};
```

---

## Reusability and Scalability

### Design Systems with TypeScript  
A design system helps standardize the user interface across applications. With TypeScript, you can ensure that your design system components are reusable and type-safe.

**Example:**
```tsx
// components/Button/Button.tsx
import React from 'react';

interface ButtonProps {
  label: string;
  onClick: () => void;
}

export const Button: React.FC<ButtonProps> = ({ label, onClick }) => (
  <button onClick={onClick}>{label}</button>
);

// apps/web/pages/index.tsx
import { Button } from '@my-monorepo/ui/Button';

const HomePage = () => (
  <div>
    <Button label="Click me" onClick={() => alert('Button clicked')} />
  </div>
);
```

### Creating Internal Libraries  
Creating internal libraries (e.g., for authentication, data fetching) helps centralize functionality, making it reusable across multiple projects.

**Example:**
```tsx
// packages/auth/src/index.ts
export const login = async (username: string, password: string) => {
  // Authentication logic
};

// apps/web/pages/login.tsx
import { login } from '@my-monorepo/auth';

const LoginPage = () => {
  const handleLogin = async () => {
    await login('username', 'password');
  };
  return <button onClick={handleLogin}>Login</button>;
};
```

---

## Maintaining and Scaling Large Codebases

### Managing Types in Large Projects  
In large projects, TypeScript types are crucial for maintaining consistency and ensuring scalability. Split types into reusable definitions and manage them centrally to reduce complexity.

**Example:**
```tsx
// types/global.d.ts
declare module 'my-app/types' {
  export interface Post {
    id: number;
    title: string;
    content: string;
  }
}

// pages/api/posts.ts
import { Post } from 'my-app/types';

export default async function handler(req, res) {
  const posts: Post[] = await fetchPostsFromDatabase();
  res.status(200).json(posts);
}
```

### Documentation and Type Safety Practices  
Ensure that all functions, components, and services are well-documented with JSDoc and types. Adopting consistent practices for typing and documenting can significantly reduce the chances of bugs and make the codebase easier to maintain.

**Example:**
```tsx
// utils/formatDate.ts
/**
 * Formats a Date object to a string (YYYY-MM-DD).
 * @param {Date} date - The date to format.
 * @returns {string} - The formatted date string.
 */
export function formatDate(date: Date): string {
  return date.toISOString().slice(0, 10);
}

// pages/index.tsx
import { formatDate } from 'my-app/utils/formatDate';

const HomePage = () => {
  const today = formatDate(new Date());
  return <div>Today's date: {today}</div>;
};
```

---

## Conclusion

**Key Takeaways:**
- A modular project structure and domain-driven design patterns help scale your project efficiently.
- Monorepos with TurboRepo allow for managing multiple applications and shared utilities under a single repository.
- Design systems and reusable components ensure consistency and scalability in the frontend.
- Maintaining large codebases requires effective management of types, documentation, and consistent coding practices.

---

## Practical Exercise

**Build a Fullstack E-Commerce App with a Modular Structure:**
1. Create a product catalog using a modular design where product-related logic (e.g., models, services, repositories) is encapsulated in its domain.
2. Set up a monorepo using TurboRepo and share utilities (e.g., date formatting, API helpers) between your `web` and `admin` apps.
3. Implement a design system with reusable components, such as buttons, input fields, and modals.
4. Create a library for managing user authentication and integrate it across both the web and admin applications.
