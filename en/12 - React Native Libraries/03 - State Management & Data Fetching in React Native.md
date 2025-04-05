
# State Management & Data Fetching in React Native

**Introduction**  
In this course, you’ll master state management and data fetching in React Native using modern libraries like **Zustand**, **Recoil**, and **React Query**. Learn when and how to manage local and global states efficiently while fetching and caching data from the server.

## Table of Contents  
1. [Understanding State Management in React Native](#understanding-state-management-in-react-native)  
    - [Local State vs. Global State](#local-state-vs-global-state)  
    - [Choosing the Right State Management Library](#choosing-the-right-state-management-library)  
2. [State Management Libraries](#state-management-libraries)  
    - [Managing State with Zustand](#managing-state-with-zustand)  
    - [Using Recoil for Complex State Structures](#using-recoil-for-complex-state-structures)  
    - [Server-Side State Management with React Query](#server-side-state-management-with-react-query)  
3. [Best Practices & Performance](#best-practices--performance)  
    - [Caching and Synchronization Strategies](#caching-and-synchronization-strategies)  
    - [Optimizing Performance for State Management](#optimizing-performance-for-state-management)  

---

## Understanding State Management in React Native

### Local State vs. Global State
- **Local state** refers to state that is only needed within a single component.
- **Global state** refers to state that needs to be shared across multiple components.

**Example**  
Local state with React's **useState**:  
```jsx
const [count, setCount] = useState(0);
```

Global state using **Context API**:  
```jsx
const CountContext = React.createContext();

const App = () => {
  const [count, setCount] = useState(0);
  return (
    <CountContext.Provider value={{ count, setCount }}>
      <ChildComponent />
    </CountContext.Provider>
  );
};
```

### Choosing the Right State Management Library
Selecting the right library depends on the complexity of your app:
- **Zustand** for simple global state.
- **Recoil** for complex state management with atoms and selectors.
- **React Query** for server-side state management with caching.

---

## State Management Libraries

### Managing State with Zustand
**Zustand** is a minimal, fast state management library with a simple API and excellent performance.

**Example**  
```bash
npm install zustand
```

```jsx
import create from 'zustand';

const useStore = create(set => ({
  count: 0,
  increment: () => set(state => ({ count: state.count + 1 })),
}));

const App = () => {
  const { count, increment } = useStore();
  return (
    <View>
      <Text>{count}</Text>
      <Button onPress={increment} title="Increment" />
    </View>
  );
};
```

### Using Recoil for Complex State Structures
**Recoil** provides a powerful way to manage complex state with atoms and selectors, enabling fine-grained control over state dependencies.

**Example**  
```bash
npm install recoil
```

```jsx
import { atom, useRecoilState } from 'recoil';

const countState = atom({
  key: 'countState',
  default: 0,
});

const App = () => {
  const [count, setCount] = useRecoilState(countState);
  return (
    <View>
      <Text>{count}</Text>
      <Button onPress={() => setCount(count + 1)} title="Increment" />
    </View>
  );
};
```

### Server-Side State Management with React Query
**React Query** simplifies server-side state management by abstracting data fetching, caching, and synchronization.

**Example**  
```bash
npm install react-query
```

```jsx
import { useQuery } from 'react-query';

const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  return response.json();
};

const App = () => {
  const { data, isLoading, error } = useQuery('data', fetchData);

  if (isLoading) return <Text>Loading...</Text>;
  if (error) return <Text>Error fetching data</Text>;

  return <Text>{JSON.stringify(data)}</Text>;
};
```

---

## Best Practices & Performance

### Caching and Synchronization Strategies
To optimize data fetching and state management, leverage caching strategies:
- Use **React Query** to cache server responses.
- For local state, avoid unnecessary re-renders by using **React.memo** and **useMemo**.

**Example**  
Caching with **React Query**:  
```jsx
const { data } = useQuery('posts', fetchPosts, { cacheTime: 10000 });
```

### Optimizing Performance for State Management
- **Avoid deep nested state**: Break down state into smaller parts.
- **Use selectors**: In **Recoil**, use selectors to derive state to avoid redundant calculations.

**Example**  
Optimizing **Recoil** selectors:
```jsx
import { selector } from 'recoil';

const doubledCountState = selector({
  key: 'doubledCountState',
  get: ({ get }) => {
    const count = get(countState);
    return count * 2;
  },
});
```

---

## Conclusion

### Key Takeaways  
1. **Local state** is best suited for single component needs, while **global state** is needed for shared data across multiple components.  
2. **Zustand** is perfect for simple global state management with minimal overhead.  
3. **Recoil** offers a powerful API for managing complex state through atoms and selectors.  
4. **React Query** simplifies data fetching and caching, making server-side state management easy.  
5. Performance optimization requires careful state design and caching strategies to minimize re-renders.

### Practical Exercise  
1. Create an app using **Zustand** for global state management and **React Query** for fetching data from a mock API.  
2. Implement a **Recoil** atom for managing a counter and create a selector that returns double the counter value.  
3. Optimize your app by implementing caching in **React Query** and using **React.memo** for components that don't require re-renders.
