
# Authentification et Autorisation

Apprenez à implémenter l'authentification et l'autorisation dans votre application Next.js en utilisant TypeScript. Explorez NextAuth.js, le contrôle d'accès basé sur les rôles et la sécurisation des routes et des points de terminaison API.

---

## Table des Matières

- [NextAuth.js avec TypeScript](#nextauthjs-avec-typescript)
  - [Configuration et Fournisseurs](#configuration-et-fournisseurs)
  - [Typage des Objets Session et Utilisateur](#typage-des-objets-session-et-utilisateur)
- [Contrôle d'Accès Basé sur les Rôles](#contrôle-daccès-basé-sur-les-rôles)
  - [Gardes et Middleware Typés](#gardes-et-middleware-typés)
- [Protection des Routes et des Points de Terminaison API](#protection-des-routes-et-des-points-de-terminaison-api)
  - [Rendu Conditionnel avec les Types](#rendu-conditionnel-avec-les-types)
  - [Hook Personnalisé pour le Contexte d'Authentification](#hook-personnalisé-pour-le-contexte-dauthentification)

---

## NextAuth.js avec TypeScript

### Configuration et Fournisseurs
NextAuth.js s'intègre facilement dans Next.js pour l'authentification avec plusieurs fournisseurs comme Google, GitHub et plus encore. La prise en charge de TypeScript assure une authentification type-safe.

**Exemple:**
```tsx
// pages/api/auth/[...nextauth].ts
import NextAuth from 'next-auth';
import GoogleProvider from 'next-auth/providers/google';

export default NextAuth({
  providers: [
    GoogleProvider({
      clientId: process.env.GOOGLE_CLIENT_ID!,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
    }),
  ],
});
```

### Typage des Objets Session et Utilisateur
TypeScript vous permet de typer les objets session et utilisateur retournés par NextAuth, assurant ainsi la sécurité des types.

**Exemple:**
```tsx
// lib/nextAuth.d.ts
import { DefaultSession } from 'next-auth';

declare module 'next-auth' {
  interface Session {
    user: {
      id: string;
      name: string;
      email: string;
    };
  }
}

// Utilisation
import { useSession } from 'next-auth/react';

const Profile = () => {
  const { data: session } = useSession();
  if (session) {
    return <div>Bienvenue, {session.user.name}</div>;
  }
  return <div>Non authentifié</div>;
};
```

---

## Contrôle d'Accès Basé sur les Rôles

### Gardes et Middleware Typés
Le contrôle d'accès basé sur les rôles (RBAC) implique de restreindre l'accès aux routes et aux ressources en fonction des rôles des utilisateurs. Les gardes et les middleware typés aident à appliquer cela de manière sécurisée.

**Exemple:**
```tsx
// lib/guards.ts
export function withRole(role: string) {
  return (req: any, res: any, next: any) => {
    if (req.user.role !== role) {
      return res.status(403).json({ error: 'Accès refusé' });
    }
    next();
  };
}

// Utilisation dans une route API
import { withRole } from '../../lib/guards';

export default function handler(req, res) {
  withRole('admin')(req, res, () => {
    res.status(200).json({ message: 'Accès autorisé' });
  });
}
```

---

## Protection des Routes et des Points de Terminaison API

### Rendu Conditionnel avec les Types
En TypeScript, le rendu conditionnel basé sur l'état d'authentification peut être effectué en toute sécurité, offrant une expérience utilisateur fluide tout en sécurisant certaines parties de votre application.

**Exemple:**
```tsx
import { useSession } from 'next-auth/react';

const ProtectedPage = () => {
  const { data: session } = useSession();

  if (!session) {
    return <div>Veuillez vous connecter pour accéder à cette page</div>;
  }

  return <div>Bienvenue, {session.user.name}</div>;
};
```

### Hook Personnalisé pour le Contexte d'Authentification
Un hook personnalisé pour le contexte d'authentification vous permet de gérer l'état de l'utilisateur dans toute votre application, rendant les vérifications d'authentification plus faciles et plus cohérentes.

**Exemple:**
```tsx
// lib/useAuth.ts
import { useSession } from 'next-auth/react';

export function useAuth() {
  const { data: session, status } = useSession();
  const isAuthenticated = status === 'authenticated';

  return { session, isAuthenticated };
}

// Utilisation dans un composant
import { useAuth } from '../lib/useAuth';

const ProtectedPage = () => {
  const { session, isAuthenticated } = useAuth();

  if (!isAuthenticated) {
    return <div>Veuillez vous connecter</div>;
  }

  return <div>Bienvenue, {session?.user?.name}</div>;
};
```

---

## Conclusion

**Points Clés à Retenir:**
- NextAuth.js simplifie l'authentification avec la prise en charge de TypeScript et de multiples fournisseurs comme Google, GitHub et plus encore.
- Le typage des objets session et utilisateur assure un accès sûr et prévisible aux données d'authentification.
- Le contrôle d'accès basé sur les rôles (RBAC) vous permet de définir des gardes et des middleware pour une gestion sécurisée des ressources.
- La protection des routes et des points de terminaison API de manière type-safe avec le rendu conditionnel ou des hooks personnalisés rend votre application plus sécurisée et maintenable.

---

## Exercice Pratique

**Construire une Application de Blog Authentifiée :**
1. Configurez NextAuth.js avec l'authentification Google et TypeScript.
2. Créez des routes protégées auxquelles seuls les utilisateurs authentifiés peuvent accéder.
3. Implémentez un contrôle d'accès basé sur les rôles pour les fonctionnalités d'administrateur (par exemple, créer, supprimer des articles).
4. Utilisez un hook personnalisé pour gérer l'état d'authentification dans toute l'application.
