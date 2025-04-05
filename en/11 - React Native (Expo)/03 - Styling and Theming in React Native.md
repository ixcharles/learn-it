
# Styling and Theming in React Native

Styling is a core part of building beautiful, responsive UIs in React Native. This module covers native styling methods, CSS-in-JS with styled-components, and managing themes across your app.

## Table of Contents
- [React Native StyleSheet API](#react-native-stylesheet-api)
- [Styled-Components with TypeScript](#styled-components-with-typescript)
- [Global Theming and Context API](#global-theming-and-context-api)
- [Responsive Design and Flexbox Layouts](#responsive-design-and-flexbox-layouts)
- [Dark Mode and Dynamic Themes](#dark-mode-and-dynamic-themes)

---

## React Native StyleSheet API

**Definition:**  
The built-in `StyleSheet` API in React Native lets you define styles as JavaScript objects, similar to CSS.

**Example:**

```tsx
import { StyleSheet, Text, View } from 'react-native';

const styles = StyleSheet.create({
  container: { padding: 16 },
  text: { fontSize: 18, color: 'blue' },
});

const Box = () => (
  <View style={styles.container}>
    <Text style={styles.text}>Hello StyleSheet</Text>
  </View>
);
```

`StyleSheet.create` enables performance optimizations and consistency.

---

## Styled-Components with TypeScript

**Definition:**  
Styled-components is a CSS-in-JS library that supports dynamic styling and TypeScript typings for props.

**Example:**

```tsx
import styled from 'styled-components/native';

type Props = { primary?: boolean };

const Button = styled.TouchableOpacity<Props>`
  background-color: ${({ primary }) => (primary ? 'blue' : 'gray')};
  padding: 10px;
`;

const Label = styled.Text`
  color: white;
`;

const StyledExample = () => (
  <Button primary>
    <Label>Click Me</Label>
  </Button>
);
```

It allows co-locating styles with components for better modularity.

---

## Global Theming and Context API

**Definition:**  
Using React Context, you can create and share a global theme object throughout your app.

**Example:**

```tsx
// theme.ts
export const theme = {
  colors: {
    background: '#fff',
    text: '#333',
  },
};
```

```tsx
// ThemeContext.tsx
import { createContext, useContext } from 'react';
export const ThemeContext = createContext(theme);
export const useTheme = () => useContext(ThemeContext);
```

Wrap your app in a `ThemeProvider` and access values via `useTheme()`.

---

## Responsive Design and Flexbox Layouts

**Definition:**  
React Native uses Flexbox by default for layout, making it easy to create responsive designs.

**Example:**

```tsx
import { View } from 'react-native';

const ResponsiveLayout = () => (
  <View style={{ flexDirection: 'row', justifyContent: 'space-between' }}>
    <View style={{ flex: 1, backgroundColor: 'red', height: 100 }} />
    <View style={{ flex: 2, backgroundColor: 'blue', height: 100 }} />
  </View>
);
```

Use `flex`, `flexDirection`, `justifyContent`, and `alignItems` to control layout.

---

## Dark Mode and Dynamic Themes

**Definition:**  
React Native can detect system color schemes, allowing you to switch between light and dark themes dynamically.

**Example:**

```tsx
import { useColorScheme } from 'react-native';

const App = () => {
  const colorScheme = useColorScheme();
  const isDark = colorScheme === 'dark';

  return (
    <View style={{ backgroundColor: isDark ? '#000' : '#fff', flex: 1 }}>
      <Text style={{ color: isDark ? '#fff' : '#000' }}>Dark Mode Example</Text>
    </View>
  );
};
```

Combine with styled-components or a custom theme provider for full control.

---

## Conclusion

**Key Takeaways:**
1. The `StyleSheet` API is fast and native to React Native.
2. Styled-components allow dynamic, scoped styling using TypeScript.
3. Themes can be globally managed using Context for consistency.
4. Flexbox powers responsive, adaptable UI layouts in React Native.
5. System-level theming enables seamless dark mode support.

**Practical Exercise:**
- Create a reusable `ThemedButton` component.
- Use styled-components and access theme values from a context.
- Implement a toggle switch that switches between light and dark themes.
