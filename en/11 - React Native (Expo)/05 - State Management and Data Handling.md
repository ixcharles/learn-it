
# State Management and Data Handling

Managing application state and fetching data efficiently are essential for building robust, scalable React Native apps. This module covers key state management tools and patterns, all using TypeScript for type safety.

## Table of Contents
- [Context API with TypeScript](#context-api-with-typescript)
- [Redux Toolkit with TypeScript](#redux-toolkit-with-typescript)
- [React Query for Data Fetching](#react-query-for-data-fetching)
- [Zustand and Recoil for Simpler State Management](#zustand-and-recoil-for-simpler-state-management)
- [Best Practices for Managing Global and Local State](#best-practices-for-managing-global-and-local-state)

---

## Context API with TypeScript

**Definition:**  
The Context API provides a way to share values like themes, authentication, or settings across the component tree.

**Example:**

```tsx
// AuthContext.tsx
import { createContext, useContext, useState } from 'react';

type AuthContextType = {
  user: string | null;
  login: (user: string) => void;
};

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export const AuthProvider = ({ children }: { children: React.ReactNode }) => {
  const [user, setUser] = useState<string | null>(null);
  const login = (name: string) => setUser(name);
  return <AuthContext.Provider value={{ user, login }}>{children}</AuthContext.Provider>;
};

export const useAuth = () => {
  const context = useContext(AuthContext);
  if (!context) throw new Error("useAuth must be used within AuthProvider");
  return context;
};
```

---

## Redux Toolkit with TypeScript

**Definition:**  
Redux Toolkit simplifies Redux with less boilerplate and strong TypeScript support out-of-the-box.

**Example:**

```ts
// store.ts
import { configureStore, createSlice, PayloadAction } from '@reduxjs/toolkit';

type CounterState = { value: number };
const initialState: CounterState = { value: 0 };

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment: state => { state.value += 1; },
    set: (state, action: PayloadAction<number>) => { state.value = action.payload; }
  }
});

export const { increment, set } = counterSlice.actions;
export const store = configureStore({ reducer: { counter: counterSlice.reducer } });
export type RootState = ReturnType<typeof store.getState>;
```

Use `useSelector` and `useDispatch` with proper types in components.

---

## React Query for Data Fetching

**Definition:**  
React Query (TanStack Query) manages remote data fetching, caching, and synchronization efficiently.

**Example:**

```tsx
import { useQuery } from '@tanstack/react-query';
import axios from 'axios';

const fetchUser = async () => (await axios.get('/api/user')).data;

const Profile = () => {
  const { data, isLoading } = useQuery(['user'], fetchUser);
  if (isLoading) return <Text>Loading...</Text>;
  return <Text>{data.name}</Text>;
};
```

Type your API responses for full safety in consuming components.

---

## Zustand and Recoil for Simpler State Management

**Definition:**  
Zustand and Recoil offer minimal, flexible alternatives to Redux for state management.

**Zustand Example:**

```ts
import create from 'zustand';

type Store = {
  count: number;
  increment: () => void;
};

export const useStore = create<Store>(set => ({
  count: 0,
  increment: () => set(state => ({ count: state.count + 1 })),
}));
```

**Recoil Example:**

```ts
import { atom, useRecoilState } from 'recoil';

const countAtom = atom<number>({ key: 'count', default: 0 });

const Counter = () => {
  const [count, setCount] = useRecoilState(countAtom);
  return <Button onPress={() => setCount(count + 1)} title={`Count: ${count}`} />;
};
```

Both integrate easily with TypeScript and are great for small to medium apps.

---

## Best Practices for Managing Global and Local State

**Definition:**  
Use the right state management strategy depending on whether state is shared (global) or isolated (local).

**Recommendations:**

- **Local UI state**: useState or useReducer.
- **Global app state**: Context, Redux, Zustand, or Recoil.
- **Server state**: React Query or SWR.
- Keep state colocated as much as possible.
- Avoid unnecessary context re-renders by splitting providers.

---

## Conclusion

**Key Takeaways:**
1. Context API is great for simple global state like auth and theme.
2. Redux Toolkit reduces boilerplate and works well in large apps.
3. React Query simplifies async data handling with caching and syncing.
4. Zustand and Recoil are lightweight alternatives with minimal setup.
5. Match your state tool to the complexity and purpose of the data.

**Practical Exercise:**
- Build a small app with a counter and user login system.
- Use Zustand for the counter and Context API for the user.
- Display the logged-in user's name and allow logging out.
