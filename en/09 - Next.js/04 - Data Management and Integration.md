
# Data Management and Integration

A comprehensive guide to handling data fetching, API consumption, and database integration in Next.js projects using TypeScript, focusing on popular tools like Axios, SWR, React Query, and Prisma.

---

## Table of Contents

- [Consuming REST and GraphQL APIs](#consuming-rest-and-graphql-apis)  
  - [Axios/Fetch with TypeScript](#axiosfetch-with-typescript)  
  - [Typed GraphQL Queries and Mutations](#typed-graphql-queries-and-mutations)  
- [SWR and React Query](#swr-and-react-query)  
  - [Type-safe Data Fetching](#type-safe-data-fetching)  
  - [Caching and Mutations](#caching-and-mutations)  
- [Server Actions and Functions (App Router)](#server-actions-and-functions-app-router)  
  - [Using Server Actions with Types](#using-server-actions-with-types)  
- [Database Integration](#database-integration)  
  - [Using Prisma with TypeScript](#using-prisma-with-typescript)  
  - [Type-safe DB Queries](#type-safe-db-queries)  

---

## Consuming REST and GraphQL APIs

### Axios/Fetch with TypeScript  
Axios and Fetch can be used to make API requests while maintaining type safety with TypeScript.

**Example:**
```tsx
import axios from 'axios';

type Post = { id: number; title: string; body: string };

const fetchPosts = async (): Promise<Post[]> => {
  const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
  return response.data;
};

const posts = await fetchPosts();
```

### Typed GraphQL Queries and Mutations  
GraphQL queries and mutations can be typed using Apollo Client or other GraphQL clients for TypeScript support.

**Example:**
```tsx
import { gql } from '@apollo/client';

const GET_POSTS = gql`
  query GetPosts {
    posts {
      id
      title
      body
    }
  }
`;

type Post = { id: number; title: string; body: string };

const { data, error } = useQuery<{ posts: Post[] }>(GET_POSTS);
```

---

## SWR and React Query

### Type-safe Data Fetching  
SWR and React Query offer easy-to-use hooks for data fetching while supporting TypeScript for type-safe queries.

**Example (SWR):**
```tsx
import useSWR from 'swr';

type Post = { id: number; title: string; body: string };

const fetcher = (url: string) => fetch(url).then((res) => res.json());

const Posts = () => {
  const { data, error } = useSWR<Post[]>('https://jsonplaceholder.typicode.com/posts', fetcher);
  if (error) return <div>Error loading posts</div>;
  if (!data) return <div>Loading...</div>;

  return <ul>{data.map((post) => <li key={post.id}>{post.title}</li>)}</ul>;
};
```

**Example (React Query):**
```tsx
import { useQuery } from 'react-query';

type Post = { id: number; title: string; body: string };

const fetchPosts = async (): Promise<Post[]> => {
  const response = await fetch('https://jsonplaceholder.typicode.com/posts');
  return response.json();
};

const Posts = () => {
  const { data, error } = useQuery<Post[]>('posts', fetchPosts);

  if (error) return <div>Error loading posts</div>;
  if (!data) return <div>Loading...</div>;

  return <ul>{data.map((post) => <li key={post.id}>{post.title}</li>)}</ul>;
};
```

### Caching and Mutations  
React Query and SWR automatically handle caching, and provide easy APIs for mutations (creating/updating/deleting data).

**Example (React Query Mutation):**
```tsx
import { useMutation } from 'react-query';

const createPost = async (post: { title: string; body: string }) => {
  const response = await fetch('/api/posts', {
    method: 'POST',
    body: JSON.stringify(post),
  });
  return response.json();
};

const NewPost = () => {
  const mutation = useMutation(createPost);

  const handleSubmit = (event: React.FormEvent) => {
    event.preventDefault();
    const newPost = { title: 'New Post', body: 'This is a new post.' };
    mutation.mutate(newPost);
  };

  return <button onClick={handleSubmit}>Create Post</button>;
};
```

---

## Server Actions and Functions (App Router)

### Using Server Actions with Types  
Server-side functions in the App Router (Next.js 13+) can be typed for API interaction and data fetching.

**Example:**
```tsx
// app/api/posts/route.ts
import { NextResponse } from 'next/server';

type Post = { id: number; title: string; body: string };

export async function GET() {
  const posts: Post[] = await fetch('https://jsonplaceholder.typicode.com/posts').then((res) => res.json());
  return NextResponse.json(posts);
}
```

---

## Database Integration

### Using Prisma with TypeScript  
Prisma is an ORM that allows for type-safe database queries with TypeScript.

**Example:**
```ts
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

const getAllPosts = async () => {
  const posts = await prisma.post.findMany();
  return posts;
};
```

### Type-safe DB Queries  
Prisma automatically generates types for your database schema, ensuring that all queries are type-safe.

**Example:**
```ts
const createPost = async (title: string, body: string) => {
  const newPost = await prisma.post.create({
    data: { title, body },
  });
  return newPost;
};
```

---

## Conclusion

**Key Takeaways:**
- Axios and Fetch provide easy API integration with TypeScript support for typed responses.
- GraphQL queries and mutations can be typed for better developer experience.
- SWR and React Query handle caching, mutation, and type-safe data fetching efficiently.
- Server Actions in the App Router offer seamless server-side logic integration with type safety.
- Prisma offers type-safe database queries with automatic type generation from your schema.

---

## Practical Exercise

**Create a Type-safe Blog Application:**
1. Scaffold a Next.js app with Prisma and set up your database schema.
2. Create an API route to fetch all blog posts.
3. Use SWR or React Query to fetch and display posts on the front-end.
4. Implement a mutation to create a new post and display it after successful creation.
