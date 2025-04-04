
# Gestion du Réseau et Récupération de Données dans React

## Introduction
Une récupération et une gestion efficaces des données sont essentielles pour construire des applications React interactives et dynamiques. Dans cette section, nous explorerons deux outils puissants, Axios et React Query, qui rationalisent les appels API et la gestion de l'état dans les applications React.

## Table des Matières
1. [Axios](#axios)
2. [React Query](#react-query)
3. [Conclusion](#conclusion)

---

## Axios
Axios est un client HTTP populaire, basé sur des promesses, pour effectuer des requêtes API dans React. Il permet une gestion facile des requêtes HTTP asynchrones et fournit une API claire pour traiter les réponses et les erreurs.

### Exemple :
1. Installez Axios :
   ```bash
   npm install axios
   ```
2. Effectuez une requête GET :
   ```jsx
   import axios from 'axios';
   import { useState, useEffect } from 'react';

   function DataFetching() {
     const [data, setData] = useState([]);
     const [loading, setLoading] = useState(true);

     useEffect(() => {
       axios.get('https://jsonplaceholder.typicode.com/posts')
         .then((response) => {
           setData(response.data);
           setLoading(false);
         })
         .catch((error) => {
           console.error('Erreur lors de la récupération des données :', error);
           setLoading(false);
         });
     }, []);

     if (loading) return <div>Chargement...</div>;

     return (
       <div>
         <ul>
           {data.map(item => (
             <li key={item.id}>{item.title}</li>
           ))}
         </ul>
       </div>
     );
   }
   ```

#### Fonctionnalités Clés :
- **API basée sur les promesses** : Axios utilise des promesses pour la gestion des requêtes asynchrones, ce qui facilite l'enchaînement de `.then()` et `.catch()` ou l'utilisation de `async/await`.
- **Analyse JSON automatique** : Axios analyse automatiquement la réponse au format JSON.
- **Intercepteurs de requêtes et de réponses** : Modifiez ou enregistrez les requêtes et les réponses avant qu'elles ne soient traitées.
- **Gestion des erreurs** : Axios fournit un moyen robuste de gérer les erreurs HTTP, telles que les réponses 404 ou 500.

---

## React Query
React Query est une puissante bibliothèque qui simplifie la récupération de données, la mise en cache et la synchronisation de l'état du serveur. Elle automatise des tâches telles que la mise en cache, la synchronisation des données en arrière-plan et la pagination, ce qui facilite la gestion des données côté serveur dans les applications React.

### Exemple :
1. Installez React Query :
   ```bash
   npm install react-query
   ```
2. Récupérez des données à l'aide de React Query :
   ```jsx
   import { useQuery } from 'react-query';

   function DataFetching() {
     const { data, isLoading, error } = useQuery('posts', () =>
       fetch('https://jsonplaceholder.typicode.com/posts')
         .then(res => res.json())
     );

     if (isLoading) return <div>Chargement...</div>;
     if (error) return <div>Erreur : {error.message}</div>;

     return (
       <div>
         <ul>
           {data.map(item => (
             <li key={item.id}>{item.title}</li>
           ))}
         </ul>
       </div>
     );
   }
   ```

#### Fonctionnalités Clés :
- **Mise en cache** : React Query met automatiquement en cache les réponses du serveur, réduisant ainsi le besoin de requêtes répétées.
- **Récupération en arrière-plan** : Il prend en charge la récupération des données en arrière-plan, garantissant que l'application dispose toujours des données les plus récentes.
- **Gestion automatique des erreurs** : React Query fournit des états d'erreur et de chargement intégrés, simplifiant la gestion de la récupération des données.
- **Synchronisation des données** : Synchronisez facilement les données du serveur dans toute votre application sans vous soucier des états incohérents.
- **Pagination et défilement infini** : Prise en charge intégrée de la gestion des données paginées ou à défilement infini.

---

## Conclusion

### Points Clés à Retenir :
1. **Axios** est un client HTTP flexible, basé sur des promesses, pour effectuer des requêtes API dans React, avec une gestion robuste des erreurs et une analyse JSON automatique.
2. **React Query** est une puissante bibliothèque de récupération de données qui automatise la mise en cache, la synchronisation et la récupération en arrière-plan des données côté serveur, simplifiant la gestion de l'état dans les applications React.

### Exercice Pratique :
1. Utilisez **Axios** pour récupérer une liste d'utilisateurs à partir d'une API publique (comme JSONPlaceholder) et affichez leurs noms dans un composant React.
2. Implémentez **React Query** pour récupérer et afficher une liste d'articles, en assurant une gestion appropriée du chargement, des erreurs et de la mise en cache des données.
