
# Mastering UI & Theming in React Native Expo

**Introduction**  
This course will guide you through mastering UI and theming in React Native Expo. You’ll learn to design beautiful, responsive, and performance-optimized UIs using popular libraries like **react-native-paper**, **react-native-elements**, and **react-native-animatable**, along with advanced techniques for theming and animations.

## Table of Contents  
1. [Foundations](#foundations)  
    - [Introduction to UI Design in React Native](#introduction-to-ui-design-in-react-native)  
    - [Understanding Theming and Styling in Expo](#understanding-theming-and-styling-in-expo)  
2. [Material Design & UI Libraries](#material-design--ui-libraries)  
    - [Using react-native-paper for Material Design Components](#using-react-native-paper-for-material-design-components)  
    - [Customizing UI with react-native-elements](#customizing-ui-with-react-native-elements)  
3. [Animations & UX Enhancements](#animations--ux-enhancements)  
    - [Animating Components with react-native-animatable](#animating-components-with-react-native-animatable)  
    - [Implementing Lottie Animations with lottie-react-native](#implementing-lottie-animations-with-lottie-react-native)  
    - [Creating Skeleton Screens with react-native-skeleton-content](#creating-skeleton-screens-with-react-native-skeleton-content)  
4. [Advanced UI & Performance Optimization](#advanced-ui--performance-optimization)  
    - [Performance Best Practices for UI Components](#performance-best-practices-for-ui-components)  
    - [Dynamic Themes & Dark Mode Implementation](#dynamic-themes--dark-mode-implementation)  

---

## Foundations

### Introduction to UI Design in React Native
UI design in React Native involves creating user interfaces that are visually appealing and function well on both iOS and Android devices. This is achieved through reusable components, layouts, and styles.

**Example**  
```jsx
import { View, Text, StyleSheet } from 'react-native';

const App = () => (
  <View style={styles.container}>
    <Text>Hello, React Native!</Text>
  </View>
);

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#fff',
  },
});
```

### Understanding Theming and Styling in Expo
Theming and styling in Expo apps are done using **StyleSheet** and can be dynamically changed with tools like **react-native-paper** or custom themes.

**Example**  
```jsx
import { DefaultTheme, Provider as PaperProvider } from 'react-native-paper';

const theme = {
  ...DefaultTheme,
  colors: {
    ...DefaultTheme.colors,
    primary: 'tomato',
  },
};

const App = () => (
  <PaperProvider theme={theme}>
    <Text>Hello, Themed App!</Text>
  </PaperProvider>
);
```

---

## Material Design & UI Libraries

### Using react-native-paper for Material Design Components
**react-native-paper** provides a set of high-quality, pre-designed Material Design components for React Native.

**Example**  
```jsx
import { Button } from 'react-native-paper';

const App = () => (
  <Button icon="camera" mode="contained" onPress={() => console.log('Pressed')}>
    Press me
  </Button>
);
```

### Customizing UI with react-native-elements
**react-native-elements** is a UI toolkit offering customizable components for creating modern, responsive designs.

**Example**  
```jsx
import { Button } from 'react-native-elements';

const App = () => (
  <Button title="Custom Button" buttonStyle={{ backgroundColor: 'purple' }} />
);
```

---

## Animations & UX Enhancements

### Animating Components with react-native-animatable
**react-native-animatable** simplifies animations by offering pre-configured animations or custom ones.

**Example**  
```jsx
import * as Animatable from 'react-native-animatable';

const App = () => (
  <Animatable.View animation="bounceIn" duration={1500}>
    <Text>Animated Text</Text>
  </Animatable.View>
);
```

### Implementing Lottie Animations with lottie-react-native
**lottie-react-native** enables smooth vector animations using JSON files from Lottie.

**Example**  
```jsx
import LottieView from 'lottie-react-native';

const App = () => (
  <LottieView
    source={require('./animation.json')}
    autoPlay
    loop
  />
);
```

### Creating Skeleton Screens with react-native-skeleton-content
**react-native-skeleton-content** helps create loading skeleton screens, improving the user experience during data fetch.

**Example**  
```jsx
import SkeletonContent from 'react-native-skeleton-content';

const App = () => (
  <SkeletonContent isLoading={true}>
    <Text>Content Loaded</Text>
  </SkeletonContent>
);
```

---

## Advanced UI & Performance Optimization

### Performance Best Practices for UI Components
Optimizing UI components involves reducing unnecessary renders, lazy loading resources, and using efficient styles.

**Example**  
```jsx
const MemoizedComponent = React.memo(({ text }) => <Text>{text}</Text>);
```

### Dynamic Themes & Dark Mode Implementation
Switching themes or enabling dark mode dynamically can be done using libraries like **react-native-paper** or **styled-components**.

**Example**  
```jsx
import { useState } from 'react';
import { DefaultTheme, DarkTheme, Provider as PaperProvider } from 'react-native-paper';

const App = () => {
  const [isDark, setIsDark] = useState(false);
  const theme = isDark ? DarkTheme : DefaultTheme;

  return (
    <PaperProvider theme={theme}>
      <Button onPress={() => setIsDark(!isDark)}>Toggle Theme</Button>
    </PaperProvider>
  );
};
```

---

## Conclusion

### Key Takeaways  
1. **react-native-paper** offers Material Design components that are highly customizable.  
2. **react-native-elements** provides easy-to-use UI components for quick customization.  
3. Animating components with **react-native-animatable** and **lottie-react-native** enhances UX.  
4. Skeleton screens improve perceived performance during data loading.  
5. Performance optimization is critical to ensuring smooth UI rendering.  

### Practical Exercise  
1. Create a React Native Expo app that uses **react-native-paper** for UI components and **lottie-react-native** for animations.
2. Implement a theme toggle button to switch between light and dark modes using **react-native-paper**.
3. Add a skeleton screen for loading data from a mock API endpoint.
