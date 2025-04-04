
# Fondamentaux de Next.js avec TypeScript

Un guide concis et pratique pour maîtriser les concepts fondamentaux de Next.js associé à TypeScript, permettant un développement React évolutif et type-safe.

---

## Table des Matières

- [Introduction à Next.js et TypeScript](#introduction-à-nextjs-et-typescript)
  - [Qu'est-ce que Next.js](#quest-ce-que-nextjs)
  - [Pourquoi TypeScript avec Next.js](#pourquoi-typescript-avec-nextjs)
- [Configuration et Installation du Projet](#configuration-et-installation-du-projet)
  - [Installer Next.js avec TypeScript](#installer-nextjs-avec-typescript)
  - [Configurer `tsconfig.json`](#configurer-tsconfigjson)
  - [Comprendre la Structure des Fichiers Next.js](#comprendre-la-structure-des-fichiers-nextjs)
- [Bases des Pages et du Routage](#bases-des-pages-et-du-routage)
  - [Les Pages comme Routes](#les-pages-comme-routes)
  - [Routes Dynamiques](#routes-dynamiques)
  - [Routes Imbriquées](#routes-imbriquées)
  - [Routes Attrape-tout](#routes-attrape-tout)
- [Composants et Props avec TypeScript](#composants-et-props-avec-typescript)
  - [Composants Fonctionnels avec TypeScript](#composants-fonctionnels-avec-typescript)
  - [Typage des Props et des Enfants](#typage-des-props-et-des-enfants)
  - [Props par Défaut et Props Optionnelles](#props-par-défaut-et-props-optionnelles)
- [Assets Statiques et Styles](#assets-statiques-et-styles)
  - [Utilisation des Modules CSS](#utilisation-des-modules-css)
  - [Intégration de Tailwind CSS](#intégration-de-tailwind-css)
  - [Styles Globaux et Styles Portée](#styles-globaux-et-styles-portée)
- [Récupération de Données de Base](#récupération-de-données-de-base)
  - [`getStaticProps`](#getstaticprops)
  - [`getServerSideProps`](#getserversideprops)
  - [`getStaticPaths`](#getstaticpaths)

---

## Introduction à Next.js et TypeScript

### Qu'est-ce que Next.js
Un framework React pour construire des applications de qualité production avec SSR, génération statique et rendu hybride.

**Exemple:**
```bash
npx create-next-app my-app
```

### Pourquoi TypeScript avec Next.js
TypeScript ajoute un typage statique pour améliorer la fiabilité du code et l'expérience développeur dans les applications à grande échelle.

**Exemple:**
```ts
const title: string = "Hello, Next.js + TS";
```

---

## Configuration et Installation du Projet

### Installer Next.js avec TypeScript
Démarrez une application Next.js compatible TypeScript en utilisant la CLI.

**Exemple:**
```bash
npx create-next-app@latest --typescript
```

### Configurer `tsconfig.json`
Définit les options du compilateur et le comportement de vérification des types pour le projet.

**Exemple:**
```json
{
  "compilerOptions": {
    "strict": true,
    "baseUrl": ".",
    "paths": { "@/*": ["src/*"] }
  }
}
```

### Comprendre la Structure des Fichiers Next.js
Next.js repose sur une structure de fichiers basée sur des conventions.

**Exemple:**
```
/pages - Routes
/public - Assets statiques
/styles - CSS global
```

---

## Bases des Pages et du Routage

### Les Pages comme Routes
Les fichiers dans `/pages` deviennent automatiquement des routes.

**Exemple:**
```tsx
// pages/about.tsx
export default function About() {
  return <h1>About Page</h1>;
}
```

### Routes Dynamiques
Utilisez `[param].tsx` pour définir des segments dynamiques.

**Exemple:**
```tsx
// pages/post/[id].tsx
export default function Post({ params }: any) {
  return <p>Post: {params.id}</p>;
}
```

### Routes Imbriquées
Créez des hiérarchies de dossiers dans `/pages` pour des URLs imbriquées.

**Exemple:**
```
/pages/blog/index.tsx → /blog
/pages/blog/post.tsx → /blog/post
```

### Routes Attrape-tout
Utilisez `[...slug].tsx` pour correspondre à plusieurs segments de chemin.

**Exemple:**
```tsx
// pages/docs/[...slug].tsx
```

---

## Composants et Props avec TypeScript

### Composants Fonctionnels avec TypeScript
Définissez les types pour les props directement dans la signature de la fonction.

**Exemple:**
```tsx
type Props = { title: string };
const Header: React.FC<Props> = ({ title }) => <h1>{title}</h1>;
```

### Typage des Props et des Enfants
Typez `children` explicitement lorsque cela est nécessaire.

**Exemple:**
```tsx
type LayoutProps = { children: React.ReactNode };
const Layout = ({ children }: LayoutProps) => <main>{children}</main>;
```

### Props par Défaut et Props Optionnelles
Utilisez `?` pour les props optionnelles et définissez les valeurs par défaut manuellement.

**Exemple:**
```tsx
type Props = { subtitle?: string };
const Header = ({ subtitle = "Default" }: Props) => <h2>{subtitle}</h2>;
```

---

## Assets Statiques et Styles

### Utilisation des Modules CSS
Styles à portée limitée avec hachage automatique des noms de classes.

**Exemple:**
```tsx
import styles from './Button.module.css';
```

### Intégration de Tailwind CSS
Framework CSS utilitaire pour un stylage rapide.

**Exemple:**
```tsx
<button className="bg-blue-500 text-white p-2 rounded">Click Me</button>
```

### Styles Globaux et Styles Portée
Les styles globaux vont dans `pages/_app.tsx`.

**Exemple:**
```tsx
import '../styles/globals.css';
```

---

## Récupération de Données de Base

### `getStaticProps`
Récupérez les données au moment de la construction pour la génération statique.

**Exemple:**
```tsx
export async function getStaticProps() {
  return { props: { data: 'static content' } };
}
```

### `getServerSideProps`
Récupérez les données à chaque requête, côté serveur.

**Exemple:**
```tsx
export async function getServerSideProps() {
  return { props: { data: 'server content' } };
}
```

### `getStaticPaths`
Utilisé avec les pages dynamiques pour pré-générer les chemins.

**Exemple:**
```tsx
export async function getStaticPaths() {
  return { paths: [{ params: { id: '1' } }], fallback: false };
}
```

---

## Conclusion

**Points Clés à Retenir:**
- Next.js + TypeScript offre un framework fullstack puissant et évolutif.
- Le routage est basé sur les fichiers et les routes dynamiques sont faciles à implémenter.
- La génération statique et le SSR sont des fonctionnalités de premier ordre.
- TypeScript améliore la sécurité et la maintenabilité.
- Le typage des composants et une configuration de projet structurée sont essentiels pour la croissance.

---

## Exercice Pratique

**Créer une petite page d'accueil de blog :**
1. Créez une nouvelle application Next.js + TypeScript.
2. Créez un fichier `/pages/index.tsx` qui récupère et affiche des titres d'articles fictifs en utilisant `getStaticProps`.
3. Ajoutez un composant `Header` stylisé avec des props typées.
4. Utilisez les Modules CSS ou Tailwind CSS pour le stylage.
