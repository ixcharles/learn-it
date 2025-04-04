
# Fondations des Tests en JavaScript et React

Tester est essentiel pour construire des applications fiables, maintenables et évolutives. Ce cours introduit les fondamentaux des tests en JavaScript et React, jetant les bases pour des tests unitaires, d'intégration et de bout en bout (E2E) efficaces.

---

## Table des Matières

- [Introduction aux Tests : Importance et Types](#introduction-aux-tests-importance-et-types)
- [Aperçu des Tests Unitaires, d'Intégration et E2E](#apercu-des-tests-unitaires-dintegration-et-e2e)
- [Stratégies de Test et Bonnes Pratiques](#strategies-de-test-et-bonnes-pratiques)
- [Introduction à Jest](#introduction-a-jest)
- [Introduction à React Testing Library](#introduction-a-react-testing-library)
- [Introduction à Cypress](#introduction-a-cypress)
- [Conclusion](#conclusion)

---

## Introduction aux Tests : Importance et Types

**Définition** : Tester assure la correction du code et prévient les régressions en vérifiant automatiquement que la fonctionnalité fonctionne comme prévu.

**Types de Tests** :
- **Tests unitaires** : Testent de petites parties comme des fonctions/composants.
- **Tests d'intégration** : Testent les interactions entre les unités.
- **Tests E2E** : Simulent le comportement réel de l'utilisateur à travers toute l'application.

**Exemple** :
```js
// Simple unit test
function add(a, b) { return a + b; }
test('adds two numbers', () => {
  expect(add(2, 3)).toBe(5);
});
```

---

## Aperçu des Tests Unitaires, d'Intégration et E2E

**Tests Unitaires** : Vérifient une seule unité de manière isolée.
**Tests d'Intégration** : Valident l'interaction entre les composants/modules.
**Tests E2E** : Testent le flux complet, de l'entrée utilisateur à la sortie finale dans un environnement réel.

**Exemple** :
- Unitaire : Tester un seul composant React.
- Intégration : Tester un formulaire avec plusieurs entrées et une logique de validation.
- E2E : Remplir et soumettre le formulaire dans le navigateur en utilisant Cypress.

---

## Stratégies de Test et Bonnes Pratiques

**Définition** : La stratégie de test définit les types, les outils et la structure des tests pour assurer la qualité avec efficacité.

**Bonnes Pratiques** :
- Privilégier les tests unitaires pour les composants à forte logique.
- Utiliser les tests d'intégration pour le comportement entre les composants.
- Tests E2E pour les parcours utilisateurs — en écrire moins, mais plus critiques.
- Suivre la **Pyramide de Test** : Plus d'unitaires, moins d'E2E.

**Exemple** :
```
          /\
         /  \    E2E (peu)
        /----\
       /      \  Intégration
      /--------\
     /          \ Unitaire (beaucoup)
```

---

## Introduction à Jest

**Définition** : Jest est un framework de test JavaScript utilisé pour les tests unitaires et d'intégration avec une configuration nulle.

**Fonctionnalités** :
- Assertions intégrées, mocking et snapshots.
- Exécution des tests rapide et parallèle.

**Exemple** :
```js
describe('Math utils', () => {
  it('returns correct sum', () => {
    expect(1 + 2).toBe(3);
  });
});
```

---

## Introduction à React Testing Library

**Définition** : React Testing Library (RTL) teste les composants React en simulant la manière dont les utilisateurs interagissent avec l'UI.

**Philosophie** : Tester le comportement plutôt que les détails d'implémentation.

**Exemple** :
```js
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Button from './Button';

test('calls click handler', async () => {
  const handleClick = jest.fn();
  render(<Button onClick={handleClick}>Click me</Button>);
  await userEvent.click(screen.getByText('Click me'));
  expect(handleClick).toHaveBeenCalled();
});
```

---

## Introduction à Cypress

**Définition** : Cypress est un framework tout-en-un rapide pour écrire des tests E2E dans le navigateur.

**Fonctionnalités** :
- S'exécute dans un environnement de navigateur réel.
- Fournit des attentes automatiques, le voyage dans le temps et le débogage UI.

**Exemple** :
```js
describe('Login Flow', () => {
  it('logs in successfully', () => {
    cy.visit('/login');
    cy.get('input[name="username"]').type('user');
    cy.get('input[name="password"]').type('pass');
    cy.get('button[type="submit"]').click();
    cy.contains('Welcome').should('be.visible');
  });
});
```

---

## Conclusion

**Points Clés à Retenir** :
1. Tester est essentiel pour assurer la qualité et la confiance du logiciel.
2. Les tests unitaires, d'intégration et E2E servent des objectifs différents — utilisez-les ensemble.
3. Jest est idéal pour les tests unitaires/d'intégration avec d'excellentes performances et fonctionnalités.
4. React Testing Library encourage le test de l'UI à travers les interactions utilisateur.
5. Cypress est l'outil de référence pour des tests E2E fiables basés sur le navigateur.

**Exercice Pratique** :
- Mettre en place un projet React simple.
- Écrire un test unitaire Jest pour une fonction utilitaire.
- Écrire un test RTL pour un clic de bouton.
- Écrire un test Cypress qui simule la soumission d'un formulaire de connexion.
