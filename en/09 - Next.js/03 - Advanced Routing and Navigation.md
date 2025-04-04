
# Advanced Routing and Navigation

A comprehensive guide to mastering advanced routing and navigation in Next.js, covering dynamic routes, programmatic navigation, middleware, and internationalization.

---

## Table of Contents

- [Deep Dive into Dynamic Routing](#deep-dive-into-dynamic-routing)  
  - [Optional Catch-all Routes](#optional-catch-all-routes)  
  - [Fallback Pages](#fallback-pages)  
- [Programmatic Navigation](#programmatic-navigation)  
  - [useRouter Hook](#userouter-hook)  
  - [Query Params with Types](#query-params-with-types)  
- [Middleware and Edge Functions](#middleware-and-edge-functions)  
  - [Writing Middleware](#writing-middleware)  
  - [Typing Middleware Functions](#typing-middleware-functions)  
- [Internationalized Routing](#internationalized-routing)  
  - [Configuring i18n](#configuring-i18n)  
  - [Locale-Specific Routing](#locale-specific-routing)  

---

## Deep Dive into Dynamic Routing

### Optional Catch-all Routes  
Optional catch-all routes allow for capturing a variable number of path segments while being optional.

**Example:**
```tsx
// pages/blog/[...slug].tsx
export default function Blog({ slug }: { slug?: string[] }) {
  return <div>Blog: {slug?.join('/')}</div>;
}
```

### Fallback Pages  
Fallback pages let you define a loading state for static paths not generated at build time.

**Example:**
```tsx
// pages/blog/[id].tsx
export async function getStaticPaths() {
  return {
    paths: [{ params: { id: '1' } }],
    fallback: 'blocking', // 'true' or 'false' or 'blocking'
  };
}
```

---

## Programmatic Navigation

### useRouter Hook  
The `useRouter` hook provides access to the router object and allows for programmatic navigation.

**Example:**
```tsx
import { useRouter } from 'next/router';

const NavigateButton = () => {
  const router = useRouter();

  const handleNavigate = () => {
    router.push('/about');
  };

  return <button onClick={handleNavigate}>Go to About</button>;
};
```

### Query Params with Types  
Type-safe query parameters help ensure the correct structure for URL parameters.

**Example:**
```tsx
import { useRouter } from 'next/router';

const Page = () => {
  const router = useRouter();
  const { id } = router.query; // id is a string or undefined by default

  if (typeof id === 'string') {
    return <div>Post ID: {id}</div>;
  }

  return <div>Loading...</div>;
};
```

---

## Middleware and Edge Functions

### Writing Middleware  
Middleware in Next.js allows you to execute custom logic before serving a request.

**Example:**
```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(req: Request) {
  const url = req.url;
  if (url.includes('restricted')) {
    return NextResponse.redirect(new URL('/login', url));
  }
  return NextResponse.next();
}
```

### Typing Middleware Functions  
Type your middleware functions for better control and type safety.

**Example:**
```tsx
// middleware.ts
import { NextResponse } from 'next/server';
import { NextRequest } from 'next/server';

export function middleware(req: NextRequest) {
  const token = req.cookies.get('authToken');
  if (!token) {
    return NextResponse.redirect(new URL('/login', req.url));
  }
  return NextResponse.next();
}
```

---

## Internationalized Routing

### Configuring i18n  
Next.js supports internationalized routing by configuring the `i18n` property in `next.config.js`.

**Example:**
```js
// next.config.js
module.exports = {
  i18n: {
    locales: ['en', 'fr', 'es'],
    defaultLocale: 'en',
  },
};
```

### Locale-Specific Routing  
Next.js allows for locale-based routing, so users can access content in different languages.

**Example:**
```tsx
// pages/[locale]/index.tsx
export default function Home({ locale }: { locale: string }) {
  return <div>Current Locale: {locale}</div>;
}
```

---

## Conclusion

**Key Takeaways:**
- Optional catch-all routes enable flexible URL matching with optional parameters.
- Fallback pages allow handling missing paths by showing loading states.
- Programmatic navigation using `useRouter` is a powerful way to control route transitions.
- Middleware offers a mechanism to intercept requests, ideal for authentication and redirects.
- Internationalization in Next.js is straightforward with locale-based routing.

---

## Practical Exercise

**Create a blog with dynamic routing and internationalization:**
1. Scaffold a Next.js app with i18n support.
2. Create dynamic routes for individual blog posts (`[id].tsx`).
3. Implement a middleware that checks for an "authToken" cookie, redirecting users if it's not present.
4. Add a language switcher to navigate between English and French locales.
