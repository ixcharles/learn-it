
# React 19 Routing and Navigation

Routing and navigation are key aspects of building single-page applications (SPAs) in React. This course explores React Router v7 and advanced navigation patterns in React 19.

---

## Table of Contents
- [React Router v7 (Latest with React 19)](#react-router-v7-latest-with-react-19)  
  - [Route, Routes, Navigate, useNavigate](#route-routes-navigate-usenavigate)  
  - [Nested Routes](#nested-routes)  
  - [Dynamic Routing](#dynamic-routing)  
  - [Route Loaders and Actions](#route-loaders-and-actions)  
  - [Route-based Code Splitting](#route-based-code-splitting)  
- [Navigation Guards and Authentication Flows](#navigation-guards-and-authentication-flows)  
- [Lazy Loading Routes](#lazy-loading-routes)  
- [Error Boundaries in Routing](#error-boundaries-in-routing)  
- [Conclusion & Key Takeaways](#conclusion--key-takeaways)  
- [Practical Exercise](#practical-exercise)

---

## React Router v7 (Latest with React 19)

### Route, Routes, Navigate, useNavigate

**Definition:** `Route` defines a path, `Routes` wraps multiple routes, `Navigate` redirects users, and `useNavigate` programmatically navigates.  
**Example:**
```jsx
import { Routes, Route, Navigate, useNavigate } from 'react-router-dom';

const App = () => {
  const navigate = useNavigate();

  const handleRedirect = () => {
    navigate('/home');
  };

  return (
    <div>
      <button onClick={handleRedirect}>Go to Home</button>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="home" element={<h2>Home Page</h2>} />
      </Routes>
    </div>
  );
};
```

---

### Nested Routes

**Definition:** Nested routes allow defining child routes inside parent routes.  
**Example:**
```jsx
<Routes>
  <Route path="dashboard" element={<Dashboard />}>
    <Route path="profile" element={<Profile />} />
    <Route path="settings" element={<Settings />} />
  </Route>
</Routes>
```

---

### Dynamic Routing

**Definition:** Dynamic routes are created based on the parameters or external data.  
**Example:**
```jsx
<Routes>
  <Route path="user/:id" element={<UserDetail />} />
</Routes>

const UserDetail = () => {
  const { id } = useParams();
  return <div>User ID: {id}</div>;
};
```

---

### Route Loaders and Actions

**Definition:** Route loaders and actions can fetch data before rendering the route or perform actions like authentication.  
**Example:**
```jsx
import { Route, useLoaderData } from 'react-router-dom';

const fetchData = async () => {
  const response = await fetch('/api/data');
  return response.json();
};

<Routes>
  <Route path="/data" element={<DataPage />} loader={fetchData} />
</Routes>

const DataPage = () => {
  const data = useLoaderData();
  return <div>{JSON.stringify(data)}</div>;
};
```

---

### Route-based Code Splitting

**Definition:** Code splitting loads only the necessary components when the route is accessed.  
**Example:**
```jsx
import { Suspense, lazy } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

<Routes>
  <Route
    path="/lazy"
    element={
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    }
  />
</Routes>
```

---

## Navigation Guards and Authentication Flows

**Definition:** Navigation guards protect routes from unauthorized access, often requiring authentication.  
**Example:**
```jsx
const ProtectedRoute = ({ children }) => {
  const isAuthenticated = useAuth();
  return isAuthenticated ? children : <Navigate to="/login" />;
};

<Routes>
  <Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
</Routes>
```

---

## Lazy Loading Routes

**Definition:** Routes are loaded lazily to improve performance by splitting the bundle.  
**Example:**
```jsx
const HomePage = lazy(() => import('./HomePage'));

<Routes>
  <Route
    path="/home"
    element={
      <Suspense fallback={<div>Loading...</div>}>
        <HomePage />
      </Suspense>
    }
  />
</Routes>
```

---

## Error Boundaries in Routing

**Definition:** Error boundaries catch errors in React components and prevent crashes in the UI.  
**Example:**
```jsx
import { ErrorBoundary } from 'react-error-boundary';

<Routes>
  <Route
    path="/dashboard"
    element={
      <ErrorBoundary FallbackComponent={ErrorFallback}>
        <Dashboard />
      </ErrorBoundary>
    }
  />
</Routes>

const ErrorFallback = ({ error }) => <div>Error: {error.message}</div>;
```

---

## Conclusion & Key Takeaways

- `Route`, `Routes`, and `Navigate` are foundational to React Router’s navigation flow.
- Nested and dynamic routes provide flexibility for scalable application structures.
- Route loaders and actions enhance data fetching and conditional logic within routes.
- Lazy loading routes and code splitting significantly improve performance.
- Navigation guards protect sensitive routes based on authentication or other conditions.
- Error boundaries ensure that navigation does not break the app in case of errors.

---

## Practical Exercise

Build a basic blog application with React Router:
1. Create a route for the homepage (`/`), a post list (`/posts`), and a single post (`/posts/:id`).
2. Use `useNavigate` to redirect to a post detail page.
3. Implement lazy loading for the post detail page and error boundaries to catch potential errors during navigation.
