
# Introduction à TypeScript et Configuration

TypeScript est un surensemble de JavaScript à typage statique qui améliore le langage en ajoutant des annotations de type optionnelles, des interfaces et d'autres fonctionnalités qui améliorent l'expérience du développeur et la maintenabilité. Ce cours vous guidera à travers la configuration initiale et la compréhension de base de TypeScript.

## Table des Matières

1. [Qu'est-ce que TypeScript ?](#what-is-typescript)
2. [Installation de TypeScript et Configuration d'un Projet](#installing-typescript-and-setting-up-a-project)
3. [Configuration de TypeScript (tsconfig.json)](#typescript-configuration-tsconfigjson)
4. [Comprendre le Processus de Compilation de TypeScript](#understanding-typescript-compilation-process)
5. [Travailler avec TypeScript dans les Éditeurs (VS Code, etc.)](#working-with-typescript-in-editors-vs-code-etc)
6. [Exécuter du Code TypeScript : tsc vs. ts-node](#running-typescript-code-tsc-vs-ts-node)

---

## Qu'est-ce que TypeScript ?

TypeScript est un surensemble de JavaScript qui ajoute le typage statique, ce qui peut aider à détecter les erreurs pendant le développement. Il est compilé en JavaScript simple qui s'exécute dans n'importe quel environnement JavaScript.

### Exemple :

```typescript
let message: string = "Hello, TypeScript!";
console.log(message);
```

---

## Installation de TypeScript et Configuration d'un Projet

Pour commencer avec TypeScript, vous devez l'installer globalement ou localement en utilisant npm.

### Installation (Globale) :

```bash
npm install -g typescript
```

### Installation (Locale dans le Projet) :

```bash
npm install --save-dev typescript
```

Vous devez également initialiser un nouveau projet en créant un fichier `tsconfig.json` (traité dans la section suivante).

---

## Configuration de TypeScript (tsconfig.json)

Le fichier `tsconfig.json` contient les options du compilateur TypeScript. Il vous aide à configurer la manière dont le code TypeScript est compilé.

### Exemple de `tsconfig.json` :

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist"
  },
  "include": ["src/**/*.ts"]
}
```

- `target`: Spécifie la version de JavaScript vers laquelle compiler.
- `module`: Définit le système de modules.
- `strict`: Active les options strictes de vérification de type.
- `outDir`: Spécifie le répertoire de sortie pour les fichiers JS compilés.
- `include`: Fichiers ou répertoires à inclure dans la compilation.

---

## Comprendre le Processus de Compilation de TypeScript

TypeScript doit être compilé en JavaScript avant d'être exécuté. Ce processus est effectué à l'aide de la commande `tsc` (Compilateur TypeScript).

### Exemple de Commande :

```bash
tsc
```

Cette commande lit le fichier `tsconfig.json` et compile les fichiers TypeScript en JavaScript en fonction de la configuration.

---

## Travailler avec TypeScript dans les Éditeurs (VS Code, etc.)

L'utilisation d'un éditeur comme VS Code avec la prise en charge de TypeScript facilite la complétion de code, le linting et la vérification de type en ligne.

1. Installez VS Code.
2. Installez le plugin TypeScript (bien que VS Code prenne souvent en charge TypeScript par défaut).
3. Ouvrez le dossier du projet TypeScript et commencez à coder !

VS Code offre des fonctionnalités telles qu'IntelliSense et la prise en charge du terminal intégré pour exécuter TypeScript directement.

---

## Exécuter du Code TypeScript : tsc vs. ts-node

- `tsc`: Compile les fichiers TypeScript en JavaScript.
- `ts-node`: Un environnement d'exécution qui exécute directement les fichiers TypeScript sans les compiler au préalable.

### Exemple d'utilisation de `tsc` :

```bash
tsc index.ts
```

Ceci compilera `index.ts` en `index.js`.

### Exemple d'utilisation de `ts-node` :

```bash
npx ts-node index.ts
```

`ts-node` est plus rapide pour le développement car il élimine le besoin de compilation manuelle.

---

## Conclusion

### Points Clés à Retenir :
1. TypeScript est un surensemble de JavaScript à typage statique qui améliore la qualité du code et l'expérience du développeur.
2. Vous pouvez installer TypeScript globalement ou localement dans un projet via npm.
3. Le fichier `tsconfig.json` configure les options de compilation de TypeScript.
4. Le code TypeScript doit être compilé en JavaScript à l'aide de `tsc`, ou exécuté directement avec `ts-node`.
5. Les éditeurs comme VS Code offrent des fonctionnalités telles qu'IntelliSense pour un développement TypeScript efficace.

### Exercice Pratique :
1. Installez TypeScript localement dans un projet.
2. Créez un fichier `tsconfig.json` avec les paramètres par défaut.
3. Écrivez un simple fichier TypeScript qui consigne une chaîne de caractères et compilez-le à l'aide de `tsc` et exécutez-le avec `ts-node`.
