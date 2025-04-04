
# Gestion d'État dans React

## Introduction
La gestion d'état dans React est un aspect crucial de la construction d'applications robustes. Dans ce cours, nous explorerons diverses solutions de gestion d'état qui peuvent vous aider à gérer efficacement l'état côté client et côté serveur dans les applications React.

## Table des Matières
1. [Redux](#redux)
2. [Recoil](#recoil)
3. [Zustand](#zustand)
4. [React Query](#react-query)
5. [Apollo Client](#apollo-client)
6. [Conclusion](#conclusion)

---

## Redux
Redux est une bibliothèque classique de gestion d'état pour React qui vous permet de gérer l'état global de manière prédictible. Il utilise un store centralisé et un flux de données unidirectionnel.

### Exemple :
```jsx
import { createStore } from 'redux';

const initialState = { count: 0 };
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
};

const store = createStore(reducer);

store.dispatch({ type: 'INCREMENT' });
console.log(store.getState()); // { count: 1 }
```
Redux offre une gestion d'état prédictible avec un store central et des actions, ce qui facilite le débogage mais nécessite souvent du code boilerplate.

---

## Recoil
Recoil est une bibliothèque de gestion d'état moderne et flexible pour React. Elle permet une approche plus fine de l'état avec des atomes (morceaux d'état) et des sélecteurs (valeurs calculées).

### Exemple :
```jsx
import { atom, useRecoilState } from 'recoil';

const countState = atom({
  key: 'countState',
  default: 0,
});

function Counter() {
  const [count, setCount] = useRecoilState(countState);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```
Recoil vous permet de gérer l'état de manière plus granulaire tout en offrant des fonctionnalités avancées telles que l'état dérivé et une isolation facile des composants.

---

## Zustand
Zustand est une bibliothèque de gestion d'état légère et minimaliste pour React qui vous permet de créer des stores avec un minimum de code boilerplate et des performances rapides.

### Exemple :
```jsx
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
}));

function Counter() {
  const { count, increment } = useStore();
  return <button onClick={increment}>{count}</button>;
}
```
Zustand est simple et très performant, utilisant les hooks React pour gérer l'état, sans avoir besoin de reducers ou d'actions.

---

## React Query
React Query est une puissante bibliothèque pour la gestion de l'état côté serveur et la récupération de données asynchrones, simplifiant le processus de gestion des requêtes asynchrones, de la mise en cache et de la synchronisation.

### Exemple :
```jsx
import { useQuery } from 'react-query';

function fetchData() {
  return fetch('https://api.example.com/data').then(res => res.json());
}

function DataComponent() {
  const { data, isLoading, error } = useQuery('data', fetchData);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error fetching data</div>;

  return <div>{JSON.stringify(data)}</div>;
}
```
React Query aide à gérer l'état du serveur avec la mise en cache, la récupération et la synchronisation automatiques, améliorant les performances et réduisant le code boilerplate.

---

## Apollo Client
Apollo Client est une solution complète de gestion d'état pour GraphQL. Il gère la récupération des données, la mise en cache et la gestion d'état, simplifiant le processus d'intégration de GraphQL avec les applications React.

### Exemple :
```jsx
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';
import { useQuery } from '@apollo/react-hooks';

const GET_DATA = gql`
  query {
    items {
      id
      name
    }
  }
`;

const client = new ApolloClient({
  uri: 'https://graphql.example.com',
  cache: new InMemoryCache(),
});

function DataComponent() {
  const { loading, error, data } = useQuery(GET_DATA, { client });

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error fetching data</div>;

  return <div>{JSON.stringify(data)}</div>;
}
```
Apollo Client simplifie la gestion des données GraphQL avec la mise en cache, la pagination et des hooks faciles à utiliser.

---

## Conclusion

### Points Clés à Retenir :
1. **Redux** est une solution de gestion d'état robuste et prédictible, mais peut impliquer beaucoup de code boilerplate.
2. **Recoil** offre une approche plus moderne avec une gestion d'état fine, prenant en charge l'état dérivé et des atomes faciles à gérer.
3. **Zustand** est une solution minimaliste et légère qui se concentre sur la simplicité et la performance sans code boilerplate complexe.
4. **React Query** est idéal pour la gestion de l'état côté serveur, la gestion de la mise en cache et la simplification de la récupération de données dans les applications React.
5. **Apollo Client** excelle dans l'intégration de GraphQL avec React, fournissant une récupération de données et une gestion d'état efficaces prêtes à l'emploi.

### Exercice Pratique :
1. Configurez une application simple en utilisant **React Query** pour récupérer des données à partir d'une API (telle qu'une API publique comme JSONPlaceholder).
2. Créez un composant de compteur en utilisant **Recoil** ou **Zustand**, et gérez son état globalement dans votre application.
