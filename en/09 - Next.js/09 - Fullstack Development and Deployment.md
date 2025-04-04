
# Fullstack Development and Deployment

This guide covers how to build fullstack applications using Next.js and TypeScript, manage webhooks and background jobs, configure environment variables, and set up deployment pipelines for a seamless development-to-production flow.

---

## Table of Contents

- [Building Fullstack Apps](#building-fullstack-apps)  
  - [Combining API Routes with UI](#combining-api-routes-with-ui)  
  - [Type-safe End-to-End Flows](#type-safe-end-to-end-flows)  
- [Webhooks and Background Jobs](#webhooks-and-background-jobs)  
  - [Receiving and Validating Webhooks](#receiving-and-validating-webhooks)  
  - [Serverless Functions with TypeScript](#serverless-functions-with-typescript)  
- [Environment Variables and Configuration](#environment-variables-and-configuration)  
  - [Using `process.env` Safely](#using-processenv-safely)  
  - [Typing Environment Variables](#typing-environment-variables)  
- [Deployment Pipelines](#deployment-pipelines)  
  - [Vercel Deployment with TypeScript](#vercel-deployment-with-typescript)  
  - [CI/CD Integration](#cicd-integration)  

---

## Building Fullstack Apps

### Combining API Routes with UI  
Next.js allows you to create fullstack applications by combining API routes and the frontend UI in the same project. This setup lets you fetch data directly from API routes and display it within your React components.

**Example:**
```tsx
// pages/api/posts.ts
export default async function handler(req, res) {
  const posts = await fetchPostsFromDatabase();
  res.status(200).json(posts);
}

// pages/index.tsx
import { useEffect, useState } from 'react';

const HomePage = () => {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    async function fetchPosts() {
      const response = await fetch('/api/posts');
      const data = await response.json();
      setPosts(data);
    }
    fetchPosts();
  }, []);

  return (
    <div>
      <h1>Posts</h1>
      {posts.map(post => (
        <div key={post.id}>{post.title}</div>
      ))}
    </div>
  );
};
```

### Type-safe End-to-End Flows  
Type safety ensures the correctness of data being passed between your UI and API routes, reducing bugs and improving developer experience. You can define types for API responses and ensure the UI components are working with the correct data structures.

**Example:**
```tsx
// types.ts
export interface Post {
  id: string;
  title: string;
  content: string;
}

// pages/api/posts.ts
import { NextApiRequest, NextApiResponse } from 'next';
import { Post } from '../../types';

export default async function handler(req: NextApiRequest, res: NextApiResponse<Post[]>) {
  const posts = await fetchPostsFromDatabase();
  res.status(200).json(posts);
}

// pages/index.tsx
import { Post } from '../types';

const HomePage = () => {
  const [posts, setPosts] = useState<Post[]>([]);

  useEffect(() => {
    async function fetchPosts() {
      const response = await fetch('/api/posts');
      const data: Post[] = await response.json();
      setPosts(data);
    }
    fetchPosts();
  }, []);

  return (
    <div>
      <h1>Posts</h1>
      {posts.map(post => (
        <div key={post.id}>{post.title}</div>
      ))}
    </div>
  );
};
```

---

## Webhooks and Background Jobs

### Receiving and Validating Webhooks  
Webhooks allow you to receive notifications from external services. You can use API routes to handle and validate incoming webhook data.

**Example:**
```tsx
// pages/api/webhook.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  if (req.method === 'POST') {
    const signature = req.headers['x-signature'];
    const isValid = validateWebhookSignature(signature, req.body);
    if (!isValid) {
      return res.status(400).json({ error: 'Invalid signature' });
    }

    const data = req.body;
    // Process webhook data...
    return res.status(200).json({ message: 'Webhook received successfully' });
  }

  res.status(405).json({ error: 'Method Not Allowed' });
}

function validateWebhookSignature(signature: string, payload: any): boolean {
  // Signature validation logic...
  return true;
}
```

### Serverless Functions with TypeScript  
Serverless functions in Next.js can be written with TypeScript, enabling you to handle backend logic in a scalable way without managing server infrastructure.

**Example:**
```tsx
// pages/api/send-email.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  const { email, message } = req.body;

  try {
    // Send email logic...
    return res.status(200).json({ message: 'Email sent successfully' });
  } catch (error) {
    return res.status(500).json({ error: 'Error sending email' });
  }
}
```

---

## Environment Variables and Configuration

### Using `process.env` Safely  
In Next.js, you can use environment variables to store sensitive information, such as API keys. Make sure to access them securely and only expose necessary variables to the client-side.

**Example:**
```tsx
// .env.local
NEXT_PUBLIC_API_URL=https://api.example.com
SECRET_API_KEY=your-secret-key

// pages/api/data.ts
export default async function handler(req, res) {
  const apiUrl = process.env.NEXT_PUBLIC_API_URL;
  const apiKey = process.env.SECRET_API_KEY;

  const response = await fetch(`${apiUrl}/data?apiKey=${apiKey}`);
  const data = await response.json();
  res.status(200).json(data);
}
```

### Typing Environment Variables  
TypeScript supports type-safe environment variables by declaring types for `process.env` to prevent errors caused by missing or malformed values.

**Example:**
```tsx
// env.d.ts
declare global {
  namespace NodeJS {
    interface ProcessEnv {
      NEXT_PUBLIC_API_URL: string;
      SECRET_API_KEY: string;
    }
  }
}
```

---

## Deployment Pipelines

### Vercel Deployment with TypeScript  
Vercel is the recommended platform for deploying Next.js applications. It has built-in support for TypeScript, allowing you to deploy your project seamlessly.

**Example:**
1. Push your project to GitHub, GitLab, or Bitbucket.
2. Connect your repository to Vercel via the Vercel dashboard.
3. Vercel automatically detects the Next.js framework and deploys your app, including TypeScript files.

No configuration is needed for TypeScript deployment on Vercel as it works out-of-the-box.

### CI/CD Integration  
Integrate Continuous Integration and Continuous Deployment (CI/CD) pipelines using GitHub Actions, GitLab CI, or similar tools to automate testing, building, and deploying your Next.js app.

**Example (GitHub Actions):**
```yaml
name: Deploy Next.js to Vercel

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Install dependencies
        run: npm install

      - name: Run build
        run: npm run build

      - name: Deploy to Vercel
        run: vercel --prod --token ${{ secrets.VERCEL_TOKEN }}
```

---

## Conclusion

**Key Takeaways:**
- Fullstack applications in Next.js combine API routes with UI, enabling you to create dynamic applications with TypeScript support.
- Webhooks can be handled in Next.js using API routes, and background jobs can be managed with serverless functions.
- Safely manage environment variables using `process.env`, and ensure type safety by declaring types for these variables.
- Deploy your Next.js app easily on Vercel and integrate CI/CD pipelines for automated deployments and testing.

---

## Practical Exercise

**Create a Fullstack Blog Application:**
1. Build a simple blog where users can fetch posts from an API route and submit comments via a form.
2. Implement a webhook to receive notifications when a new post is published.
3. Use TypeScript to manage environment variables for the blog's configuration (e.g., API URL, secret keys).
4. Set up CI/CD using GitHub Actions for automatic deployments to Vercel.
