
# Navigation et Routage

La navigation est un élément essentiel des applications mobiles, permettant les transitions d'écrans et le flux utilisateur. React Navigation, associé à TypeScript, offre un moyen type-safe et flexible de gérer la navigation dans les applications React Native.

## Table des matières
- [Configuration de React Navigation dans Expo](#configuration-de-react-navigation-dans-expo)
- [Navigation Stack, Tab et Drawer](#navigation-stack-tab-et-drawer)
- [Passage de Props et Type Safety dans la navigation](#passage-de-props-et-type-safety-dans-la-navigation)
- [Liens profonds et gestion de l'état de la navigation](#liens-profonds-et-gestion-de-létat-de-la-navigation)
- [Flux d'authentification dans la navigation](#flux-dauthentification-dans-la-navigation)

---

## Configuration de React Navigation dans Expo

**Définition :**
React Navigation est la librairie de navigation la plus populaire pour React Native, avec un support complet dans Expo.

**Exemple :**

```bash
npm install @react-navigation/native
npx expo install react-native-screens react-native-safe-area-context
npm install @react-navigation/native-stack
```

Configurez le conteneur de navigation :

```tsx
import { NavigationContainer } from '@react-navigation/native';

export default function App() {
  return <NavigationContainer>{/* Navigators */}</NavigationContainer>;
}
```

Encapsulez votre application avec `NavigationContainer` pour activer la prise en charge de la navigation.

---

## Navigation Stack, Tab et Drawer

**Définition :**
React Navigation prend en charge plusieurs types de navigateurs pour différents paradigmes d'interface utilisateur : stack (transitions d'écrans), tab (navigation inférieure) et drawer (menu latéral).

**Exemple :**

```tsx
import { createNativeStackNavigator } from '@react-navigation/native-stack';
const Stack = createNativeStackNavigator();

<Stack.Navigator>
  <Stack.Screen name="Home" component={HomeScreen} />
  <Stack.Screen name="Details" component={DetailsScreen} />
</Stack.Navigator>
```

Vous pouvez imbriquer des navigateurs pour des mises en page avancées (par exemple, des onglets à l'intérieur d'un tiroir).

---

## Passage de Props et Type Safety dans la navigation

**Définition :**
React Navigation s'intègre à TypeScript pour appliquer un passage de props sécurisé entre les écrans.

**Exemple :**

```ts
type RootStackParamList = {
  Home: undefined;
  Profile: { userId: string };
};

const Stack = createNativeStackNavigator<RootStackParamList>();

// Usage
navigation.navigate('Profile', { userId: '123' });
```

Définissez vos types de paramètres une seule fois et réutilisez-les sur tous les écrans pour la sécurité et l'autocomplétion.

---

## Liens profonds et gestion de l'état de la navigation

**Définition :**
Les liens profonds permettent à votre application de répondre aux URL et de router vers des écrans spécifiques. L'état de la navigation peut également être rendu persistant.

**Exemple :**

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

Cela permet aux liens externes ou aux notifications push d'ouvrir des écrans spécifiques.

---

## Flux d'authentification dans la navigation

**Définition :**
Les flux d'authentification utilisent souvent une navigation conditionnelle pour basculer entre les écrans publics et privés.

**Exemple :**

```tsx
const AppNavigator = ({ isLoggedIn }: { isLoggedIn: boolean }) => (
  <NavigationContainer>
    {isLoggedIn ? <MainStack /> : <AuthStack />}
  </NavigationContainer>
);
```

Utilisez un simple indicateur booléen ou un contexte d'authentification pour contrôler quel navigateur est affiché.

---

## Conclusion

**Points clés à retenir :**
1. React Navigation s'intègre de manière transparente avec Expo et TypeScript.
2. Les navigateurs Stack, Tab et Drawer offrent des flux d'écrans flexibles.
3. La navigation typée assure une gestion correcte des props entre les écrans.
4. Les liens profonds permettent le routage depuis l'extérieur de l'application.
5. Les flux d'authentification sont gérés par le rendu conditionnel des navigateurs.

**Exercice pratique :**
- Create a basic stack navigator with two screens: `Login` and `Dashboard`.
- Add a type-safe param `userId` to `Dashboard`.
- Simulate a login button that navigates with a sample ID.
