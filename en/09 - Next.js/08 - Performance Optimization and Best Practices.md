
# Performance Optimization and Best Practices

Learn how to optimize your Next.js app's performance and follow best practices for image and font optimization, code splitting, caching strategies, and improving accessibility and SEO, all with TypeScript.

---

## Table of Contents

- [Image and Font Optimization](#image-and-font-optimization)  
  - [next/image and next/font with Types](#nextimage-and-nextfont-with-types)  
- [Code Splitting and Lazy Loading](#code-splitting-and-lazy-loading)  
  - [Dynamic Imports](#dynamic-imports)  
  - [Typed Lazy Components](#typed-lazy-components)  
- [Caching Strategies](#caching-strategies)  
  - [ISR with TypeScript](#isr-with-typescript)  
  - [CDN and Edge Caching](#cdn-and-edge-caching)  
- [Accessibility and SEO](#accessibility-and-seo)  
  - [Head Component and Meta Tags](#head-component-and-meta-tags)  
  - [ARIA and Semantic HTML with Types](#aria-and-semantic-html-with-types)  

---

## Image and Font Optimization

### next/image and next/font with Types  
Next.js provides built-in optimization for images and fonts. `next/image` automatically optimizes images for faster loading, and `next/font` optimizes custom fonts. Both support TypeScript for type safety.

**Example:**
```tsx
// Image optimization using next/image
import Image from 'next/image';

const MyImage = () => (
  <Image 
    src="/images/hero.jpg" 
    alt="Hero Image" 
    width={1200} 
    height={800} 
    priority 
  />
);

// Font optimization using next/font
import { Inter } from 'next/font/google';

const inter = Inter({ subsets: ['latin'] });

export default function Page() {
  return (
    <div className={inter.className}>
      <h1>Optimized Fonts and Images</h1>
    </div>
  );
}
```

---

## Code Splitting and Lazy Loading

### Dynamic Imports  
Next.js supports dynamic imports, allowing you to load JavaScript modules on demand, improving the performance of your application by splitting code into smaller chunks.

**Example:**
```tsx
import dynamic from 'next/dynamic';

const LazyComponent = dynamic(() => import('../components/LazyComponent'), {
  ssr: false, // Disable SSR for this component
});

export default function Page() {
  return (
    <div>
      <h1>Page with Lazy Loaded Component</h1>
      <LazyComponent />
    </div>
  );
}
```

### Typed Lazy Components  
When using dynamic imports with TypeScript, ensure that your components are typed correctly for better development experience and type safety.

**Example:**
```tsx
import dynamic from 'next/dynamic';

const LazyComponent = dynamic(() => import('../components/LazyComponent'), {
  ssr: false,
  loading: () => <p>Loading...</p>,
});

const Page = () => {
  return (
    <div>
      <h1>Page with Lazy Loaded Component</h1>
      <LazyComponent />
    </div>
  );
};

export default Page;
```

---

## Caching Strategies

### ISR with TypeScript  
Incremental Static Regeneration (ISR) enables you to update static content without rebuilding the entire site. You can use ISR with TypeScript to ensure type-safe fetching and caching of data.

**Example:**
```tsx
// pages/posts/[id].tsx
import { GetStaticProps, GetStaticPaths } from 'next';

export const getStaticProps: GetStaticProps = async ({ params }) => {
  const post = await fetchPostById(params?.id as string);
  return {
    props: { post },
    revalidate: 60, // Regenerate the page every 60 seconds
  };
};

export const getStaticPaths: GetStaticPaths = async () => {
  const posts = await fetchAllPosts();
  const paths = posts.map(post => ({
    params: { id: post.id.toString() },
  }));
  return { paths, fallback: 'blocking' };
};

export default function Post({ post }: { post: PostType }) {
  return <div>{post.title}</div>;
}
```

### CDN and Edge Caching  
Use CDN and edge caching strategies to serve your assets closer to the user, reducing latency and improving the speed of your app.

**Example:**
```tsx
// next.config.js
module.exports = {
  images: {
    domains: ['example.com'],
  },
  async rewrites() {
    return [
      {
        source: '/api/:path*',
        destination: 'https://cdn.example.com/:path*',
      },
    ];
  },
};
```

---

## Accessibility and SEO

### Head Component and Meta Tags  
Next.js provides a `Head` component for managing SEO-related metadata, like title and meta tags, to improve your site's visibility and indexing on search engines.

**Example:**
```tsx
import Head from 'next/head';

const Page = () => {
  return (
    <>
      <Head>
        <title>SEO Optimized Page</title>
        <meta name="description" content="This is an optimized page for SEO" />
        <meta name="robots" content="index, follow" />
      </Head>
      <div>
        <h1>Welcome to the SEO Optimized Page</h1>
      </div>
    </>
  );
};
```

### ARIA and Semantic HTML with Types  
Ensure your web application is accessible to everyone by using ARIA attributes and semantic HTML elements, all while maintaining type safety with TypeScript.

**Example:**
```tsx
// Accessible button component with ARIA attributes
const AccessibleButton = ({ onClick }: { onClick: () => void }) => (
  <button onClick={onClick} aria-label="Click to perform action">
    Click Me
  </button>
);

// Using semantic HTML for better accessibility
const Article = ({ title, content }: { title: string; content: string }) => (
  <article>
    <header>
      <h1>{title}</h1>
    </header>
    <section>
      <p>{content}</p>
    </section>
  </article>
);
```

---

## Conclusion

**Key Takeaways:**
- Optimize images and fonts with `next/image` and `next/font` to improve loading times.
- Implement code splitting and lazy loading with dynamic imports to reduce initial load time.
- Use Incremental Static Regeneration (ISR) and CDN/edge caching to improve performance and content freshness.
- Enhance SEO and accessibility by using the `Head` component for metadata and incorporating ARIA and semantic HTML with TypeScript.

---

## Practical Exercise

**Build an Optimized Blog App:**
1. Implement image optimization using `next/image` for post images.
2. Use `next/font` to optimize fonts across the app.
3. Apply dynamic imports for lazy-loaded components.
4. Implement ISR for fetching and caching blog posts.
5. Use the `Head` component to add SEO metadata for each page.
6. Ensure accessibility with ARIA attributes and semantic HTML.
