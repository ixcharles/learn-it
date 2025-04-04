
# Networking & Data Fetching in React

## Introduction
Efficient data fetching and management are key to building interactive and dynamic React applications. In this section, we'll explore two powerful tools, Axios and React Query, that streamline API calls and state management in React apps.

## Table of Contents
1. [Axios](#axios)
2. [React Query](#react-query)
3. [Conclusion](#conclusion)

---

## Axios
Axios is a popular, promise-based HTTP client for making API requests in React. It allows for easy handling of asynchronous HTTP requests and provides a clean API for dealing with responses and errors.

### Example:
1. Install Axios:
   ```bash
   npm install axios
   ```
2. Make a GET request:
   ```jsx
   import axios from 'axios';
   import { useState, useEffect } from 'react';

   function DataFetching() {
     const [data, setData] = useState([]);
     const [loading, setLoading] = useState(true);

     useEffect(() => {
       axios.get('https://jsonplaceholder.typicode.com/posts')
         .then((response) => {
           setData(response.data);
           setLoading(false);
         })
         .catch((error) => {
           console.error('Error fetching data:', error);
           setLoading(false);
         });
     }, []);

     if (loading) return <div>Loading...</div>;

     return (
       <div>
         <ul>
           {data.map(item => (
             <li key={item.id}>{item.title}</li>
           ))}
         </ul>
       </div>
     );
   }
   ```

#### Key Features:
- **Promise-based API**: Axios uses promises for handling async requests, making it easy to chain `.then()` and `.catch()` or use `async/await`.
- **Automatic JSON Parsing**: Axios automatically parses the response as JSON.
- **Request and Response Interceptors**: Modify or log requests and responses before they are handled.
- **Error Handling**: Axios provides a robust way to handle HTTP errors, such as 404 or 500 responses.

---

## React Query
React Query is a powerful library that simplifies data-fetching, caching, and synchronization of server state. It automates tasks like caching, background data syncing, and pagination, making it easier to manage server-side data in React applications.

### Example:
1. Install React Query:
   ```bash
   npm install react-query
   ```
2. Fetch data using React Query:
   ```jsx
   import { useQuery } from 'react-query';

   function DataFetching() {
     const { data, isLoading, error } = useQuery('posts', () =>
       fetch('https://jsonplaceholder.typicode.com/posts')
         .then(res => res.json())
     );

     if (isLoading) return <div>Loading...</div>;
     if (error) return <div>Error: {error.message}</div>;

     return (
       <div>
         <ul>
           {data.map(item => (
             <li key={item.id}>{item.title}</li>
           ))}
         </ul>
       </div>
     );
   }
   ```

#### Key Features:
- **Caching**: React Query automatically caches server responses, reducing the need for repeated requests.
- **Background Fetching**: It supports background refetching of data, ensuring the app always has the latest data.
- **Automatic Error Handling**: React Query provides built-in error and loading states, simplifying data-fetching management.
- **Data Synchronization**: Easily synchronize server data across your application without worrying about inconsistent states.
- **Pagination & Infinite Scroll**: Built-in support for managing paginated or infinite scrolling data.

---

## Conclusion

### Key Takeaways:
1. **Axios** is a flexible, promise-based HTTP client for making API requests in React, with robust error handling and automatic JSON parsing.
2. **React Query** is a powerful data-fetching library that automates caching, synchronization, and background fetching of server-side data, simplifying state management in React apps.

### Practical Exercise:
1. Use **Axios** to fetch a list of users from a public API (like JSONPlaceholder) and display their names in a React component.
2. Implement **React Query** to fetch and display a list of posts, ensuring proper loading, error handling, and caching of the data.
