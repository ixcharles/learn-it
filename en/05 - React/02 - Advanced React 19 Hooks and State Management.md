
# Advanced React 19 Hooks and State Management

React 19 builds on powerful Hooks for managing side effects, state, and application logic. This course dives deep into advanced Hooks and strategies for scalable and optimized state handling.

---

## Table of Contents
- [useEffect Hook Deep Dive](#useeffect-hook-deep-dive)  
  - [Lifecycle Simulation](#lifecycle-simulation)  
  - [Cleanup Functions](#cleanup-functions)  
- [useMemo and useCallback](#usememo-and-usecallback)  
  - [Performance Optimization](#performance-optimization)  
- [useRef and DOM Access](#useref-and-dom-access)  
- [Custom Hooks](#custom-hooks)  
  - [Building Reusable Logic](#building-reusable-logic)  
- [useReducer and State Machines](#usereducer-and-state-machines)  
- [Context API](#context-api)  
  - [Global State with useContext](#global-state-with-usecontext)  
  - [Context Performance Patterns](#context-performance-patterns)  
- [Conclusion & Key Takeaways](#conclusion--key-takeaways)  
- [Practical Exercise](#practical-exercise)

---

## useEffect Hook Deep Dive

### Lifecycle Simulation
**Definition:** `useEffect` replicates mounting, updating, and unmounting behavior.  
**Example:**
```jsx
useEffect(() => {
  console.log('Mounted or updated');
}, [dependency]);
```

### Cleanup Functions
**Definition:** Cleanup functions run on unmount or before re-running the effect.  
**Example:**
```jsx
useEffect(() => {
  const timer = setInterval(...);
  return () => clearInterval(timer);
}, []);
```

---

## useMemo and useCallback

### Performance Optimization
**Definition:** `useMemo` memoizes computed values; `useCallback` memoizes functions.  
**Example:**
```jsx
const expensiveResult = useMemo(() => compute(data), [data]);
const memoizedFn = useCallback(() => doSomething(), []);
```

---

## useRef and DOM Access
**Definition:** `useRef` accesses DOM nodes or persists values without re-renders.  
**Example:**
```jsx
const inputRef = useRef();
<input ref={inputRef} />;
inputRef.current.focus();
```

---

## Custom Hooks

### Building Reusable Logic
**Definition:** Custom Hooks encapsulate logic for reuse across components.  
**Example:**
```jsx
function useToggle(initial = false) {
  const [value, setValue] = useState(initial);
  const toggle = () => setValue(v => !v);
  return [value, toggle];
}
```

---

## useReducer and State Machines
**Definition:** `useReducer` is useful for complex state transitions and finite state logic.  
**Example:**
```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
  }
}
const [state, dispatch] = useReducer(reducer, { count: 0 });
```

---

## Context API

### Global State with useContext
**Definition:** `useContext` accesses shared state across components.  
**Example:**
```jsx
const ThemeContext = createContext();
const theme = useContext(ThemeContext);
```

### Context Performance Patterns
**Definition:** Prevent unnecessary re-renders with memoized providers and context splitting.  
**Example:**
```jsx
const MemoizedProvider = React.memo(({ children }) => (
  <ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>
));
```

---

## Conclusion & Key Takeaways
- `useEffect` manages side effects and mimics lifecycle methods.
- `useMemo` and `useCallback` boost performance in rendering.
- `useRef` provides mutable storage and DOM references.
- Custom Hooks promote modular, reusable logic.
- `useReducer` and Context API power scalable global state systems.

---

## Practical Exercise

Build a toggleable theme switcher using Context and Custom Hooks:
1. Create a `ThemeContext` with `"light"` or `"dark"` values.
2. Use a custom hook to toggle the theme.
3. Display a button that toggles the theme using context.
