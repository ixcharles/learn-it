
# Navigation Avancée et Gestion des Gestes dans React Native

**Introduction**
Ce cours explore les concepts avancés de navigation et de gestion des gestes dans React Native. Apprenez à créer des flux de navigation et des interactions fluides et transparents dans votre application en utilisant des bibliothèques telles que **react-navigation**, **react-native-gesture-handler** et **react-native-reanimated**.

## Table des Matières
1. [Fondamentaux de la Navigation](#navigation-fundamentals)
    - [Introduction à la Navigation dans React Native](#introduction-to-navigation-in-react-native)
    - [Configuration de react-navigation](#setting-up-react-navigation)
2. [Techniques de Navigation Avancées](#advanced-navigation-techniques)
    - [Navigation Stack, Tiroir et Onglets](#stack-drawer-and-tab-navigation)
    - [Liens Profonds et Navigation Dynamique](#deep-linking--dynamic-navigation)
3. [Gestion des Gestes et Animations](#gesture-handling--animations)
    - [Utilisation de react-native-gesture-handler pour des Interactions Fluides](#using-react-native-gesture-handler-for-smooth-interactions)
    - [Animations Complexes avec react-native-reanimated](#complex-animations-with-react-native-reanimated)
4. [Performance de la Navigation et Meilleures Pratiques](#navigation-performance--best-practices)
    - [Optimisation des Performances de la Navigation](#optimizing-navigation-performance)
    - [Gestion de la Navigation dans les Grandes Applications](#handling-navigation-in-large-applications)

---

## Fondamentaux de la Navigation

### Introduction à la Navigation dans React Native
La navigation dans React Native fait référence au système qui contrôle la manière dont les utilisateurs se déplacent entre les différents écrans ou vues de l'application. Une navigation appropriée améliore l'UX et la convivialité de l'application.

**Exemple**
```bash
npm install @react-navigation/native @react-navigation/stack react-native-screens react-native-safe-area-context
```

### Configuration de react-navigation
Pour commencer avec la navigation, vous devez installer **react-navigation** et configurer une navigation de base à l'aide d'un navigateur de pile (stack navigator).

**Exemple**
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

## Techniques de Navigation Avancées

### Navigation Stack, Tiroir et Onglets
La navigation avancée implique la combinaison de différents navigateurs tels que **Stack**, **Drawer** et **Tab** pour créer des flux de navigation multicouches.

**Exemple**
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

### Liens Profonds et Navigation Dynamique
Les liens profonds permettent aux utilisateurs d'ouvrir directement des écrans spécifiques de l'application à partir d'un lien externe, ce qui permet une navigation dynamique et contextuelle.

**Exemple**
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

## Gestion des Gestes et Animations

### Utilisation de react-native-gesture-handler pour des Interactions Fluides
**react-native-gesture-handler** vous permet d'implémenter des gestes tactiles complexes, tels que le balayage et le glissement, afin d'améliorer l'interactivité de l'application.

**Exemple**
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

### Animations Complexes avec react-native-reanimated
**react-native-reanimated** fournit une API puissante pour créer des animations complexes qui s'exécutent sur le thread natif pour des performances fluides.

**Exemple**
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

## Performance de la Navigation et Meilleures Pratiques

### Optimisation des Performances de la Navigation
L'optimisation des performances est cruciale dans les grandes applications pour éviter les rendus inutiles et garantir des transitions fluides. Utilisez des techniques de mémorisation et de chargement paresseux pour améliorer les performances de la navigation.

**Exemple**
```jsx
import { useMemo } from 'react';

const MemoizedScreen = React.memo(ScreenComponent);
```

### Gestion de la Navigation dans les Grandes Applications
À mesure que les applications grandissent, la gestion de la navigation et des états devient plus complexe. Utilisez des techniques telles que le **chargement paresseux de React Navigation** et les **navigateurs imbriqués** pour maintenir l'application performante.

**Exemple**
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

### Points Clés
1. **react-navigation** est essentiel pour naviguer entre les différents écrans dans React Native.
2. La combinaison des navigateurs **Stack**, **Drawer** et **Tab** crée des flux de navigation complexes et multicouches.
3. Les **liens profonds** permettent aux utilisateurs de naviguer directement vers des écrans spécifiques à l'aide d'URL externes.
4. **react-native-gesture-handler** permet des interactions gestuelles fluides pour une meilleure expérience utilisateur.
5. Utilisez **react-native-reanimated** pour des animations complexes qui s'exécutent en douceur sur le thread natif.

### Exercice Pratique
1. Créez une application React Native avec plusieurs types de navigation (Stack, Drawer, Tab).
2. Implémentez des liens profonds pour naviguer vers un écran de profil à partir d'un lien externe.
3. Ajoutez des gestes de balayage à un écran à l'aide de **react-native-gesture-handler** et créez une animation fluide avec **react-native-reanimated**.
