
# App Router and Modern Features

An in-depth guide to the new features in Next.js 13+ with the App Router, including file-based routing, server components, metadata management, and error boundaries. Learn how to integrate these modern tools with TypeScript for a more scalable and maintainable app.

---

## Table of Contents

- [Introduction to App Router](#introduction-to-app-router)  
  - [File-based Routing in App Directory](#file-based-routing-in-app-directory)  
  - [Layouts and Templates](#layouts-and-templates)  
- [Server Components and Client Components](#server-components-and-client-components)  
  - [Differences and Use Cases](#differences-and-use-cases)  
  - [Typing Server/Client Boundaries](#typing-serverclient-boundaries)  
- [Metadata API](#metadata-api)  
  - [Defining Page Metadata with Types](#defining-page-metadata-with-types)  
- [Loading UI and Error Boundaries](#loading-ui-and-error-boundaries)  
  - [Suspense with Server Components](#suspense-with-server-components)  
  - [Typed Error Handling](#typed-error-handling)  

---

## Introduction to App Router

### File-based Routing in App Directory  
With Next.js 13+ and the App Router, routing is handled by the file structure in the `app` directory, providing cleaner and more intuitive navigation.

**Example:**
```tsx
// app/page.tsx
export default function Home() {
  return <h1>Welcome to the Home Page</h1>;
}

// app/about/page.tsx
export default function About() {
  return <h1>About Us</h1>;
}
```

### Layouts and Templates  
Layouts and templates are reusable components that help organize the UI across different pages, ensuring consistency.

**Example:**
```tsx
// app/layout.tsx
export default function Layout({ children }: { children: React.ReactNode }) {
  return (
    <div>
      <header>Header</header>
      <main>{children}</main>
      <footer>Footer</footer>
    </div>
  );
}
```

---

## Server Components and Client Components

### Differences and Use Cases  
Server components are rendered on the server and sent to the client as HTML. Client components are rendered on the client, suitable for interactivity.

**Example:**
```tsx
// Server Component (app/posts/page.tsx)
export default function Posts() {
  const posts = await fetchPosts(); // Server-side fetching
  return (
    <div>
      {posts.map(post => <div key={post.id}>{post.title}</div>)}
    </div>
  );
}

// Client Component (app/components/Button.tsx)
'use client';

export default function Button() {
  const handleClick = () => alert('Button clicked!');
  return <button onClick={handleClick}>Click Me</button>;
}
```

### Typing Server/Client Boundaries  
When using server and client components, ensure the boundary between them is clear by typing props correctly.

**Example:**
```tsx
// Server Component
export default async function PostsPage() {
  const posts = await fetchPosts();
  return <PostsList posts={posts} />;
}

// Client Component
'use client';
type Post = { id: number; title: string };
export default function PostsList({ posts }: { posts: Post[] }) {
  return (
    <div>
      {posts.map(post => <div key={post.id}>{post.title}</div>)}
    </div>
  );
}
```

---

## Metadata API

### Defining Page Metadata with Types  
Next.js allows you to define page-specific metadata, like titles and descriptions, using the Metadata API.

**Example:**
```tsx
// app/about/page.tsx
import { Metadata } from 'next';

export const metadata: Metadata = {
  title: 'About Us',
  description: 'Learn more about our team and mission',
};

export default function AboutPage() {
  return <h1>About Us</h1>;
}
```

---

## Loading UI and Error Boundaries

### Suspense with Server Components  
React Suspense works seamlessly with server components to show loading states while server-side data is being fetched.

**Example:**
```tsx
// app/posts/page.tsx
import { Suspense } from 'react';

export default function Posts() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <PostsList />
    </Suspense>
  );
}

// app/posts/PostsList.tsx
export default function PostsList() {
  const posts = await fetchPosts(); // Server-side fetching
  return (
    <div>
      {posts.map(post => <div key={post.id}>{post.title}</div>)}
    </div>
  );
}
```

### Typed Error Handling  
Handling errors with types allows you to capture and handle potential errors in your app more predictably.

**Example:**
```tsx
// app/posts/page.tsx
import { Suspense } from 'react';

const fetchPosts = async (): Promise<Post[]> => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts');
    if (!response.ok) throw new Error('Failed to fetch posts');
    return response.json();
  } catch (error: any) {
    console.error(error.message);
    throw new Error('Error fetching posts');
  }
};

export default function PostsPage() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <PostsList />
    </Suspense>
  );
}

type Post = { id: number; title: string; body: string };
```

---

## Conclusion

**Key Takeaways:**
- The App Router and file-based routing in Next.js 13+ improve project structure and navigation clarity.
- Server and client components serve different use cases: server components for rendering, client components for interactivity.
- Type-safe metadata allows you to define and manage page-specific details like title and description.
- React Suspense provides a smooth way to handle loading states for server components.
- Proper error handling with TypeScript ensures a more robust and reliable application.

---

## Practical Exercise

**Build a Multi-Page App with Server and Client Components:**
1. Scaffold a Next.js 13+ app using the App Router.
2. Create multiple pages, each with its own layout and metadata.
3. Use a server component to fetch a list of posts from an API.
4. Add a client component for interactivity (e.g., a "Like" button).
5. Implement React Suspense to handle loading states.
