
# Navigation and Routing

Navigation is a critical part of mobile apps, enabling screen transitions and user flow. React Navigation, paired with TypeScript, offers a type-safe, flexible way to handle navigation in React Native apps.

## Table of Contents
- [Setting Up React Navigation in Expo](#setting-up-react-navigation-in-expo)
- [Stack, Tab, and Drawer Navigation](#stack-tab-and-drawer-navigation)
- [Passing Props and Type Safety in Navigation](#passing-props-and-type-safety-in-navigation)
- [Deep Linking and Handling Navigation State](#deep-linking-and-handling-navigation-state)
- [Authentication Flows in Navigation](#authentication-flows-in-navigation)

---

## Setting Up React Navigation in Expo

**Definition:**  
React Navigation is the most popular navigation library for React Native, with full support in Expo.

**Example:**

```bash
npm install @react-navigation/native
npx expo install react-native-screens react-native-safe-area-context
npm install @react-navigation/native-stack
```

Set up the navigation container:

```tsx
import { NavigationContainer } from '@react-navigation/native';

export default function App() {
  return <NavigationContainer>{/* Navigators */}</NavigationContainer>;
}
```

Wrap your app with `NavigationContainer` to enable navigation support.

---

## Stack, Tab, and Drawer Navigation

**Definition:**  
React Navigation supports multiple navigator types for different UI paradigms: stack (screen transitions), tab (bottom navigation), and drawer (side menu).

**Example:**

```tsx
import { createNativeStackNavigator } from '@react-navigation/native-stack';
const Stack = createNativeStackNavigator();

<Stack.Navigator>
  <Stack.Screen name="Home" component={HomeScreen} />
  <Stack.Screen name="Details" component={DetailsScreen} />
</Stack.Navigator>
```

You can nest navigators for advanced layouts (e.g., tabs inside a drawer).

---

## Passing Props and Type Safety in Navigation

**Definition:**  
React Navigation integrates with TypeScript to enforce safe prop passing between screens.

**Example:**

```ts
type RootStackParamList = {
  Home: undefined;
  Profile: { userId: string };
};

const Stack = createNativeStackNavigator<RootStackParamList>();

// Usage
navigation.navigate('Profile', { userId: '123' });
```

Define your param types once and reuse across screens for safety and autocompletion.

---

## Deep Linking and Handling Navigation State

**Definition:**  
Deep linking enables your app to respond to URLs and route to specific screens. Navigation state can also be persisted.

**Example:**

```tsx
const linking = {
  prefixes: ['myapp://'],
  config: {
    screens: {
      Home: 'home',
      Profile: 'profile/:userId',
    },
  },
};

<NavigationContainer linking={linking}>{/* Navigators */}</NavigationContainer>
```

This allows external links or push notifications to open specific screens.

---

## Authentication Flows in Navigation

**Definition:**  
Authentication flows often use conditional navigation to switch between public and private screens.

**Example:**

```tsx
const AppNavigator = ({ isLoggedIn }: { isLoggedIn: boolean }) => (
  <NavigationContainer>
    {isLoggedIn ? <MainStack /> : <AuthStack />}
  </NavigationContainer>
);
```

Use a simple boolean flag or auth context to control which navigator is shown.

---

## Conclusion

**Key Takeaways:**
1. React Navigation integrates seamlessly with Expo and TypeScript.
2. Stack, Tab, and Drawer navigators provide flexible screen flows.
3. Typed navigation ensures correct prop handling across screens.
4. Deep linking enables routing from outside the app.
5. Auth flows are managed through conditional navigator rendering.

**Practical Exercise:**
- Create a basic stack navigator with two screens: `Login` and `Dashboard`.
- Add a type-safe param `userId` to `Dashboard`.
- Simulate a login button that navigates with a sample ID.
