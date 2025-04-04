
# Gestion et Intégration des Données

Un guide complet pour la gestion de la récupération de données, de la consommation d'API et de l'intégration de bases de données dans les projets Next.js utilisant TypeScript, se concentrant sur des outils populaires comme Axios, SWR, React Query et Prisma.

---

## Table des Matières

- [Consommation d'APIs REST et GraphQL](#consommation-dapis-rest-et-graphql)
  - [Axios/Fetch avec TypeScript](#axiosfetch-avec-typescript)
  - [Requêtes et Mutations GraphQL Typées](#requêtes-et-mutations-graphql-typées)
- [SWR et React Query](#swr-et-react-query)
  - [Récupération de Données Type-Safe](#récupération-de-données-type-safe)
  - [Mise en Cache et Mutations](#mise-en-cache-et-mutations)
- [Actions et Fonctions Serveur (App Router)](#actions-et-fonctions-serveur-app-router)
  - [Utilisation des Actions Serveur avec les Types](#utilisation-des-actions-serveur-avec-les-types)
- [Intégration de Base de Données](#intégration-de-base-de-données)
  - [Utilisation de Prisma avec TypeScript](#utilisation-de-prisma-avec-typescript)
  - [Requêtes DB Type-Safe](#requêtes-db-type-safe)

---

## Consommation d'APIs REST et GraphQL

### Axios/Fetch avec TypeScript
Axios et Fetch peuvent être utilisés pour effectuer des requêtes API tout en maintenant la sécurité des types avec TypeScript.

**Exemple:**
```tsx
import axios from 'axios';

type Post = { id: number; title: string; body: string };

const fetchPosts = async (): Promise<Post[]> => {
  const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
  return response.data;
};

const posts = await fetchPosts();
```

### Requêtes et Mutations GraphQL Typées
Les requêtes et mutations GraphQL peuvent être typées à l'aide d'Apollo Client ou d'autres clients GraphQL pour la prise en charge de TypeScript.

**Exemple:**
```tsx
import { gql } from '@apollo/client';

const GET_POSTS = gql`
  query GetPosts {
    posts {
      id
      title
      body
    }
  }
`;

type Post = { id: number; title: string; body: string };

const { data, error } = useQuery<{ posts: Post[] }>(GET_POSTS);
```

---

## SWR et React Query

### Récupération de Données Type-Safe
SWR et React Query offrent des hooks faciles à utiliser pour la récupération de données tout en prenant en charge TypeScript pour les requêtes type-safe.

**Exemple (SWR):**
```tsx
import useSWR from 'swr';

type Post = { id: number; title: string; body: string };

const fetcher = (url: string) => fetch(url).then((res) => res.json());

const Posts = () => {
  const { data, error } = useSWR<Post[]>('https://jsonplaceholder.typicode.com/posts', fetcher);
  if (error) return <div>Erreur lors du chargement des articles</div>;
  if (!data) return <div>Chargement...</div>;

  return <ul>{data.map((post) => <li key={post.id}>{post.title}</li>)}</ul>;
};
```

**Exemple (React Query):**
```tsx
import { useQuery } from 'react-query';

type Post = { id: number; title: string; body: string };

const fetchPosts = async (): Promise<Post[]> => {
  const response = await fetch('https://jsonplaceholder.typicode.com/posts');
  return response.json();
};

const Posts = () => {
  const { data, error } = useQuery<Post[]>('posts', fetchPosts);

  if (error) return <div>Erreur lors du chargement des articles</div>;
  if (!data) return <div>Chargement...</div>;

  return <ul>{data.map((post) => <li key={post.id}>{post.title}</li>)}</ul>;
};
```

### Mise en Cache et Mutations
React Query et SWR gèrent automatiquement la mise en cache et fournissent des API faciles pour les mutations (création/mise à jour/suppression de données).

**Exemple (Mutation React Query):**
```tsx
import { useMutation } from 'react-query';

const createPost = async (post: { title: string; body: string }) => {
  const response = await fetch('/api/posts', {
    method: 'POST',
    body: JSON.stringify(post),
  });
  return response.json();
};

const NewPost = () => {
  const mutation = useMutation(createPost);

  const handleSubmit = (event: React.FormEvent) => {
    event.preventDefault();
    const newPost = { title: 'New Post', body: 'This is a new post.' };
    mutation.mutate(newPost);
  };

  return <button onClick={handleSubmit}>Créer un Article</button>;
};
```

---

## Actions et Fonctions Serveur (App Router)

### Utilisation des Actions Serveur avec les Types
Les fonctions côté serveur dans l'App Router (Next.js 13+) peuvent être typées pour l'interaction API et la récupération de données.

**Exemple:**
```tsx
// app/api/posts/route.ts
import { NextResponse } from 'next/server';

type Post = { id: number; title: string; body: string };

export async function GET() {
  const posts: Post[] = await fetch('https://jsonplaceholder.typicode.com/posts').then((res) => res.json());
  return NextResponse.json(posts);
}
```

---

## Intégration de Base de Données

### Utilisation de Prisma avec TypeScript
Prisma est un ORM qui permet des requêtes de base de données type-safe avec TypeScript.

**Exemple:**
```ts
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

const getAllPosts = async () => {
  const posts = await prisma.post.findMany();
  return posts;
};
```

### Requêtes DB Type-Safe
Prisma génère automatiquement des types pour votre schéma de base de données, garantissant que toutes les requêtes sont type-safe.

**Exemple:**
```ts
const createPost = async (title: string, body: string) => {
  const newPost = await prisma.post.create({
    data: { title, body },
  });
  return newPost;
};
```

---

## Conclusion

**Points Clés à Retenir:**
- Axios et Fetch facilitent l'intégration d'API avec la prise en charge de TypeScript pour les réponses typées.
- Les requêtes et mutations GraphQL peuvent être typées pour une meilleure expérience développeur.
- SWR et React Query gèrent efficacement la mise en cache, les mutations et la récupération de données type-safe.
- Les Actions Serveur dans l'App Router offrent une intégration transparente de la logique côté serveur avec la sécurité des types.
- Prisma propose des requêtes de base de données type-safe avec génération automatique de types à partir de votre schéma.

---

## Exercice Pratique

**Créer une Application de Blog Type-Safe :**
1. Créez une application Next.js avec Prisma et configurez votre schéma de base de données.
2. Créez une route API pour récupérer tous les articles de blog.
3. Utilisez SWR ou React Query pour récupérer et afficher les articles sur le front-end.
4. Implémentez une mutation pour créer un nouvel article et l'afficher après sa création réussie.
