
# Gestion d'État et Récupération de Données dans React Native

**Introduction**
Dans ce cours, vous maîtriserez la gestion d'état et la récupération de données dans React Native en utilisant des bibliothèques modernes comme **Zustand**, **Recoil** et **React Query**. Apprenez quand et comment gérer efficacement les états locaux et globaux tout en récupérant et en mettant en cache les données du serveur.

## Table des Matières
1. [Comprendre la Gestion d'État dans React Native](#understanding-state-management-in-react-native)
    - [État Local vs. État Global](#local-state-vs-global-state)
    - [Choisir la Bonne Bibliothèque de Gestion d'État](#choosing-the-right-state-management-library)
2. [Bibliothèques de Gestion d'État](#state-management-libraries)
    - [Gestion de l'État avec Zustand](#managing-state-with-zustand)
    - [Utilisation de Recoil pour les Structures d'État Complexes](#using-recoil-for-complex-state-structures)
    - [Gestion de l'État Côté Serveur avec React Query](#server-side-state-management-with-react-query)
3. [Meilleures Pratiques et Performance](#best-practices--performance)
    - [Stratégies de Mise en Cache et de Synchronisation](#caching-and-synchronization-strategies)
    - [Optimisation des Performances pour la Gestion d'État](#optimizing-performance-for-state-management)

---

## Comprendre la Gestion d'État dans React Native

### État Local vs. État Global
- L'**état local** fait référence à l'état qui n'est nécessaire qu'au sein d'un seul composant.
- L'**état global** fait référence à l'état qui doit être partagé entre plusieurs composants.

**Exemple**
État local avec **useState** de React :
```jsx
const [count, setCount] = useState(0);
```

État global en utilisant l'**API Context** :
```jsx
const CountContext = React.createContext();

const App = () => {
  const [count, setCount] = useState(0);
  return (
    <CountContext.Provider value={{ count, setCount }}>
      <ChildComponent />
    </CountContext.Provider>
  );
};
```

### Choisir la Bonne Bibliothèque de Gestion d'État
Le choix de la bonne bibliothèque dépend de la complexité de votre application :
- **Zustand** pour un état global simple.
- **Recoil** pour une gestion d'état complexe avec des atomes et des sélecteurs.
- **React Query** pour la gestion de l'état côté serveur avec la mise en cache.

---

## Bibliothèques de Gestion d'État

### Gestion de l'État avec Zustand
**Zustand** est une bibliothèque de gestion d'état minimale et rapide avec une API simple et d'excellentes performances.

**Exemple**
```bash
npm install zustand
```

```jsx
import create from 'zustand';

const useStore = create(set => ({
  count: 0,
  increment: () => set(state => ({ count: state.count + 1 })),
}));

const App = () => {
  const { count, increment } = useStore();
  return (
    <View>
      <Text>{count}</Text>
      <Button onPress={increment} title="Increment" />
    </View>
  );
};
```

### Utilisation de Recoil pour les Structures d'État Complexes
**Recoil** offre un moyen puissant de gérer un état complexe avec des atomes et des sélecteurs, permettant un contrôle précis des dépendances d'état.

**Exemple**
```bash
npm install recoil
```

```jsx
import { atom, useRecoilState } from 'recoil';

const countState = atom({
  key: 'countState',
  default: 0,
});

const App = () => {
  const [count, setCount] = useRecoilState(countState);
  return (
    <View>
      <Text>{count}</Text>
      <Button onPress={() => setCount(count + 1)} title="Increment" />
    </View>
  );
};
```

### Gestion de l'État Côté Serveur avec React Query
**React Query** simplifie la gestion de l'état côté serveur en abstraisant la récupération, la mise en cache et la synchronisation des données.

**Exemple**
```bash
npm install react-query
```

```jsx
import { useQuery } from 'react-query';

const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  return response.json();
};

const App = () => {
  const { data, isLoading, error } = useQuery('data', fetchData);

  if (isLoading) return <Text>Loading...</Text>;
  if (error) return <Text>Error fetching data</Text>;

  return <Text>{JSON.stringify(data)}</Text>;
};
```

---

## Meilleures Pratiques et Performance

### Stratégies de Mise en Cache et de Synchronisation
Pour optimiser la récupération de données et la gestion d'état, tirez parti des stratégies de mise en cache :
- Utilisez **React Query** pour mettre en cache les réponses du serveur.
- Pour l'état local, évitez les rendus inutiles en utilisant **React.memo** et **useMemo**.

**Exemple**
Mise en cache avec **React Query** :
```jsx
const { data } = useQuery('posts', fetchPosts, { cacheTime: 10000 });
```

### Optimisation des Performances pour la Gestion d'État
- **Évitez les états profondément imbriqués** : Décomposez l'état en parties plus petites.
- **Utilisez des sélecteurs** : Dans **Recoil**, utilisez des sélecteurs pour dériver l'état afin d'éviter les calculs redondants.

**Exemple**
Optimisation des sélecteurs **Recoil** :
```jsx
import { selector } from 'recoil';

const doubledCountState = selector({
  key: 'doubledCountState',
  get: ({ get }) => {
    const count = get(countState);
    return count * 2;
  },
});
```

---

## Conclusion

### Points Clés
1. L'**état local** est le mieux adapté aux besoins d'un seul composant, tandis que l'**état global** est nécessaire pour les données partagées entre plusieurs composants.
2. **Zustand** est parfait pour une gestion d'état global simple avec une surcharge minimale.
3. **Recoil** offre une API puissante pour gérer un état complexe grâce à des atomes et des sélecteurs.
4. **React Query** simplifie la récupération et la mise en cache des données, facilitant la gestion de l'état côté serveur.
5. L'optimisation des performances nécessite une conception d'état et des stratégies de mise en cache soignées pour minimiser les rendus.

### Exercice Pratique
1. Créez une application utilisant **Zustand** pour la gestion d'état global et **React Query** pour la récupération de données à partir d'une API simulée.
2. Implémentez un atome **Recoil** pour gérer un compteur et créez un sélecteur qui renvoie le double de la valeur du compteur.
3. Optimisez votre application en implémentant la mise en cache dans **React Query** et en utilisant **React.memo** pour les composants qui ne nécessitent pas de rendus.
