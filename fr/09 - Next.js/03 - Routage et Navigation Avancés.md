
# Routage et Navigation Avancés

Un guide complet pour maîtriser le routage et la navigation avancés dans Next.js, couvrant les routes dynamiques, la navigation programmatique, le middleware et l'internationalisation.

---

## Table des Matières

- [Exploration Approfondie du Routage Dynamique](#exploration-approfondie-du-routage-dynamique)
  - [Routes Attrape-tout Optionnelles](#routes-attrape-tout-optionnelles)
  - [Pages de Repli](#pages-de-repli)
- [Navigation Programmatique](#navigation-programmatique)
  - [Hook `useRouter`](#hook-userouter)
  - [Paramètres de Requête avec Types](#paramètres-de-requête-avec-types)
- [Middleware et Fonctions Edge](#middleware-et-fonctions-edge)
  - [Écriture de Middleware](#écriture-de-middleware)
  - [Typage des Fonctions Middleware](#typage-des-fonctions-middleware)
- [Routage Internationalisé](#routage-internationalisé)
  - [Configuration de l'i18n](#configuration-de-li18n)
  - [Routage Spécifique à la Locale](#routage-spécifique-à-la-locale)

---

## Exploration Approfondie du Routage Dynamique

### Routes Attrape-tout Optionnelles
Les routes attrape-tout optionnelles permettent de capturer un nombre variable de segments de chemin tout en étant optionnelles.

**Exemple:**
```tsx
// pages/blog/[...slug].tsx
export default function Blog({ slug }: { slug?: string[] }) {
  return <div>Blog: {slug?.join('/')}</div>;
}
```

### Pages de Repli
Les pages de repli vous permettent de définir un état de chargement pour les chemins statiques non générés au moment de la construction.

**Exemple:**
```tsx
// pages/blog/[id].tsx
export async function getStaticPaths() {
  return {
    paths: [{ params: { id: '1' } }],
    fallback: 'blocking', // 'true' ou 'false' ou 'blocking'
  };
}
```

---

## Navigation Programmatique

### Hook `useRouter`
Le hook `useRouter` donne accès à l'objet routeur et permet la navigation programmatique.

**Exemple:**
```tsx
import { useRouter } from 'next/router';

const NavigateButton = () => {
  const router = useRouter();

  const handleNavigate = () => {
    router.push('/about');
  };

  return <button onClick={handleNavigate}>Go to About</button>;
};
```

### Paramètres de Requête avec Types
Les paramètres de requête type-safe aident à garantir la structure correcte des paramètres d'URL.

**Exemple:**
```tsx
import { useRouter } from 'next/router';

const Page = () => {
  const router = useRouter();
  const { id } = router.query; // id est une chaîne de caractères ou undefined par défaut

  if (typeof id === 'string') {
    return <div>Post ID: {id}</div>;
  }

  return <div>Loading...</div>;
};
```

---

## Middleware et Fonctions Edge

### Écriture de Middleware
Le middleware dans Next.js vous permet d'exécuter une logique personnalisée avant de servir une requête.

**Exemple:**
```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(req: Request) {
  const url = req.url;
  if (url.includes('restricted')) {
    return NextResponse.redirect(new URL('/login', url));
  }
  return NextResponse.next();
}
```

### Typage des Fonctions Middleware
Typez vos fonctions middleware pour un meilleur contrôle et une meilleure sécurité des types.

**Exemple:**
```tsx
// middleware.ts
import { NextResponse } from 'next/server';
import { NextRequest } from 'next/server';

export function middleware(req: NextRequest) {
  const token = req.cookies.get('authToken');
  if (!token) {
    return NextResponse.redirect(new URL('/login', req.url));
  }
  return NextResponse.next();
}
```

---

## Routage Internationalisé

### Configuration de l'i18n
Next.js prend en charge le routage internationalisé en configurant la propriété `i18n` dans `next.config.js`.

**Exemple:**
```js
// next.config.js
module.exports = {
  i18n: {
    locales: ['en', 'fr', 'es'],
    defaultLocale: 'en',
  },
};
```

### Routage Spécifique à la Locale
Next.js permet un routage basé sur la locale, afin que les utilisateurs puissent accéder au contenu dans différentes langues.

**Exemple:**
```tsx
// pages/[locale]/index.tsx
export default function Home({ locale }: { locale: string }) {
  return <div>Current Locale: {locale}</div>;
}
```

---

## Conclusion

**Points Clés à Retenir:**
- Les routes attrape-tout optionnelles permettent une correspondance d'URL flexible avec des paramètres optionnels.
- Les pages de repli permettent de gérer les chemins manquants en affichant des états de chargement.
- La navigation programmatique à l'aide de `useRouter` est un moyen puissant de contrôler les transitions de routes.
- Le middleware offre un mécanisme pour intercepter les requêtes, idéal pour l'authentification et les redirections.
- L'internationalisation dans Next.js est simple grâce au routage basé sur la locale.

---

## Exercice Pratique

**Créer un blog avec routage dynamique et internationalisation :**
1. Créez une application Next.js avec la prise en charge de l'i18n.
2. Créez des routes dynamiques pour les articles de blog individuels (`[id].tsx`).
3. Implémentez un middleware qui vérifie la présence d'un cookie "authToken", en redirigeant les utilisateurs s'il n'est pas présent.
4. Ajoutez un sélecteur de langue pour naviguer entre les locales anglaise et française.
