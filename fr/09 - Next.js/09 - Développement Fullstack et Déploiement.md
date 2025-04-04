
# Développement Fullstack et Déploiement

Ce guide couvre la création d'applications fullstack à l'aide de Next.js et TypeScript, la gestion des webhooks et des tâches de fond, la configuration des variables d'environnement et la mise en place de pipelines de déploiement pour un flux de développement à production sans heurt.

---

## Table des Matières

- [Création d'Applications Fullstack](#création-dapplications-fullstack)
  - [Combiner les Routes API avec l'UI](#combiner-les-routes-api-avec-lui)
  - [Flux End-to-End Type-Safe](#flux-end-to-end-type-safe)
- [Webhooks et Tâches de Fond](#webhooks-et-tâches-de-fond)
  - [Réception et Validation des Webhooks](#réception-et-validation-des-webhooks)
  - [Fonctions Serverless avec TypeScript](#fonctions-serverless-avec-typescript)
- [Variables d'Environnement et Configuration](#variables-denvironnement-et-configuration)
  - [Utiliser `process.env` en Toute Sécurité](#utiliser-processenv-en-toute-sécurité)
  - [Typer les Variables d'Environnement](#typer-les-variables-denvironnement)
- [Pipelines de Déploiement](#pipelines-de-déploiement)
  - [Déploiement Vercel avec TypeScript](#déploiement-vercel-avec-typescript)
  - [Intégration CI/CD](#intégration-cicd)

---

## Création d'Applications Fullstack

### Combiner les Routes API avec l'UI
Next.js vous permet de créer des applications fullstack en combinant les routes API et l'interface utilisateur frontend dans le même projet. Cette configuration vous permet de récupérer des données directement à partir des routes API et de les afficher dans vos composants React.

**Exemple:**
```tsx
// pages/api/posts.ts
export default async function handler(req, res) {
  const posts = await fetchPostsFromDatabase();
  res.status(200).json(posts);
}

// pages/index.tsx
import { useEffect, useState } from 'react';

const HomePage = () => {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    async function fetchPosts() {
      const response = await fetch('/api/posts');
      const data = await response.json();
      setPosts(data);
    }
    fetchPosts();
  }, []);

  return (
    <div>
      <h1>Articles</h1>
      {posts.map(post => (
        <div key={post.id}>{post.title}</div>
      ))}
    </div>
  );
};
```

### Flux End-to-End Type-Safe
La sécurité des types garantit l'exactitude des données transmises entre votre interface utilisateur et vos routes API, réduisant ainsi les bugs et améliorant l'expérience développeur. Vous pouvez définir des types pour les réponses API et vous assurer que les composants de l'interface utilisateur fonctionnent avec les structures de données correctes.

**Exemple:**
```tsx
// types.ts
export interface Post {
  id: string;
  title: string;
  content: string;
}

// pages/api/posts.ts
import { NextApiRequest, NextApiResponse } from 'next';
import { Post } from '../../types';

export default async function handler(req: NextApiRequest, res: NextApiResponse<Post[]>) {
  const posts = await fetchPostsFromDatabase();
  res.status(200).json(posts);
}

// pages/index.tsx
import { Post } from '../types';

const HomePage = () => {
  const [posts, setPosts] = useState<Post[]>([]);

  useEffect(() => {
    async function fetchPosts() {
      const response = await fetch('/api/posts');
      const data: Post[] = await response.json();
      setPosts(data);
    }
    fetchPosts();
  }, []);

  return (
    <div>
      <h1>Articles</h1>
      {posts.map(post => (
        <div key={post.id}>{post.title}</div>
      ))}
    </div>
  );
};
```

---

## Webhooks et Tâches de Fond

### Réception et Validation des Webhooks
Les webhooks vous permettent de recevoir des notifications de services externes. Vous pouvez utiliser les routes API pour gérer et valider les données de webhook entrantes.

**Exemple:**
```tsx
// pages/api/webhook.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  if (req.method === 'POST') {
    const signature = req.headers['x-signature'];
    const isValid = validateWebhookSignature(signature, req.body);
    if (!isValid) {
      return res.status(400).json({ error: 'Signature invalide' });
    }

    const data = req.body;
    // Traiter les données du webhook...
    return res.status(200).json({ message: 'Webhook reçu avec succès' });
  }

  res.status(405).json({ error: 'Méthode non autorisée' });
}

function validateWebhookSignature(signature: string, payload: any): boolean {
  // Logique de validation de la signature...
  return true;
}
```

### Fonctions Serverless avec TypeScript
Les fonctions serverless dans Next.js peuvent être écrites avec TypeScript, vous permettant de gérer la logique backend de manière évolutive sans gérer l'infrastructure serveur.

**Exemple:**
```tsx
// pages/api/send-email.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  const { email, message } = req.body;

  try {
    // Logique d'envoi d'e-mail...
    return res.status(200).json({ message: 'E-mail envoyé avec succès' });
  } catch (error) {
    return res.status(500).json({ error: 'Erreur lors de l'envoi de l'e-mail' });
  }
}
```

---

## Variables d'Environnement et Configuration

### Utiliser `process.env` en Toute Sécurité
Dans Next.js, vous pouvez utiliser des variables d'environnement pour stocker des informations sensibles, telles que des clés API. Assurez-vous d'y accéder en toute sécurité et de n'exposer que les variables nécessaires côté client.

**Exemple:**
```tsx
// .env.local
NEXT_PUBLIC_API_URL=https://api.example.com
SECRET_API_KEY=votre-clé-secrète

// pages/api/data.ts
export default async function handler(req, res) {
  const apiUrl = process.env.NEXT_PUBLIC_API_URL;
  const apiKey = process.env.SECRET_API_KEY;

  const response = await fetch(`${apiUrl}/data?apiKey=${apiKey}`);
  const data = await response.json();
  res.status(200).json(data);
}
```

### Typer les Variables d'Environnement
TypeScript prend en charge les variables d'environnement type-safe en déclarant des types pour `process.env` afin d'éviter les erreurs causées par des valeurs manquantes ou mal formées.

**Exemple:**
```tsx
// env.d.ts
declare global {
  namespace NodeJS {
    interface ProcessEnv {
      NEXT_PUBLIC_API_URL: string;
      SECRET_API_KEY: string;
    }
  }
}
```

---

## Pipelines de Déploiement

### Déploiement Vercel avec TypeScript
Vercel est la plateforme recommandée pour le déploiement des applications Next.js. Elle offre une prise en charge intégrée de TypeScript, vous permettant de déployer votre projet de manière transparente.

**Exemple:**
1. Poussez votre projet sur GitHub, GitLab ou Bitbucket.
2. Connectez votre dépôt à Vercel via le tableau de bord Vercel.
3. Vercel détecte automatiquement le framework Next.js et déploie votre application, y compris les fichiers TypeScript.

Aucune configuration n'est nécessaire pour le déploiement TypeScript sur Vercel, car cela fonctionne immédiatement.

### Intégration CI/CD
Intégrez des pipelines d'intégration continue et de déploiement continu (CI/CD) à l'aide de GitHub Actions, GitLab CI ou d'outils similaires pour automatiser les tests, la construction et le déploiement de votre application Next.js.

**Exemple (GitHub Actions):**
```yaml
name: Déployer Next.js sur Vercel

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Vérifier le code
        uses: actions/checkout@v2

      - name: Installer les dépendances
        run: npm install

      - name: Exécuter la construction
        run: npm run build

      - name: Déployer sur Vercel
        run: vercel --prod --token ${{ secrets.VERCEL_TOKEN }}
```

---

## Conclusion

**Points Clés à Retenir:**
- Les applications fullstack dans Next.js combinent les routes API avec l'UI, vous permettant de créer des applications dynamiques avec la prise en charge de TypeScript.
- Les webhooks peuvent être gérés dans Next.js à l'aide des routes API, et les tâches de fond peuvent être gérées avec des fonctions serverless.
- Gérez en toute sécurité les variables d'environnement à l'aide de `process.env` et assurez la sécurité des types en déclarant des types pour ces variables.
- Déployez facilement votre application Next.js sur Vercel et intégrez des pipelines CI/CD pour les déploiements et tests automatisés.

---

## Exercice Pratique

**Créer une Application de Blog Fullstack :**
1. Créez un blog simple où les utilisateurs peuvent récupérer des articles à partir d'une route API et soumettre des commentaires via un formulaire.
2. Implémentez un webhook pour recevoir des notifications lorsqu'un nouvel article est publié.
3. Utilisez TypeScript pour gérer les variables d'environnement pour la configuration du blog (par exemple, URL de l'API, clés secrètes).
4. Configurez CI/CD à l'aide de GitHub Actions pour les déploiements automatiques sur Vercel.
