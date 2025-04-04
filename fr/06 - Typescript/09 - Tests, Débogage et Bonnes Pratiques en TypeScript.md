
# Tests, Débogage et Bonnes Pratiques en TypeScript

Ce cours se concentre sur les stratégies pratiques pour tester, déboguer et écrire du code TypeScript maintenable. Il couvre les outils essentiels comme Jest, ESLint et Prettier, ainsi que les meilleures pratiques pour la sécurité des types, la gestion des erreurs et le formatage.

## Table des Matières

1. [Tests Unitaires avec TypeScript (Jest, Mocha)](#unit-testing-with-typescript-jest-mocha)
2. [Vérification des Types TypeScript Pendant le Développement](#typescript-type-checking-during-development)
3. [Débogage du Code TypeScript dans les IDE](#debugging-typescript-code-in-ides)
4. [Écrire du TypeScript avec ESLint et Prettier](#writing-typescript-with-eslint-and-prettier)
5. [Bonnes Pratiques de Linting et de Formatage du Code TypeScript](#typescript-code-linting-and-formatting-best-practices)
6. [Bonnes Pratiques de Gestion des Erreurs en TypeScript](#error-handling-best-practices-in-typescript)

---

## Tests Unitaires avec TypeScript (Jest, Mocha)

Utilisez des lanceurs de tests comme **Jest** ou **Mocha** avec TypeScript pour écrire des tests unitaires et garantir l'exactitude du code.

### Exemple avec Jest :

```bash
npm install --save-dev jest ts-jest @types/jest
npx ts-jest config:init
```

```typescript
// sum.ts
export function sum(a: number, b: number): number {
  return a + b;
}

// sum.test.ts
import { sum } from './sum';

test('adds 1 + 2 = 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

---

## Vérification des Types TypeScript Pendant le Développement

Activez le mode `strict` dans `tsconfig.json` pour une sécurité de type complète et une détection précoce des erreurs.

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true
  }
}
```

Exécutez le compilateur TypeScript avec :

```bash
tsc --noEmit
```

---

## Débogage du Code TypeScript dans les IDE

Les IDE modernes comme **VS Code** offrent de puissants outils de débogage TypeScript avec des cartes de source.

### Configuration du Débogage dans VS Code :

```json
// .vscode/launch.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Debug TS",
      "program": "${workspaceFolder}/src/index.ts",
      "preLaunchTask": "tsc: build - tsconfig.json",
      "outFiles": ["${workspaceFolder}/dist/**/*.js"]
    }
  ]
}
```

Activez les cartes de source dans `tsconfig.json` :

```json
"sourceMap": true
```

---

## Écrire du TypeScript avec ESLint et Prettier

Utilisez **ESLint** pour détecter les problèmes de code et **Prettier** pour le formatage automatique.

### Configuration :

```bash
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin prettier eslint-config-prettier eslint-plugin-prettier
```

### Exemple de `.eslintrc.js` :

```javascript
module.exports = {
  parser: '@typescript-eslint/parser',
  plugins: ['@typescript-eslint', 'prettier'],
  extends: ['plugin:@typescript-eslint/recommended', 'plugin:prettier/recommended'],
};
```

---

## Bonnes Pratiques de Linting et de Formatage du Code TypeScript

- Activez `noImplicitAny`, `strictNullChecks` et `alwaysStrict`.
- Utilisez Prettier pour appliquer un formatage cohérent (par exemple, espacement, points-virgules).
- Configurez des hooks de pré-commit avec **lint-staged** et **husky** pour la qualité du code.

### Exemple :

```json
"lint-staged": {
  "*.ts": ["eslint --fix", "prettier --write"]
}
```

---

## Bonnes Pratiques de Gestion des Erreurs en TypeScript

- Rétrécissez toujours les types d'erreur à l'aide de gardes de type.
- Évitez d'utiliser `any` pour les blocs `catch` — utilisez `unknown` et affinez.
- Utilisez des classes d'erreur personnalisées pour la clarté et la structure.

### Exemple :

```typescript
try {
  throw new Error("Oups !");
} catch (err: unknown) {
  if (err instanceof Error) {
    console.error(err.message);
  }
}
```

---

## Conclusion

### Points Clés à Retenir :
1. Utilisez Jest ou Mocha avec ts-jest pour des tests TypeScript efficaces.
2. Activez la vérification stricte des types pour un code plus sûr et plus prévisible.
3. Déboguez efficacement à l'aide des cartes de source dans les IDE modernes comme VS Code.
4. Utilisez ESLint et Prettier pour appliquer un code cohérent et propre.
5. Gérez les erreurs en utilisant `unknown`, `instanceof` et des types d'erreur personnalisés.

### Exercice Pratique :
1. Créez une fonction simple et écrivez un test unitaire pour celle-ci en utilisant Jest.
2. Activez le mode strict dans votre `tsconfig.json` et refactorisez le code pour vous y conformer.
3. Ajoutez ESLint et Prettier à votre projet et exécutez-les sur un fichier exemple.
4. Écrivez un bloc try/catch en utilisant `unknown` dans la gestion des erreurs et consignez le message en toute sécurité.
