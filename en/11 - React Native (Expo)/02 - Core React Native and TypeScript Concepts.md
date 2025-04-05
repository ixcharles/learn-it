
# Core React Native and TypeScript Concepts

This module dives into the core building blocks of React Native with TypeScript, covering how components, state, props, and user interactions are handled in a type-safe way.

## Table of Contents
- [JSX and Component Structure in React Native](#jsx-and-component-structure-in-react-native)
- [Functional Components and Hooks](#functional-components-and-hooks)
- [TypeScript Interfaces and Types in Components](#typescript-interfaces-and-types-in-components)
- [Props and State Management with TypeScript](#props-and-state-management-with-typescript)
- [Handling Events and User Input](#handling-events-and-user-input)

---

## JSX and Component Structure in React Native

**Definition:**  
JSX is a syntax extension that lets you write UI code in a familiar HTML-like format inside JavaScript/TypeScript files.

**Example:**

```tsx
import { Text, View } from 'react-native';

const MyComponent = () => (
  <View>
    <Text>Hello, React Native!</Text>
  </View>
);
```

React Native uses JSX to describe UI hierarchies using components like `<View>`, `<Text>`, and `<Image>`.

---

## Functional Components and Hooks

**Definition:**  
Functional components are stateless components that rely on hooks like `useState`, `useEffect`, and `useRef` for logic and side effects.

**Example:**

```tsx
import { useState, useEffect } from 'react';
import { Text, Button } from 'react-native';

const Counter = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log(`Count is ${count}`);
  }, [count]);

  return <Button title={`Count: ${count}`} onPress={() => setCount(count + 1)} />;
};
```

Hooks let you manage component state and lifecycle without class components.

---

## TypeScript Interfaces and Types in Components

**Definition:**  
TypeScript interfaces and types provide structure to component props and internal logic, reducing errors and improving editor support.

**Example:**

```ts
type User = {
  id: number;
  name: string;
};

interface Props {
  user: User;
}
```

Using explicit types ensures component contracts are predictable and maintainable.

---

## Props and State Management with TypeScript

**Definition:**  
Props and state are fundamental for controlling UI behavior and data flow in components. TypeScript helps define their shape clearly.

**Example:**

```tsx
type Props = {
  name: string;
};

const Greeting = ({ name }: Props) => {
  const [visible, setVisible] = useState(true);

  return visible ? <Text>Hello, {name}!</Text> : null;
};
```

Typed props and state improve component reusability and reliability.

---

## Handling Events and User Input

**Definition:**  
React Native supports handling gestures and user inputs through components like `TextInput`, `Button`, and touch events.

**Example:**

```tsx
import { useState } from 'react';
import { TextInput, Text, View } from 'react-native';

const InputExample = () => {
  const [text, setText] = useState('');

  return (
    <View>
      <TextInput
        placeholder="Type here"
        onChangeText={setText}
        value={text}
      />
      <Text>You typed: {text}</Text>
    </View>
  );
};
```

Use event handlers like `onChangeText` and `onPress` with strong typing where applicable.

---

## Conclusion

**Key Takeaways:**
1. JSX makes UI code declarative and intuitive.
2. Functional components are the modern React standard.
3. TypeScript enforces strong contracts with props and state.
4. Hooks provide reactive and composable component logic.
5. Event handling integrates user input seamlessly in mobile apps.

**Practical Exercise:**
- Create a component called `ProfileCard` that takes a typed `User` prop with `name`, `bio`, and `age`.
- Use `useState` to toggle showing the user's bio on button press.
