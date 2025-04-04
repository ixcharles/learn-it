
# Tests Cypress Avancés et Intégration CI

Ce cours couvre les fonctionnalités avancées de Cypress, y compris les tests de composants, la prise en charge multi-navigateurs, la performance, l'intégration CI/CD et les pratiques de test évolutives pour les applications modernes.

---

## Table des Matières

- [Tests de Composants avec Cypress](#tests-de-composants-avec-cypress)
- [Parallélisation et Répartition de Charge dans les Exécutions de Tests](#parallelisation-et-repartition-de-charge-dans-les-executions-de-tests)
- [Gérer le Contenu Instable et Dynamique](#gerer-le-contenu-instable-et-dynamique)
- [Tester la Performance et l'Accessibilité dans Cypress](#tester-la-performance-et-laccessibilite-dans-cypress)
- [Tests Multi-Navigateurs et Mobiles](#tests-multi-navigateurs-et-mobiles)
- [Intégrer Cypress dans les Pipelines CI/CD](#integrer-cypress-dans-les-pipelines-cicd)
- [Écrire des Suites de Tests Cypress Évolutives](#ecrire-des-suites-de-tests-cypress-evolutives)
- [Configuration de l'Environnement et Gestion des Secrets](#configuration-de-lenvironnement-et-gestion-des-secrets)
- [Plugins Cypress et Extension des Fonctionnalités](#plugins-cypress-et-extension-des-fonctionnalites)
- [Migration des Tests Entre Frameworks (Jest ⇄ Cypress)](#migration-des-tests-entre-frameworks-jest-cypress)
- [Conclusion](#conclusion)

---

## Tests de Composants avec Cypress

**Définition** : Testez des composants React individuels de manière isolée en utilisant le mode de test de composants de Cypress.

**Exemple** :
```js
import MyComponent from './MyComponent';
describe('MyComponent', () => {
  it('renders correctly', () => {
    cy.mount(<MyComponent />);
    cy.contains('Hello').should('exist');
  });
});
```

---

## Parallélisation et Répartition de Charge dans les Exécutions de Tests

**Définition** : Divisez l'exécution des tests sur plusieurs machines pour réduire le temps d'exécution total en utilisant le Cypress Dashboard.

**Exemple** :
```bash
npx cypress run --record --parallel --group e2e-tests
```

Assurez-vous que votre projet est configuré avec `cypress.json` et un `projectId`.

---

## Gérer le Contenu Instable et Dynamique

**Définition** : Gérez les incohérences de timing et le contenu non déterministe avec des tentatives et des attentes appropriées.

**Bonnes Pratiques** :
- Évitez les `wait()` statiques, préférez `cy.wait('@alias')`.
- Utilisez `should()` et la capacité de réessai.

**Exemple** :
```js
cy.get('.alert').should('contain.text', 'Success');
```

---

## Tester la Performance et l'Accessibilité dans Cypress

**Définition** : Utilisez des plugins pour exécuter des audits d'accessibilité et de performance (par exemple, Lighthouse, Axe).

**Exemple** :
```js
import 'cypress-axe';
cy.injectAxe();
cy.checkA11y();
```

Test de performance utilisant `cypress-audit` :
```bash
npx cypress run --spec 'performance.cy.js'
```

---

## Tests Multi-Navigateurs et Mobiles

**Définition** : Exécutez les tests dans plusieurs navigateurs et viewports.

**Exemple** :
```bash
npx cypress run --browser chrome
```

Définir le viewport :
```js
cy.viewport('iphone-6');
cy.visit('/');
```

---

## Intégrer Cypress dans les Pipelines CI/CD

**Définition** : Exécutez les tests en mode headless dans les outils CI comme GitHub Actions, GitLab CI, CircleCI, etc.

**Exemple GitHub Actions** :
```yaml
- name: Exécuter les tests Cypress
  uses: cypress-io/github-action@v4
  with:
    record: true
    start: npm start
    wait-on: 'http://localhost:3000'
```

---

## Écrire des Suites de Tests Cypress Évolutives

**Définition** : Organisez les cas de test de manière modulaire, regroupez par domaine ou flux utilisateur.

**Bonnes Pratiques** :
- Réutilisez les commandes personnalisées.
- Modularisez les sélecteurs et les constantes.

**Exemple** :
```
/cypress/
  /e2e/
    login.cy.js
    dashboard.cy.js
  /support/
    commands.js
    selectors.js
```

---

## Configuration de l'Environnement et Gestion des Secrets

**Définition** : Utilisez `cypress.config.js` ou les variables d'environnement pour gérer les secrets et les configurations.

**Exemple** :
```js
// cypress.config.js
env: {
  apiUrl: 'https://api.example.com',
  username: process.env.USERNAME,
}
```

Utilisation dans le test :
```js
cy.request(`${Cypress.env('apiUrl')}/users`);
```

---

## Plugins Cypress et Extension des Fonctionnalités

**Définition** : Étendez Cypress via des plugins (téléchargement de fichiers, comparaisons visuelles, etc.)

**Exemple** :
```js
// cypress/plugins/index.js
const injectDevServer = require('@cypress/react/plugins/react-scripts');
module.exports = (on, config) => {
  injectDevServer(on, config);
  return config;
};
```

Plugins populaires :
- `cypress-axe`
- `cypress-audit`
- `cypress-file-upload`

---

## Migration des Tests Entre Frameworks (Jest ⇄ Cypress)

**Définition** : Adaptez les tests unitaires/d'intégration aux tests de composants Cypress ou vice versa.

**Stratégies** :
- Extrayez la logique partagée dans des utilitaires de test.
- Utilisez `mount()` dans Cypress comme alternative à `render()` dans Jest.
- Traduisez `userEvent` → `cy.get().type()` / `click()`.

**Exemple** :
Jest :
```js
render(<Login />);
userEvent.click(screen.getByText('Submit'));
```

Cypress :
```js
cy.mount(<Login />);
cy.contains('Submit').click();
```

---

## Conclusion

**Points Clés à Retenir** :
1. Cypress prend en charge les tests E2E complets et les tests de composants avec de puissants outils de débogage.
2. Intégrez dans les pipelines CI/CD avec parallélisation pour la vitesse.
3. Améliorez la qualité des tests avec les plugins d'accessibilité et de performance.
4. Organisez et faites évoluer votre architecture de test pour les grands projets.
5. Utilisez les variables d'environnement et les plugins pour maintenir la flexibilité et la sécurité.

**Exercice Pratique** :
- Configurer un pipeline CI qui :
  - Exécute les tests Cypress en parallèle.
  - Inclut une vérification d'accessibilité en utilisant `cypress-axe`.
  - Utilise des variables d'environnement pour les tokens d'authentification.
