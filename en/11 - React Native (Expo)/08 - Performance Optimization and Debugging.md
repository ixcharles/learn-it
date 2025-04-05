
# Performance Optimization and Debugging

Optimizing performance and debugging effectively are essential for a smooth user experience in production-grade React Native apps. This module focuses on render efficiency, memory management, debugging tools, and network profiling using TypeScript.

## Table of Contents
- [Optimizing Renders and Avoiding Re-Renders](#optimizing-renders-and-avoiding-re-renders)
- [Memory Management and Performance Monitoring](#memory-management-and-performance-monitoring)
- [Using Hermes for Faster Execution](#using-hermes-for-faster-execution)
- [Debugging Tools (React DevTools, Flipper, Console Debugging)](#debugging-tools-react-devtools-flipper-console-debugging)
- [Profiling and Optimizing Network Requests](#profiling-and-optimizing-network-requests)

---

## Optimizing Renders and Avoiding Re-Renders

**Definition:**  
Prevent unnecessary component re-renders using memoization, stable references, and virtualized lists.

**Example:**

```tsx
import React, { memo, useCallback, useState } from 'react';

type ButtonProps = { onPress: () => void };
const MyButton = memo(({ onPress }: ButtonProps) => <Button title="Tap" onPress={onPress} />);

const Parent = () => {
  const [count, setCount] = useState(0);
  const handlePress = useCallback(() => setCount(c => c + 1), []);
  return <MyButton onPress={handlePress} />;
};
```

Use `React.memo`, `useCallback`, `useMemo` to avoid unnecessary updates.

---

## Memory Management and Performance Monitoring

**Definition:**  
Free unused resources and monitor memory usage to prevent leaks and crashes on lower-end devices.

**Tips:**
- Clear timers, subscriptions, and listeners in `useEffect` cleanup.
- Use FlatList with `initialNumToRender` and `windowSize` for large lists.
- Monitor memory with Flipper's Performance tab or Android Studio Profiler.

**Example Cleanup:**

```tsx
useEffect(() => {
  const id = setInterval(() => console.log('tick'), 1000);
  return () => clearInterval(id);
}, []);
```

---

## Using Hermes for Faster Execution

**Definition:**  
Hermes is a lightweight JavaScript engine optimized for React Native on Android (also supported in iOS via Expo SDK 49+).

**How to Enable in Expo:**

```json
// app.json
{
  "expo": {
    "jsEngine": "hermes"
  }
}
```

Hermes improves start-up time, memory usage, and performance in production.

---

## Debugging Tools (React DevTools, Flipper, Console Debugging)

**Definition:**  
React DevTools and Flipper are essential tools to inspect component trees, state, logs, and performance in real-time.

**Tools:**
- **React DevTools:** Inspect component hierarchy and props/state.
- **Flipper:** Inspect logs, performance, React DevTools, network.
- **Console:** Use `console.log`, `console.table`, `console.warn` for quick insight.

**Flipper Setup:**

```bash
npx expo install react-native-flipper
```

Install Flipper app and run with Metro connected.

---

## Profiling and Optimizing Network Requests

**Definition:**  
Track and reduce the number and size of network calls using Flipper or custom Axios interceptors.

**Example (Axios Interceptor for Logging):**

```ts
import axios from 'axios';

const api = axios.create();

api.interceptors.request.use(req => {
  console.log(`[REQUEST] ${req.method?.toUpperCase()} ${req.url}`);
  return req;
});

api.interceptors.response.use(res => {
  console.log(`[RESPONSE] ${res.status} - ${res.config.url}`);
  return res;
});
```

Batch API calls, use caching (e.g., React Query), and avoid redundant fetches.

---

## Conclusion

**Key Takeaways:**
1. Use memoization and pure components to prevent unnecessary re-renders.
2. Clean up resources in components to avoid memory leaks.
3. Enable Hermes for better performance on Android (and optionally iOS).
4. Use Flipper and React DevTools to inspect and debug effectively.
5. Monitor and optimize API usage to reduce latency and overhead.

**Practical Exercise:**
- Build a screen that lists items from a remote API using `FlatList`.
- Use `memo` for list items to avoid unnecessary re-renders.
- Add Axios interceptors to log each network request.
- Test with Flipper to observe performance and network activity.
