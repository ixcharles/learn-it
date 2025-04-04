
# App Router et Fonctionnalités Modernes

Un guide approfondi des nouvelles fonctionnalités de Next.js 13+ avec l'App Router, incluant le routage basé sur les fichiers, les composants serveur, la gestion des métadonnées et les limites d'erreur. Apprenez à intégrer ces outils modernes avec TypeScript pour une application plus évolutive et maintenable.

---

## Table des Matières

- [Introduction à l'App Router](#introduction-à-lapp-router)
  - [Routage Basé sur les Fichiers dans le Répertoire `app`](#routage-basé-sur-les-fichiers-dans-le-répertoire-app)
  - [Layouts et Templates](#layouts-et-templates)
- [Composants Serveur et Composants Client](#composants-serveur-et-composants-client)
  - [Différences et Cas d'Utilisation](#différences-et-cas-dutilisation)
  - [Typage des Limites Serveur/Client](#typage-des-limites-serveurclient)
- [API Metadata](#api-metadata)
  - [Définition des Métadonnées de Page avec les Types](#définition-des-métadonnées-de-page-avec-les-types)
- [UI de Chargement et Limites d'Erreur](#ui-de-chargement-et-limites-derreur)
  - [Suspense avec les Composants Serveur](#suspense-avec-les-composants-serveur)
  - [Gestion des Erreurs Typée](#gestion-des-erreurs-typée)

---

## Introduction à l'App Router

### Routage Basé sur les Fichiers dans le Répertoire `app`
Avec Next.js 13+ et l'App Router, le routage est géré par la structure des fichiers dans le répertoire `app`, offrant une navigation plus propre et intuitive.

**Exemple:**
```tsx
// app/page.tsx
export default function Home() {
  return <h1>Bienvenue sur la Page d'Accueil</h1>;
}

// app/about/page.tsx
export default function About() {
  return <h1>À Propos de Nous</h1>;
}
```

### Layouts et Templates
Les layouts et les templates sont des composants réutilisables qui aident à organiser l'interface utilisateur sur différentes pages, assurant ainsi une cohérence.

**Exemple:**
```tsx
// app/layout.tsx
export default function Layout({ children }: { children: React.ReactNode }) {
  return (
    <div>
      <header>En-tête</header>
      <main>{children}</main>
      <footer>Pied de page</footer>
    </div>
  );
}
```

---

## Composants Serveur et Composants Client

### Différences et Cas d'Utilisation
Les composants serveur sont rendus sur le serveur et envoyés au client en tant que HTML. Les composants client sont rendus sur le client, adaptés à l'interactivité.

**Exemple:**
```tsx
// Composant Serveur (app/posts/page.tsx)
export default function Posts() {
  const posts = await fetchPosts(); // Récupération côté serveur
  return (
    <div>
      {posts.map(post => <div key={post.id}>{post.title}</div>)}
    </div>
  );
}

// Composant Client (app/components/Button.tsx)
'use client';

export default function Button() {
  const handleClick = () => alert('Bouton cliqué !');
  return <button onClick={handleClick}>Cliquez-moi</button>;
}
```

### Typage des Limites Serveur/Client
Lorsque vous utilisez des composants serveur et client, assurez-vous que la limite entre eux est claire en typant correctement les props.

**Exemple:**
```tsx
// Composant Serveur
export default async function PostsPage() {
  const posts = await fetchPosts();
  return <PostsList posts={posts} />;
}

// Composant Client
'use client';
type Post = { id: number; title: string };
export default function PostsList({ posts }: { posts: Post[] }) {
  return (
    <div>
      {posts.map(post => <div key={post.id}>{post.title}</div>)}
    </div>
  );
}
```

---

## API Metadata

### Définition des Métadonnées de Page avec les Types
Next.js vous permet de définir des métadonnées spécifiques à la page, telles que les titres et les descriptions, à l'aide de l'API Metadata.

**Exemple:**
```tsx
// app/about/page.tsx
import { Metadata } from 'next';

export const metadata: Metadata = {
  title: 'À Propos de Nous',
  description: 'En savoir plus sur notre équipe et notre mission',
};

export default function AboutPage() {
  return <h1>À Propos de Nous</h1>;
}
```

---

## UI de Chargement et Limites d'Erreur

### Suspense avec les Composants Serveur
React Suspense fonctionne de manière transparente avec les composants serveur pour afficher des états de chargement pendant la récupération des données côté serveur.

**Exemple:**
```tsx
// app/posts/page.tsx
import { Suspense } from 'react';

export default function Posts() {
  return (
    <Suspense fallback={<div>Chargement...</div>}>
      <PostsList />
    </Suspense>
  );
}

// app/posts/PostsList.tsx
export default function PostsList() {
  const posts = await fetchPosts(); // Récupération côté serveur
  return (
    <div>
      {posts.map(post => <div key={post.id}>{post.title}</div>)}
    </div>
  );
}
```

### Gestion des Erreurs Typée
La gestion des erreurs avec les types vous permet de capturer et de traiter les erreurs potentielles dans votre application de manière plus prévisible.

**Exemple:**
```tsx
// app/posts/page.tsx
import { Suspense } from 'react';

const fetchPosts = async (): Promise<Post[]> => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts');
    if (!response.ok) throw new Error('Échec de la récupération des articles');
    return response.json();
  } catch (error: any) {
    console.error(error.message);
    throw new Error('Erreur lors de la récupération des articles');
  }
};

export default function PostsPage() {
  return (
    <Suspense fallback={<div>Chargement...</div>}>
      <PostsList />
    </Suspense>
  );
}

type Post = { id: number; title: string; body: string };
```

---

## Conclusion

**Points Clés à Retenir:**
- L'App Router et le routage basé sur les fichiers dans Next.js 13+ améliorent la structure du projet et la clarté de la navigation.
- Les composants serveur et client servent des cas d'utilisation différents : les composants serveur pour le rendu, les composants client pour l'interactivité.
- Les métadonnées type-safe vous permettent de définir et de gérer les détails spécifiques à la page tels que le titre et la description.
- React Suspense offre un moyen fluide de gérer les états de chargement pour les composants serveur.
- Une gestion des erreurs appropriée avec TypeScript assure une application plus robuste et fiable.

---

## Exercice Pratique

**Construire une Application Multipages avec des Composants Serveur et Client :**
1. Créez une application Next.js 13+ en utilisant l'App Router.
2. Créez plusieurs pages, chacune avec son propre layout et ses propres métadonnées.
3. Utilisez un composant serveur pour récupérer une liste d'articles depuis une API.
4. Ajoutez un composant client pour l'interactivité (par exemple, un bouton "J'aime").
5. Implémentez React Suspense pour gérer les états de chargement.
