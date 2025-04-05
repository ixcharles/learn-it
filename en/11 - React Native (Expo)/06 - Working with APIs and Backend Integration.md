
# Working with APIs and Backend Integration

Integrating your app with a backend is essential for dynamic content, authentication, and real-time communication. This module covers core techniques for working with REST, GraphQL, and WebSockets in React Native with TypeScript.

## Table of Contents
- [Fetching Data with Fetch API and Axios](#fetching-data-with-fetch-api-and-axios)
- [Handling API Responses and Error Management](#handling-api-responses-and-error-management)
- [Authentication with JWT and Secure Storage](#authentication-with-jwt-and-secure-storage)
- [GraphQL with Apollo Client](#graphql-with-apollo-client)
- [WebSockets and Real-Time Data Handling](#websockets-and-real-time-data-handling)

---

## Fetching Data with Fetch API and Axios

**Definition:**  
`fetch` is built into JavaScript, while Axios is a promise-based HTTP client that simplifies request handling and supports interceptors.

**Example (Axios):**

```ts
import axios from 'axios';

const api = axios.create({ baseURL: 'https://api.example.com' });

type User = { id: number; name: string };

const getUser = async (): Promise<User> => {
  const response = await api.get<User>('/user');
  return response.data;
};
```

Use generics in Axios to strongly type responses.

---

## Handling API Responses and Error Management

**Definition:**  
Always handle network failures and unexpected API behavior using try/catch and Axios interceptors.

**Example:**

```ts
try {
  const user = await getUser();
  console.log(user.name);
} catch (error) {
  if (axios.isAxiosError(error)) {
    console.error('API Error:', error.response?.data);
  } else {
    console.error('Unexpected Error:', error);
  }
}
```

Display user-friendly error messages and log details for debugging.

---

## Authentication with JWT and Secure Storage

**Definition:**  
JWTs (JSON Web Tokens) are commonly used for stateless authentication. Tokens should be stored securely on the device.

**Example:**

```ts
import * as SecureStore from 'expo-secure-store';

const login = async (email: string, password: string) => {
  const res = await axios.post('/login', { email, password });
  const token = res.data.token;
  await SecureStore.setItemAsync('token', token);
};
```

Use `SecureStore` to persist tokens safely instead of `AsyncStorage`.

---

## GraphQL with Apollo Client

**Definition:**  
Apollo Client is a powerful tool for interacting with GraphQL APIs, supporting caching, pagination, and subscriptions.

**Example:**

```tsx
import { ApolloClient, InMemoryCache, gql, useQuery } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://example.com/graphql',
  cache: new InMemoryCache(),
});

const GET_USER = gql`
  query GetUser {
    user {
      id
      name
    }
  }
`;

const UserComponent = () => {
  const { data, loading } = useQuery(GET_USER);
  if (loading) return <Text>Loading...</Text>;
  return <Text>{data.user.name}</Text>;
};
```

Wrap your app in an `ApolloProvider` to enable GraphQL queries and mutations.

---

## WebSockets and Real-Time Data Handling

**Definition:**  
WebSockets enable bidirectional, real-time communication between client and server.

**Example (socket.io-client):**

```ts
import { io } from 'socket.io-client';

const socket = io('https://example.com');

socket.on('connect', () => {
  console.log('Connected');
});

socket.on('message', (data: string) => {
  console.log('New message:', data);
});

socket.emit('sendMessage', 'Hello Server');
```

WebSockets are ideal for chats, notifications, and live updates.

---

## Conclusion

**Key Takeaways:**
1. Use Axios or `fetch` with TypeScript generics for clean, typed API calls.
2. Handle errors properly using try/catch and Axios interceptors.
3. Secure sensitive tokens with `expo-secure-store`, not `AsyncStorage`.
4. Apollo Client makes working with GraphQL simple and efficient.
5. WebSockets provide real-time capabilities for interactive features.

**Practical Exercise:**
- Create a simple login form that calls a fake login API.
- Save the JWT securely using `SecureStore`.
- Fetch and display a protected user profile from the backend using the saved token.
