
# Data Fetching, Caching & API Integration

Effective data fetching, caching, and API integration are essential for building performant and reliable React applications. This course covers modern techniques and libraries like React Query and GraphQL, as well as best practices for data handling.

---

## Table of Contents
- [Fetching Data with Fetch API and Axios](#fetching-data-with-fetch-api-and-axios)  
- [React Query (TanStack Query)](#react-query-tanstack-query)  
  - [Query Caching](#query-caching)  
  - [Query Invalidation](#query-invalidation)  
  - [Mutations and Optimistic Updates](#mutations-and-optimistic-updates)  
  - [Infinite Queries and Pagination](#infinite-queries-and-pagination)  
- [Working with GraphQL and Apollo Client](#working-with-graphql-and-apollo-client)  
- [SWR vs React Query Comparison](#swr-vs-react-query-comparison)  
- [Error and Loading States UX](#error-and-loading-states-ux)  
- [Conclusion & Key Takeaways](#conclusion--key-takeaways)  
- [Practical Exercise](#practical-exercise)

---

## Fetching Data with Fetch API and Axios

### Fetch API

**Definition:** The Fetch API provides a simple way to make HTTP requests and handle responses asynchronously.  
**Example:**
```jsx
const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
};

const App = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetchData().then(setData);
  }, []);

  return <div>{JSON.stringify(data)}</div>;
};
```

### Axios

**Definition:** Axios is a promise-based HTTP client for the browser and Node.js, with automatic JSON parsing and error handling.  
**Example:**
```jsx
import axios from 'axios';

const fetchData = async () => {
  const response = await axios.get('https://api.example.com/data');
  return response.data;
};

const App = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetchData().then(setData);
  }, []);

  return <div>{JSON.stringify(data)}</div>;
};
```

---

## React Query (TanStack Query)

### Query Caching

**Definition:** React Query automatically caches data to prevent unnecessary re-fetching, enhancing performance.  
**Example:**
```jsx
import { useQuery } from 'react-query';

const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  return response.json();
};

const App = () => {
  const { data, isLoading } = useQuery('data', fetchData);

  if (isLoading) return <div>Loading...</div>;

  return <div>{JSON.stringify(data)}</div>;
};
```

### Query Invalidation

**Definition:** Query invalidation forces React Query to re-fetch data when certain conditions are met.  
**Example:**
```jsx
const { data, refetch } = useQuery('data', fetchData);

const handleUpdate = () => {
  // Update data and invalidate query
  refetch();
};
```

### Mutations and Optimistic Updates

**Definition:** Mutations in React Query allow data to be changed on the server, with optimistic updates allowing for a seamless UX while waiting for the server response.  
**Example:**
```jsx
import { useMutation, useQueryClient } from 'react-query';

const updateData = async (newData) => {
  await fetch('/update', { method: 'POST', body: JSON.stringify(newData) });
};

const App = () => {
  const queryClient = useQueryClient();

  const mutation = useMutation(updateData, {
    onMutate: (variables) => {
      // Optimistic update
      queryClient.setQueryData('data', (oldData) => [...oldData, variables]);
    },
    onSettled: () => {
      queryClient.invalidateQueries('data');
    },
  });

  return <button onClick={() => mutation.mutate({ id: 1, text: 'Updated!' })}>Update</button>;
};
```

### Infinite Queries and Pagination

**Definition:** Infinite queries in React Query are used to handle paginated data, making it easy to fetch new pages as the user scrolls.  
**Example:**
```jsx
import { useInfiniteQuery } from 'react-query';

const fetchPage = async ({ pageParam = 1 }) => {
  const response = await fetch(`https://api.example.com/data?page=${pageParam}`);
  return response.json();
};

const App = () => {
  const { data, fetchNextPage, hasNextPage, isLoading } = useInfiniteQuery('data', fetchPage, {
    getNextPageParam: (lastPage, pages) => lastPage.nextPage ?? false,
  });

  if (isLoading) return <div>Loading...</div>;

  return (
    <div>
      {data.pages.map((page, i) => (
        <div key={i}>
          {page.items.map((item) => (
            <div key={item.id}>{item.name}</div>
          ))}
        </div>
      ))}
      {hasNextPage && <button onClick={() => fetchNextPage()}>Load More</button>}
    </div>
  );
};
```

---

## Working with GraphQL and Apollo Client

**Definition:** Apollo Client is a comprehensive state management library that enables efficient interaction with GraphQL APIs.  
**Example:**
```jsx
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://api.example.com/graphql',
  cache: new InMemoryCache(),
});

const GET_DATA = gql`
  query GetData {
    data {
      id
      name
    }
  }
`;

const App = () => {
  const { loading, error, data } = useQuery(GET_DATA, { client });

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;

  return <div>{JSON.stringify(data)}</div>;
};
```

---

## SWR vs React Query Comparison

**Definition:** SWR (stale-while-revalidate) and React Query are both libraries for data fetching, caching, and synchronization, but React Query offers more built-in features for complex scenarios like mutations and pagination, while SWR is simpler.  
**Key Differences:**
- **React Query:** More advanced features like query invalidation, pagination, and mutation handling.
- **SWR:** Lighter, simpler, and more focused on data fetching with less configuration.

---

## Error and Loading States UX

**Definition:** Handling loading and error states in your UI ensures a better user experience by providing feedback during data fetching processes.  
**Example:**
```jsx
const App = () => {
  const { data, isLoading, isError, error } = useQuery('data', fetchData);

  if (isLoading) return <div>Loading...</div>;
  if (isError) return <div>Error: {error.message}</div>;

  return <div>{JSON.stringify(data)}</div>;
};
```

**Best Practices:**
- Display loading indicators or skeleton screens during data fetching.
- Show user-friendly error messages or retry options when errors occur.

---

## Conclusion & Key Takeaways

- **Fetch API and Axios** are fundamental for simple data fetching, with Axios offering enhanced features like automatic JSON parsing.
- **React Query** simplifies data fetching, caching, and state management with built-in optimizations like query caching, mutations, and pagination.
- **Apollo Client** is ideal for managing data with GraphQL APIs, offering advanced caching and query management.
- **SWR** is a simpler alternative to React Query, focusing on efficient and minimal data fetching.
- Handling **loading** and **error states** is crucial for delivering a smooth user experience in applications.

---

## Practical Exercise

Build a simple blog application:
1. Fetch a list of blog posts using **React Query** or **Axios**.
2. Implement pagination to load more posts as the user scrolls (use **Infinite Queries** in React Query).
3. Add error and loading states with clear feedback to the user.
4. Integrate **Apollo Client** to fetch blog posts from a GraphQL API (if possible).
