
# Advanced Navigation & Gesture Handling in React Native

**Introduction**  
This course dives into advanced concepts of navigation and gesture handling in React Native. Learn how to create seamless, smooth navigational flows and interactions in your app using libraries like **react-navigation**, **react-native-gesture-handler**, and **react-native-reanimated**.

## Table of Contents  
1. [Navigation Fundamentals](#navigation-fundamentals)  
    - [Introduction to Navigation in React Native](#introduction-to-navigation-in-react-native)  
    - [Setting Up react-navigation](#setting-up-react-navigation)  
2. [Advanced Navigation Techniques](#advanced-navigation-techniques)  
    - [Stack, Drawer, and Tab Navigation](#stack-drawer-and-tab-navigation)  
    - [Deep Linking & Dynamic Navigation](#deep-linking--dynamic-navigation)  
3. [Gesture Handling & Animations](#gesture-handling--animations)  
    - [Using react-native-gesture-handler for Smooth Interactions](#using-react-native-gesture-handler-for-smooth-interactions)  
    - [Complex Animations with react-native-reanimated](#complex-animations-with-react-native-reanimated)  
4. [Navigation Performance & Best Practices](#navigation-performance--best-practices)  
    - [Optimizing Navigation Performance](#optimizing-navigation-performance)  
    - [Handling Navigation in Large Applications](#handling-navigation-in-large-applications)  

---

## Navigation Fundamentals

### Introduction to Navigation in React Native
Navigation in React Native refers to the system that controls how users move through different screens or views in the app. Proper navigation enhances UX and app usability.

**Example**  
```bash
npm install @react-navigation/native @react-navigation/stack react-native-screens react-native-safe-area-context
```

### Setting Up react-navigation
To start with navigation, you need to install **react-navigation** and set up basic navigation using a stack navigator.

**Example**  
```jsx
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import HomeScreen from './HomeScreen';
import DetailsScreen from './DetailsScreen';

const Stack = createStackNavigator();

const App = () => (
  <NavigationContainer>
    <Stack.Navigator initialRouteName="Home">
      <Stack.Screen name="Home" component={HomeScreen} />
      <Stack.Screen name="Details" component={DetailsScreen} />
    </Stack.Navigator>
  </NavigationContainer>
);
```

---

## Advanced Navigation Techniques

### Stack, Drawer, and Tab Navigation
Advanced navigation involves combining different navigators like **Stack**, **Drawer**, and **Tab** to create multi-layered navigation flows.

**Example**  
```jsx
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { createDrawerNavigator } from '@react-navigation/drawer';

const Tab = createBottomTabNavigator();
const Drawer = createDrawerNavigator();

const App = () => (
  <NavigationContainer>
    <Drawer.Navigator>
      <Drawer.Screen name="Tabs" component={Tabs} />
    </Drawer.Navigator>
  </NavigationContainer>
);

const Tabs = () => (
  <Tab.Navigator>
    <Tab.Screen name="Home" component={HomeScreen} />
    <Tab.Screen name="Profile" component={ProfileScreen} />
  </Tab.Navigator>
);
```

### Deep Linking & Dynamic Navigation
Deep linking allows users to open specific app screens directly from an external link, enabling dynamic and context-aware navigation.

**Example**  
```jsx
import { Linking } from 'react-native';

const linking = {
  prefixes: ['myapp://'],
  config: {
    screens: {
      Home: '',
      Profile: 'profile/:id',
    },
  },
};

const App = () => (
  <NavigationContainer linking={linking}>
    <Stack.Navigator>
      <Stack.Screen name="Home" component={HomeScreen} />
      <Stack.Screen name="Profile" component={ProfileScreen} />
    </Stack.Navigator>
  </NavigationContainer>
);
```

---

## Gesture Handling & Animations

### Using react-native-gesture-handler for Smooth Interactions
**react-native-gesture-handler** enables you to implement complex touch gestures, such as swiping and dragging, to enhance app interactivity.

**Example**  
```jsx
import { GestureHandlerRootView, PanGestureHandler } from 'react-native-gesture-handler';

const App = () => (
  <GestureHandlerRootView>
    <PanGestureHandler onGestureEvent={handleGesture}>
      <Animated.View style={styles.box} />
    </PanGestureHandler>
  </GestureHandlerRootView>
);
```

### Complex Animations with react-native-reanimated
**react-native-reanimated** provides a powerful API for creating complex animations that run on the native thread for smooth performance.

**Example**  
```jsx
import Animated, { Easing, withSpring } from 'react-native-reanimated';

const AnimatedBox = () => {
  const translateX = useSharedValue(0);

  const handleGesture = useAnimatedGestureHandler({
    onActive: (event) => {
      translateX.value = withSpring(event.translationX);
    },
  });

  return (
    <Animated.View style={{ transform: [{ translateX: translateX.value }] }} />
  );
};
```

---

## Navigation Performance & Best Practices

### Optimizing Navigation Performance
Optimizing performance is crucial in large applications to avoid unnecessary rerenders and ensure smooth transitions. Use memoization and lazy loading techniques to improve navigation performance.

**Example**  
```jsx
import { useMemo } from 'react';

const MemoizedScreen = React.memo(ScreenComponent);
```

### Handling Navigation in Large Applications
As apps grow, managing navigation and states becomes more complex. Use techniques like **React Navigation’s lazy loading** and **nested navigators** to keep the app performant.

**Example**  
```jsx
const App = () => (
  <NavigationContainer>
    <Stack.Navigator initialRouteName="Home" screenOptions={{ lazy: true }}>
      <Stack.Screen name="Home" component={HomeScreen} />
      <Stack.Screen name="Details" component={DetailsScreen} />
    </Stack.Navigator>
  </NavigationContainer>
);
```

---

## Conclusion

### Key Takeaways  
1. **react-navigation** is essential for navigating between different screens in React Native.  
2. Combining **Stack**, **Drawer**, and **Tab** navigators creates complex, multi-layered navigation flows.  
3. **Deep linking** allows users to navigate directly to specific screens using external URLs.  
4. **react-native-gesture-handler** enables smooth gesture interactions for a better user experience.  
5. Use **react-native-reanimated** for complex animations that run smoothly on the native thread.  

### Practical Exercise  
1. Create a React Native app with multiple navigation types (Stack, Drawer, Tab).  
2. Implement deep linking to navigate to a profile screen from an external link.  
3. Add swipe gestures to a screen using **react-native-gesture-handler** and create a smooth animation with **react-native-reanimated**.
