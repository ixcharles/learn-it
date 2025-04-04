
# Tests et Assurance Qualité

Un guide complet pour les tests, le linting, le formatage et la vérification des types dans les projets Next.js avec TypeScript. Apprenez à configurer les tests unitaires et d'intégration, à effectuer des tests de bout en bout et à maintenir la qualité du code grâce au linting et au formatage.

---

## Table des Matières

- [Tests Unitaires et d'Intégration](#tests-unitaires-et-dintégration)
  - [Jest et React Testing Library](#jest-et-react-testing-library)
  - [Typage des Mocks et des Utilitaires de Test](#typage-des-mocks-et-des-utilitaires-de-test)
- [Tests de Bout en Bout](#tests-de-bout-en-bout)
  - [Cypress avec TypeScript](#cypress-avec-typescript)
- [Linting et Formatage](#linting-et-formatage)
  - [Règles ESLint + TypeScript](#eslint-typescript-rules)
  - [Configuration de Prettier](#configuration-de-prettier)
- [Vérification des Types et Prévention des Erreurs](#vérification-des-types-et-prévention-des-erreurs)
  - [Mode Strict dans TypeScript](#mode-strict-dans-typescript)
  - [Éviter les Pièges de Types Courants](#éviter-les-pièges-de-types-courants)

---

## Tests Unitaires et d'Intégration

### Jest et React Testing Library
Jest est un framework de test populaire pour les tests unitaires et d'intégration. React Testing Library simplifie le test des composants React en se concentrant sur le comportement plutôt que sur les détails d'implémentation.

**Exemple:**
```tsx
// src/components/Button.tsx
export function Button({ onClick }: { onClick: () => void }) {
  return <button onClick={onClick}>Cliquez-moi</button>;
}

// src/components/Button.test.tsx
import { render, screen, fireEvent } from '@testing-library/react';
import { Button } from './Button';

test('appelle onClick lors du clic', () => {
  const handleClick = jest.fn();
  render(<Button onClick={handleClick} />);
  fireEvent.click(screen.getByText('Cliquez-moi'));
  expect(handleClick).toHaveBeenCalledTimes(1);
});
```

### Typage des Mocks et des Utilitaires de Test
TypeScript vous permet de typer vos mocks et vos utilitaires de test, assurant ainsi la sécurité des types pendant les tests.

**Exemple:**
```tsx
// Mocker une fonction dans Jest avec TypeScript
const mockFunction = jest.fn().mockReturnValue('Valeur Mockée');
type MockFunctionType = jest.MockedFunction<typeof mockFunction>;

// Utilisation du mock dans un test
test('devrait retourner la valeur mockée', () => {
  const result: string = mockFunction();
  expect(result).toBe('Valeur Mockée');
});
```

---

## Tests de Bout en Bout

### Cypress avec TypeScript
Cypress fournit un moyen facile de configurer des tests de bout en bout pour votre application web, garantissant que tout fonctionne comme prévu dans les flux d'utilisateurs.

**Exemple:**
```tsx
// cypress/integration/home.spec.ts
describe('Page d\'accueil', () => {
  it('devrait afficher le message de bienvenue', () => {
    cy.visit('/');
    cy.contains('Bienvenue sur la Page d\'Accueil');
  });

  it('devrait naviguer vers la page À Propos lors du clic', () => {
    cy.get('a[href="/about"]').click();
    cy.url().should('include', '/about');
    cy.contains('À Propos de Nous');
  });
});
```

**Configuration de Cypress avec TypeScript :**
1. Installez Cypress et les types TypeScript :
   ```bash
   npm install cypress @types/cypress --save-dev
   ```

2. Créez un `tsconfig.json` pour les tests Cypress :
   ```json
   {
     "compilerOptions": {
       "types": ["cypress"]
     }
   }
   ```

---

## Linting et Formatage

### Règles ESLint + TypeScript
ESLint aide à appliquer les normes de codage et à identifier les erreurs potentielles dans votre code. Les règles spécifiques à TypeScript garantissent que votre code TypeScript respecte les meilleures pratiques.

**Exemple:**
```bash
npm install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
```

**.eslintrc.js:**
```js
module.exports = {
  parser: '@typescript-eslint/parser',
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
  ],
  rules: {
    '@typescript-eslint/no-unused-vars': 'warn',
  },
};
```

### Configuration de Prettier
Prettier formate automatiquement votre code pour assurer la cohérence dans tout votre projet. Vous pouvez l'intégrer à ESLint pour un formatage transparent.

**Installer Prettier :**
```bash
npm install --save-dev prettier eslint-plugin-prettier eslint-config-prettier
```

**.prettierrc:**
```json
{
  "singleQuote": true,
  "semi": false,
  "trailingComma": "es5"
}
```

**.eslintrc.js:**
```js
module.exports = {
  extends: [
    'eslint:recommended',
    'plugin:prettier/recommended',
  ],
};
```

---

## Vérification des Types et Prévention des Erreurs

### Mode Strict dans TypeScript
Le mode strict dans TypeScript active des options de vérification de type strictes, garantissant moins d'erreurs d'exécution et un code plus robuste.

**Exemple:**
Activez le mode strict en ajoutant ce qui suit à `tsconfig.json` :
```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

### Éviter les Pièges de Types Courants
Certains pièges courants de TypeScript incluent l'assertion de type, les types `any` implicites et les bibliothèques externes non typées. Les éviter contribue à une meilleure sécurité des types.

**Exemple:**
```tsx
// Éviter : any implicite
function add(a, b) {
  return a + b; // a et b sont implicitement 'any'
}

// Mieux : typage explicite
function add(a: number, b: number): number {
  return a + b;
}
```

**Éviter `any` :**
```tsx
// Éviter le type 'any'
const user: any = { name: 'John' };

// Mieux : utiliser des types explicites
interface User {
  name: string;
}
const user: User = { name: 'John' };
```

---

## Conclusion

**Points Clés à Retenir:**
- Jest et React Testing Library vous permettent de tester les composants React avec des utilitaires type-safe, assurant des tests unitaires et d'intégration robustes.
- Cypress permet des tests de bout en bout, aidant à garantir que votre application fonctionne comme prévu du point de vue de l'utilisateur.
- ESLint et Prettier aident à maintenir la qualité du code en appliquant un style de code cohérent et en détectant les erreurs.
- L'activation du mode strict de TypeScript améliore la sécurité des types, et éviter les pièges courants garantit moins d'erreurs d'exécution.

---

## Exercice Pratique

**Construire une Suite de Tests pour une Application de Blog :**
1. Configurez des tests unitaires et d'intégration pour des composants tels que la liste des articles et le formulaire de création d'article à l'aide de Jest et React Testing Library.
2. Ajoutez des tests de bout en bout pour les flux d'utilisateurs (par exemple, créer, modifier, supprimer des articles) avec Cypress.
3. Intégrez ESLint et Prettier pour le linting et le formatage, et activez le mode strict dans TypeScript pour une meilleure sécurité des types.
