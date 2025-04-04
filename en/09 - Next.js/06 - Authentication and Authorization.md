
# Authentication and Authorization

Learn how to implement authentication and authorization in your Next.js app using TypeScript. Explore NextAuth.js, role-based access control, and securing routes and API endpoints.

---

## Table of Contents

- [NextAuth.js with TypeScript](#nextauthjs-with-typescript)  
  - [Configuration and Providers](#configuration-and-providers)  
  - [Typing Session and User Objects](#typing-session-and-user-objects)  
- [Role-based Access Control](#role-based-access-control)  
  - [Typed Guards and Middleware](#typed-guards-and-middleware)  
- [Protecting Routes and API Endpoints](#protecting-routes-and-api-endpoints)  
  - [Conditional Rendering with Types](#conditional-rendering-with-types)  
  - [Custom Hook for Auth Context](#custom-hook-for-auth-context)  

---

## NextAuth.js with TypeScript

### Configuration and Providers  
NextAuth.js integrates easily into Next.js for authentication with multiple providers like Google, GitHub, and more. TypeScript support ensures type-safe authentication.

**Example:**
```tsx
// pages/api/auth/[...nextauth].ts
import NextAuth from 'next-auth';
import GoogleProvider from 'next-auth/providers/google';

export default NextAuth({
  providers: [
    GoogleProvider({
      clientId: process.env.GOOGLE_CLIENT_ID!,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
    }),
  ],
});
```

### Typing Session and User Objects  
TypeScript allows you to type the session and user objects returned by NextAuth, ensuring type safety.

**Example:**
```tsx
// lib/nextAuth.d.ts
import { DefaultSession } from 'next-auth';

declare module 'next-auth' {
  interface Session {
    user: {
      id: string;
      name: string;
      email: string;
    };
  }
}

// Usage
import { useSession } from 'next-auth/react';

const Profile = () => {
  const { data: session } = useSession();
  if (session) {
    return <div>Welcome, {session.user.name}</div>;
  }
  return <div>Not authenticated</div>;
};
```

---

## Role-based Access Control

### Typed Guards and Middleware  
Role-based access control (RBAC) involves restricting access to routes and resources based on user roles. Typed guards and middleware help enforce this securely.

**Example:**
```tsx
// lib/guards.ts
export function withRole(role: string) {
  return (req: any, res: any, next: any) => {
    if (req.user.role !== role) {
      return res.status(403).json({ error: 'Forbidden' });
    }
    next();
  };
}

// Usage in API route
import { withRole } from '../../lib/guards';

export default function handler(req, res) {
  withRole('admin')(req, res, () => {
    res.status(200).json({ message: 'Access granted' });
  });
}
```

---

## Protecting Routes and API Endpoints

### Conditional Rendering with Types  
In TypeScript, conditional rendering based on authentication status can be done safely, providing a smooth user experience while securing parts of your app.

**Example:**
```tsx
import { useSession } from 'next-auth/react';

const ProtectedPage = () => {
  const { data: session } = useSession();
  
  if (!session) {
    return <div>Please sign in to access this page</div>;
  }

  return <div>Welcome, {session.user.name}</div>;
};
```

### Custom Hook for Auth Context  
A custom hook for authentication context allows you to manage user state across your app, making authentication checks easier and more consistent.

**Example:**
```tsx
// lib/useAuth.ts
import { useSession } from 'next-auth/react';

export function useAuth() {
  const { data: session, status } = useSession();
  const isAuthenticated = status === 'authenticated';

  return { session, isAuthenticated };
}

// Usage in component
import { useAuth } from '../lib/useAuth';

const ProtectedPage = () => {
  const { session, isAuthenticated } = useAuth();

  if (!isAuthenticated) {
    return <div>Please log in</div>;
  }

  return <div>Welcome, {session?.user?.name}</div>;
};
```

---

## Conclusion

**Key Takeaways:**
- NextAuth.js simplifies authentication with TypeScript support and multiple providers like Google, GitHub, and more.
- Typing session and user objects ensures safe and predictable access to authentication data.
- Role-based access control (RBAC) allows you to define guards and middleware for secure resource management.
- Protecting routes and API endpoints in a type-safe manner with conditional rendering or custom hooks makes your app more secure and maintainable.

---

## Practical Exercise

**Build an Authenticated Blog App:**
1. Set up NextAuth.js with Google authentication and TypeScript.
2. Create protected routes that only authenticated users can access.
3. Implement role-based access control for admin functionality (e.g., creating, deleting posts).
4. Use a custom hook to manage authentication state across the app.
