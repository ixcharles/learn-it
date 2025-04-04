
# Récupération de Données, Mise en Cache & Intégration d'API

Une récupération de données, une mise en cache et une intégration d'API efficaces sont essentielles pour construire des applications React performantes et fiables. Ce cours couvre les techniques et les librairies modernes comme React Query et GraphQL, ainsi que les meilleures pratiques pour la gestion des données.

---

## Table des Matières
- [Récupération de Données avec Fetch API et Axios](#fetching-data-with-fetch-api-and-axios)
- [React Query (TanStack Query)](#react-query-tanstack-query)
  - [Mise en Cache des Requêtes](#query-caching)
  - [Invalidation des Requêtes](#query-invalidation)
  - [Mutations et Mises à Jour Optimistes](#mutations-and-optimistic-updates)
  - [Requêtes Infinies et Pagination](#infinite-queries-and-pagination)
- [Travailler avec GraphQL et Apollo Client](#working-with-graphql-and-apollo-client)
- [Comparaison entre SWR et React Query](#swr-vs-react-query-comparison)
- [Expérience Utilisateur des États d'Erreur et de Chargement](#error-and-loading-states-ux)
- [Conclusion & Points Clés](#conclusion--key-takeaways)
- [Exercice Pratique](#practical-exercise)

---

## Récupération de Données avec Fetch API et Axios

### Fetch API

**Définition :** L'API Fetch fournit un moyen simple d'effectuer des requêtes HTTP et de gérer les réponses de manière asynchrone.
**Exemple :**
```jsx
const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
};

const App = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetchData().then(setData);
  }, []);

  return <div>{JSON.stringify(data)}</div>;
};
```

### Axios

**Définition :** Axios est un client HTTP basé sur les Promises pour le navigateur et Node.js, avec analyse JSON automatique et gestion des erreurs.
**Exemple :**
```jsx
import axios from 'axios';

const fetchData = async () => {
  const response = await axios.get('https://api.example.com/data');
  return response.data;
};

const App = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetchData().then(setData);
  }, []);

  return <div>{JSON.stringify(data)}</div>;
};
```

---

## React Query (TanStack Query)

### Mise en Cache des Requêtes

**Définition :** React Query met automatiquement en cache les données pour éviter les nouvelles récupérations inutiles, améliorant ainsi les performances.
**Exemple :**
```jsx
import { useQuery } from 'react-query';

const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  return response.json();
};

const App = () => {
  const { data, isLoading } = useQuery('data', fetchData);

  if (isLoading) return <div>Chargement...</div>;

  return <div>{JSON.stringify(data)}</div>;
};
```

### Invalidation des Requêtes

**Définition :** L'invalidation des requêtes force React Query à récupérer à nouveau les données lorsque certaines conditions sont remplies.
**Exemple :**
```jsx
const { data, refetch } = useQuery('data', fetchData);

const handleUpdate = () => {
  // Mettre à jour les données et invalider la requête
  refetch();
};
```

### Mutations et Mises à Jour Optimistes

**Définition :** Les mutations dans React Query permettent de modifier les données sur le serveur, avec des mises à jour optimistes permettant une expérience utilisateur fluide pendant l'attente de la réponse du serveur.
**Exemple :**
```jsx
import { useMutation, useQueryClient } from 'react-query';

const updateData = async (newData) => {
  await fetch('/update', { method: 'POST', body: JSON.stringify(newData) });
};

const App = () => {
  const queryClient = useQueryClient();

  const mutation = useMutation(updateData, {
    onMutate: (variables) => {
      // Mise à jour optimiste
      queryClient.setQueryData('data', (oldData) => [...oldData, variables]);
    },
    onSettled: () => {
      queryClient.invalidateQueries('data');
    },
  });

  return <button onClick={() => mutation.mutate({ id: 1, text: 'Mis à jour !' })}>Mettre à jour</button>;
};
```

### Requêtes Infinies et Pagination

**Définition :** Les requêtes infinies dans React Query sont utilisées pour gérer les données paginées, facilitant la récupération de nouvelles pages au fur et à mesure que l'utilisateur fait défiler.
**Exemple :**
```jsx
import { useInfiniteQuery } from 'react-query';

const fetchPage = async ({ pageParam = 1 }) => {
  const response = await fetch(`https://api.example.com/data?page=${pageParam}`);
  return response.json();
};

const App = () => {
  const { data, fetchNextPage, hasNextPage, isLoading } = useInfiniteQuery('data', fetchPage, {
    getNextPageParam: (lastPage, pages) => lastPage.nextPage ?? false,
  });

  if (isLoading) return <div>Chargement...</div>;

  return (
    <div>
      {data.pages.map((page, i) => (
        <div key={i}>
          {page.items.map((item) => (
            <div key={item.id}>{item.name}</div>
          ))}
        </div>
      ))}
      {hasNextPage && <button onClick={() => fetchNextPage()}>Charger Plus</button>}
    </div>
  );
};
```

---

## Travailler avec GraphQL et Apollo Client

**Définition :** Apollo Client est une librairie complète de gestion d'état qui permet une interaction efficace avec les API GraphQL.
**Exemple :**
```jsx
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://api.example.com/graphql',
  cache: new InMemoryCache(),
});

const GET_DATA = gql`
  query GetData {
    data {
      id
      name
    }
  }
`;

const App = () => {
  const { loading, error, data } = useQuery(GET_DATA, { client });

  if (loading) return <div>Chargement...</div>;
  if (error) return <div>Erreur : {error.message}</div>;

  return <div>{JSON.stringify(data)}</div>;
};
```

---

## Comparaison entre SWR et React Query

**Définition :** SWR (stale-while-revalidate) et React Query sont deux librairies pour la récupération, la mise en cache et la synchronisation des données, mais React Query offre plus de fonctionnalités intégrées pour les scénarios complexes comme les mutations et la pagination, tandis que SWR est plus simple.
**Différences Clés :**
- **React Query :** Plus de fonctionnalités avancées comme l'invalidation des requêtes, la pagination et la gestion des mutations.
- **SWR :** Plus léger, plus simple et plus axé sur la récupération de données avec moins de configuration.

---

## Expérience Utilisateur des États d'Erreur et de Chargement

**Définition :** La gestion des états de chargement et d'erreur dans votre interface utilisateur assure une meilleure expérience utilisateur en fournissant un retour d'information pendant les processus de récupération de données.
**Exemple :**
```jsx
const App = () => {
  const { data, isLoading, isError, error } = useQuery('data', fetchData);

  if (isLoading) return <div>Chargement...</div>;
  if (isError) return <div>Erreur : {error.message}</div>;

  return <div>{JSON.stringify(data)}</div>;
};
```

**Meilleures Pratiques :**
- Afficher des indicateurs de chargement ou des squelettes pendant la récupération des données.
- Afficher des messages d'erreur conviviaux ou des options de nouvelle tentative en cas d'erreur.

---

## Conclusion & Points Clés

- **Fetch API et Axios** sont fondamentaux pour la récupération de données simple, Axios offrant des fonctionnalités améliorées comme l'analyse JSON automatique.
- **React Query** simplifie la récupération de données, la mise en cache et la gestion d'état avec des optimisations intégrées comme la mise en cache des requêtes, les mutations et la pagination.
- **Apollo Client** est idéal pour la gestion des données avec les API GraphQL, offrant une mise en cache et une gestion des requêtes avancées.
- **SWR** est une alternative plus simple à React Query, axée sur une récupération de données efficace et minimale.
- La gestion des **états de chargement** et **d'erreur** est cruciale pour offrir une expérience utilisateur fluide dans les applications.

---

## Exercice Pratique

Construisez une simple application de blog :
1. Récupérez une liste d'articles de blog en utilisant **React Query** ou **Axios**.
2. Implémentez la pagination pour charger plus d'articles au fur et à mesure que l'utilisateur fait défiler (utilisez les **Requêtes Infinies** dans React Query).
3. Ajoutez des états d'erreur et de chargement avec un retour d'information clair à l'utilisateur.
4. Intégrez **Apollo Client** pour récupérer les articles de blog à partir d'une API GraphQL (si possible).
