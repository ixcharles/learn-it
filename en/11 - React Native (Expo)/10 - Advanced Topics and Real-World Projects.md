
# Advanced Topics and Real-World Projects

This module explores advanced React Native Expo techniques using TypeScript, including native modules, complex animations, offline storage, and scalable architecture patterns for large apps.

## Table of Contents
- [Creating Custom Native Modules with TypeScript](#creating-custom-native-modules-with-typescript)
- [Animations with Reanimated and Gesture Handling](#animations-with-reanimated-and-gesture-handling)
- [Offline-First Apps with SQLite and AsyncStorage](#offline-first-apps-with-sqlite-and-asyncstorage)
- [Building and Optimizing Large-Scale React Native Apps](#building-and-optimizing-large-scale-react-native-apps)
- [Best Practices for Maintainable and Scalable Codebases](#best-practices-for-maintainable-and-scalable-codebases)

---

## Creating Custom Native Modules with TypeScript

**Definition:**  
Expo supports adding native functionality via config plugins or by ejecting and writing custom modules.

**Approach (via plugin):**

```ts
// plugin.js
module.exports = function withCustomPermission(config) {
  config.android = config.android || {};
  config.android.permissions = [...(config.android.permissions || []), 'android.permission.VIBRATE'];
  return config;
};
```

Use native modules only when Expo's managed modules don't meet your needs.

---

## Animations with Reanimated and Gesture Handling

**Definition:**  
`react-native-reanimated` and `react-native-gesture-handler` provide smooth, native-driven animations and gestures.

**Example (Reanimated 2):**

```tsx
import Animated, { useSharedValue, useAnimatedStyle, withSpring } from 'react-native-reanimated';

const Example = () => {
  const offset = useSharedValue(0);
  const animatedStyle = useAnimatedStyle(() => ({ transform: [{ translateX: offset.value }] }));

  return (
    <Animated.View style={[{ width: 100, height: 100, backgroundColor: 'red' }, animatedStyle]}>
      <Button title="Move" onPress={() => (offset.value = withSpring(150))} />
    </Animated.View>
  );
};
```

Use gestures from `react-native-gesture-handler` to control animated components.

---

## Offline-First Apps with SQLite and AsyncStorage

**Definition:**  
Use `expo-sqlite` or `@react-native-async-storage/async-storage` to persist data offline for reliability and speed.

**Example (AsyncStorage):**

```ts
import AsyncStorage from '@react-native-async-storage/async-storage';

const saveData = async () => await AsyncStorage.setItem('user', JSON.stringify({ name: 'John' }));
const loadData = async () => JSON.parse(await AsyncStorage.getItem('user') || '{}');
```

**Example (SQLite):**

```ts
import * as SQLite from 'expo-sqlite';

const db = SQLite.openDatabase('my.db');
db.transaction(tx => {
  tx.executeSql('CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT)');
  tx.executeSql('INSERT INTO users (name) VALUES (?)', ['Jane']);
});
```

---

## Building and Optimizing Large-Scale React Native Apps

**Definition:**  
Scaling requires modular architecture, code splitting, lazy loading, and efficient state/data management.

**Tips:**
- Use feature-based folder structure
- Lazy load screens via `React.lazy` or navigation
- Optimize bundle size with dynamic imports
- Use TypeScript project references for monorepos

**Example Folder Structure:**

```
/src
  /features
    /auth
    /chat
    /profile
  /components
  /utils
  /hooks
```

---

## Best Practices for Maintainable and Scalable Codebases

**Definition:**  
Establishing best practices reduces technical debt and improves developer velocity.

**Best Practices:**
- Strong typing with interfaces and enums
- Use `zod` or `yup` for runtime validation
- Centralize API, constants, and themes
- Prefer composition over inheritance
- Linting, formatting, and Git hooks (e.g., Husky + ESLint + Prettier)

**Example (Type-safe API):**

```ts
type User = { id: string; name: string };
const fetchUser = async (): Promise<User> => {
  const res = await fetch('https://api.example.com/user');
  return await res.json();
};
```

---

## Conclusion

**Key Takeaways:**
1. Custom native modules extend Expo's capabilities when needed.
2. Use Reanimated and gestures for performant animations and interactions.
3. Offline-first apps improve reliability using SQLite or AsyncStorage.
4. Modularize and lazy load to scale large applications efficiently.
5. Follow TypeScript and architectural best practices for long-term maintainability.

**Practical Exercise:**
- Create an animated, draggable card using Reanimated + Gesture Handler.
- Save the card’s position in AsyncStorage.
- Reload the position on app startup.
- Organize the feature in a standalone `/features/cards/` folder.
