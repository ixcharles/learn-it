
# Introduction à React Native Expo et TypeScript

React Native avec Expo et TypeScript est une combinaison puissante pour construire des applications mobiles évolutives et performantes en utilisant une pile de développement moderne et à typage statique. Ce cours présente les outils et les pratiques de base nécessaires pour démarrer efficacement.

## Table des matières
- [Aperçu de React Native et Expo](#aperçu-de-react-native-et-expo)
- [Configuration de l'environnement de développement](#configuration-de-lenvironnement-de-développement)
- [Comprendre les fondamentaux de TypeScript](#comprendre-les-fondamentaux-de-typescript)
- [Création d'un nouveau projet Expo avec TypeScript](#création-dun-nouveau-projet-expo-avec-typescript)
- [Structure des répertoires et meilleures pratiques](#structure-des-répertoires-et-meilleures-pratiques)

---

## Aperçu de React Native et Expo

**Définition :**
React Native est un framework pour construire des applications natives en utilisant React. Expo est un flux de travail géré qui simplifie le développement React Native avec un ensemble d'outils et de services.

**Exemple :**
With Expo, you can write one codebase in React and TypeScript and deploy it to iOS and Android instantly.

```bash
npx create-expo-app MyApp
```

Expo fournit un développement rapide, des mises à jour OTA (over-the-air) et un accès aux API de l'appareil sans configuration de code natif.

---

## Configuration de l'environnement de développement

**Définition :**
Pour développer avec Expo et TypeScript, vous avez besoin de Node.js, Expo CLI et d'un éditeur de code comme VS Code.

**Exemple :**

```bash
npm install -g expo-cli
npx create-expo-app MyApp -t
cd MyApp
npm start
```

Utilisez un simulateur mobile ou l'application Expo Go sur votre téléphone pour prévisualiser instantanément votre application.

---

## Comprendre les fondamentaux de TypeScript

**Définition :**
TypeScript est un surensemble typé de JavaScript qui permet la vérification statique des types et de meilleurs outils.

**Exemple :**

```ts
type User = {
  name: string;
  age: number;
};

const greet = (user: User): string => `Hello, ${user.name}`;
```

TypeScript améliore la sécurité du code et la productivité des développeurs dans les projets React Native.

---

## Création d'un nouveau projet Expo avec TypeScript

**Définition :**
Expo prend en charge TypeScript nativement avec l'indicateur `-t` lors de l'initialisation d'un nouveau projet.

**Exemple :**

```bash
npx create-expo-app MyApp -t
```

Cela configure TypeScript avec un fichier `tsconfig.json` et des points d'entrée `.tsx` prêts à l'emploi.

---

## Structure des répertoires et meilleures pratiques

**Définition :**
L'organisation de la structure de votre projet favorise la maintenabilité et l'évolutivité.

**Exemple :**

```
MyApp/
├── assets/         # Images, fonts, etc.
├── components/     # Reusable UI components
├── screens/        # Navigation screens
├── types/          # Global TypeScript types
├── utils/          # Helpers and utility functions
├── App.tsx         # Entry point
└── tsconfig.json   # TypeScript configuration
```

Suivez des structures de dossiers modulaires et maintenez les préoccupations séparées par domaine ou fonctionnalité.

---

## Conclusion

**Points clés à retenir :**
1. React Native + Expo simplifie le développement d'applications multiplateformes.
2. TypeScript applique un typage fort et réduit les erreurs d'exécution.
3. Expo CLI fournit une configuration instantanée avec la prise en charge intégrée de TypeScript.
4. Une structure de répertoire bien organisée améliore l'évolutivité du projet.
5. Expo Go permet une itération et des tests rapides sur de vrais appareils.

**Exercice pratique :**
- Set up a new Expo project with TypeScript.
- Create a `UserCard` component in the `components/` folder using a typed `User` prop.
- Display a sample user on the screen using a `HomeScreen` in the `screens/` folder.
