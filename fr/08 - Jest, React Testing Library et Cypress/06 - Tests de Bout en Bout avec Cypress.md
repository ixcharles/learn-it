
# Tests de Bout en Bout avec Cypress

Ce cours présente Cypress pour les tests de bout en bout (E2E), permettant une interaction et une validation complètes du comportement réel du navigateur dans les applications web modernes.

---

## Table des Matières

- [Installation et Configuration de Cypress](#installation-et-configuration-de-cypress)
- [Structure des Dossiers Cypress et Utilisation de la CLI](#structure-des-dossiers-cypress-et-utilisation-de-la-cli)
- [Écrire Votre Premier Test E2E](#ecrire-votre-premier-test-e2e)
- [Interagir avec le DOM et Simuler le Comportement de l'Utilisateur](#interagir-avec-le-dom-et-simuler-le-comportement-de-lutilisateur)
- [Assertions et Chaînage de Commandes](#assertions-et-chainage-de-commandes)
- [Travailler avec les Fixtures, les Alias et les Commandes Personnalisées](#travailler-avec-les-fixtures-les-alias-et-les-commandes-personnalisees)
- [Requêtes Réseau et Interception d'API (`cy.intercept`)](#requetes-reseau-et-interception-dapi-cyintercept)
- [Captures d'Écran, Vidéos et Rapports de Tests](#captures-decran-videos-et-rapports-de-tests)
- [Gérer les Routes Authentifiées et les Sessions](#gerer-les-routes-authentifiees-et-les-sessions)
- [Déboguer les Tests Cypress](#debugger-les-tests-cypress)
- [Conclusion](#conclusion)

---

## Installation et Configuration de Cypress

**Définition** : Cypress est installé comme une dépendance de développement et initialisé avec une simple commande CLI.

**Exemple** :
```bash
npm install cypress --save-dev
npx cypress open
```

---

## Structure des Dossiers Cypress et Utilisation de la CLI

**Définition** : Cypress utilise une structure de dossiers organisée pour ranger les tests, les fixtures et les fichiers de support.

**Exemple** :
```
cypress/
  e2e/         → fichiers de spécification des tests
  fixtures/    → données de test statiques
  support/     → commandes personnalisées et configuration
```

Exécuter les tests :
```bash
npx cypress run
```

---

## Écrire Votre Premier Test E2E

**Définition** : Les tests Cypress suivent la syntaxe Mocha et s'exécutent directement dans le navigateur.

**Exemple** :
```js
describe('Page d\'accueil', () => {
  it('se charge correctement', () => {
    cy.visit('/');
    cy.contains('Welcome').should('be.visible');
  });
});
```

---

## Interagir avec le DOM et Simuler le Comportement de l'Utilisateur

**Définition** : Cypress fournit des commandes pour simuler les interactions réelles de l'utilisateur.

**Exemple** :
```js
cy.get('input[name="email"]').type('user@example.com');
cy.get('button[type="submit"]').click();
```

---

## Assertions et Chaînage de Commandes

**Définition** : Cypress utilise `should()` et `expect()` pour les assertions, souvent chaînées après les actions.

**Exemple** :
```js
cy.get('.alert').should('contain.text', 'Success');
```

Exemple de chaînage :
```js
cy.get('input').type('hello').should('have.value', 'hello');
```

---

## Travailler avec les Fixtures, les Alias et les Commandes Personnalisées

**Définition** : Les fixtures sont des fichiers statiques utilisés pour le mocking ; les alias aident à réutiliser les éléments ; les commandes étendent Cypress.

**Exemple** :
```js
cy.fixture('user.json').as('userData');
cy.get('@userData').then(user => {
  cy.get('input[name="email"]').type(user.email);
});
```

Commande personnalisée :
```js
Cypress.Commands.add('login', (email, password) => {
  cy.get('#email').type(email);
  cy.get('#password').type(password);
  cy.get('button[type="submit"]').click();
});
```

---

## Requêtes Réseau et Interception d'API (`cy.intercept`)

**Définition** : Interceptez et moquez les requêtes HTTP pour contrôler les réponses du backend dans les tests.

**Exemple** :
```js
cy.intercept('GET', '/api/user', { fixture: 'user.json' }).as('getUser');
cy.visit('/');
cy.wait('@getUser');
```

---

## Captures d'Écran, Vidéos et Rapports de Tests

**Définition** : Cypress peut capturer des artefacts pour aider au débogage et à la création de rapports.

**Exemple** :
```bash
npx cypress run --record
```

Dans les tests :
```js
cy.screenshot();
cy.screenshot('custom-name');
```

Rapports configurés via des plugins comme `mochawesome`.

---

## Gérer les Routes Authentifiées et les Sessions

**Définition** : Vous pouvez automatiser les flux de connexion ou définir les cookies/tokens de session de manière programmatique.

**Exemple** :
```js
cy.setCookie('auth_token', 'abc123');
cy.visit('/dashboard');
```

Ou utiliser la connexion API :
```js
cy.request('POST', '/api/login', { username, password })
  .then((resp) => cy.setCookie('auth_token', resp.body.token));
```

---

## Déboguer les Tests Cypress

**Définition** : Utilisez `.debug()`, `cy.pause()` et les outils de développement du navigateur pour inspecter l'état des tests.

**Exemple** :
```js
cy.get('button').debug();
cy.pause();
```

Consultez les logs dans l'exécuteur Cypress pour un retour d'information en temps réel.

---

## Conclusion

**Points Clés à Retenir** :
1. Cypress permet des tests E2E complets basés sur le navigateur avec une configuration minimale.
2. Utilisez `cy.get`, `.type`, `.click` et `.should` pour des tests clairs et lisibles.
3. Interceptez et moquez les requêtes réseau en utilisant `cy.intercept`.
4. Utilisez les fixtures, les alias et les commandes personnalisées pour des tests plus propres.
5. Déboguez visuellement avec des captures d'écran, des vidéos et `cy.pause()`.

**Exercice Pratique** :
- Créer un test de connexion qui :
  - Intercepte l'API de connexion.
  - Saisit des informations dans les champs du formulaire.
  - Clique sur soumettre et affirme le succès.
  - Utilise une fixture pour les données utilisateur.
