
# Sujets avancés et projets concrets

Ce module explore les techniques avancées de React Native Expo en utilisant TypeScript, y compris les modules natifs, les animations complexes, le stockage hors ligne et les modèles d'architecture évolutifs pour les grandes applications.

## Table des matières
- [Création de modules natifs personnalisés avec TypeScript](#création-de-modules-natifs-personnalisés-avec-typescript)
- [Animations avec Reanimated et gestion des gestes](#animations-avec-reanimated-et-gestion-des-gestes)
- [Applications "hors ligne d'abord" avec SQLite et AsyncStorage](#applications-hors-ligne-dabord-avec-sqlite-et-asyncstorage)
- [Construction et optimisation d'applications React Native à grande échelle](#construction-et-optimisation-dapplications-react-native-à-grande-échelle)
- [Meilleures pratiques pour des bases de code maintenables et évolutives](#meilleures-pratiques-pour-des-bases-de-code-maintenables-et-évolutives)

---

## Création de modules natifs personnalisés avec TypeScript

**Définition :**
Expo prend en charge l'ajout de fonctionnalités natives via des plugins de configuration ou en éjectant et en écrivant des modules personnalisés.

**Approche (via plugin) :**

```ts
// plugin.js
module.exports = function withCustomPermission(config) {
  config.android = config.android || {};
  config.android.permissions = [...(config.android.permissions || []), 'android.permission.VIBRATE'];
  return config;
};
```

N'utilisez les modules natifs que lorsque les modules gérés d'Expo ne répondent pas à vos besoins.

---

## Animations avec Reanimated et gestion des gestes

**Définition :**
`react-native-reanimated` et `react-native-gesture-handler` fournissent des animations et des gestes fluides, pilotés nativement.

**Exemple (Reanimated 2) :**

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

Utilisez les gestes de `react-native-gesture-handler` pour contrôler les composants animés.

---

## Applications "hors ligne d'abord" avec SQLite et AsyncStorage

**Définition :**
Utilisez `expo-sqlite` ou `@react-native-async-storage/async-storage` pour rendre les données persistantes hors ligne pour la fiabilité et la vitesse.

**Exemple (AsyncStorage) :**

```ts
import AsyncStorage from '@react-native-async-storage/async-storage';

const saveData = async () => await AsyncStorage.setItem('user', JSON.stringify({ name: 'John' }));
const loadData = async () => JSON.parse(await AsyncStorage.getItem('user') || '{}');
```

**Exemple (SQLite) :**

```ts
import * as SQLite from 'expo-sqlite';

const db = SQLite.openDatabase('my.db');
db.transaction(tx => {
  tx.executeSql('CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT)');
  tx.executeSql('INSERT INTO users (name) VALUES (?)', ['Jane']);
});
```

---

## Construction et optimisation d'applications React Native à grande échelle

**Définition :**
La mise à l'échelle nécessite une architecture modulaire, la division du code, le chargement paresseux et une gestion efficace de l'état/des données.

**Conseils :**
- Utilisez une structure de dossiers basée sur les fonctionnalités
- Chargez paresseusement les écrans via `React.lazy` ou la navigation
- Optimisez la taille du bundle avec les importations dynamiques
- Utilisez les références de projet TypeScript pour les monorepos

**Exemple de structure de dossiers :**

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

## Meilleures pratiques pour des bases de code maintenables et évolutives

**Définition :**
L'établissement de bonnes pratiques réduit la dette technique et améliore la vélocité des développeurs.

**Meilleures pratiques :**
- Typage fort avec les interfaces et les énumérations
- Utilisez `zod` ou `yup` pour la validation à l'exécution
- Centralisez l'API, les constantes et les thèmes
- Préférez la composition à l'héritage
- Linting, formatage et hooks Git (par exemple, Husky + ESLint + Prettier)

**Exemple (API type-safe) :**

```ts
type User = { id: string; name: string };
const fetchUser = async (): Promise<User> => {
  const res = await fetch('https://api.example.com/user');
  return await res.json();
};
```

---

## Conclusion

**Points clés à retenir :**
1. Les modules natifs personnalisés étendent les capacités d'Expo en cas de besoin.
2. Utilisez Reanimated et les gestes pour des animations et des interactions performantes.
3. Les applications "hors ligne d'abord" améliorent la fiabilité en utilisant SQLite ou AsyncStorage.
4. Modularisez et chargez paresseusement pour mettre à l'échelle efficacement les grandes applications.
5. Suivez les meilleures pratiques TypeScript et architecturales pour une maintenabilité à long terme.

**Exercice pratique :**
- Create an animated, draggable card using Reanimated + Gesture Handler.
- Save the card’s position in AsyncStorage.
- Reload the position on app startup.
- Organize the feature in a standalone `/features/cards/` folder.
