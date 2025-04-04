
# Maîtriser Jest pour les Tests Unitaires et d'Intégration

Jest est un framework de test puissant et flexible largement utilisé dans les applications React. Ce cours couvre les fonctionnalités de base et avancées de Jest pour écrire des tests unitaires et d'intégration efficaces.

---

## Table des Matières

- [Configuration de Jest dans un Projet React](#configuration-de-jest-dans-un-projet-react)
- [Structure des Fichiers de Test et Conventions de Nommage](#structure-des-fichiers-de-test-et-conventions-de-nommage)
- [Comprendre les Blocs `describe`, `it` et `test`](#comprendre-les-blocs-describe-it-et-test)
- [Matchers et Assertions (`expect`)](#matchers-et-assertions-expect)
- [Mocks, Espions et Mocks Manuels](#mocks-espions-et-mocks-manuels)
- [Mocker les Modules et les Dépendances](#mocker-les-modules-et-les-dependances)
- [Gérer les Tests Asynchrones avec les Promesses et async/await](#gerer-les-tests-asynchrones-avec-les-promesses-et-asyncawait)
- [Tests de Snapshot](#tests-de-snapshot)
- [Couverture du Code et Configuration](#couverture-du-code-et-configuration)
- [Matchers Personnalisés et Extension de Jest](#matchers-personnalises-et-extension-de-jest)
- [Conclusion](#conclusion)

---

## Configuration de Jest dans un Projet React

**Définition** : Jest peut être ajouté à n'importe quel projet React avec une configuration minimale. Si vous utilisez Create React App (CRA), Jest est préconfiguré.

**Exemple** :
```bash
npm install --save-dev jest
```

Pour les projets non-CRA, ajoutez un script de test :
```json
"scripts": {
  "test": "jest"
}
```

---

## Structure des Fichiers de Test et Conventions de Nommage

**Définition** : Jest trouve automatiquement les tests dans les dossiers `__tests__` ou les fichiers se terminant par `.test.js` ou `.spec.js`.

**Exemple** :
```
/src
  /components
    Button.js
    Button.test.js
```

---

## Comprendre les Blocs `describe`, `it` et `test`

**Définition** : Jest organise les tests en utilisant `describe`, avec des cas de test individuels définis en utilisant `test` ou `it` (alias).

**Exemple** :
```js
describe('Math', () => {
  it('adds numbers', () => {
    expect(1 + 2).toBe(3);
  });
});
```

---

## Matchers et Assertions (`expect`)

**Définition** : Jest fournit `expect()` avec un riche ensemble de matchers pour affirmer les résultats attendus.

**Exemple** :
```js
expect(value).toBe(42);
expect(arr).toContain(3);
expect(obj).toHaveProperty('key');
```

---

## Mocks, Espions et Mocks Manuels

**Définition** : Les mocks remplacent les fonctions réelles pour isoler le comportement. Les espions suivent les appels aux fonctions.

**Exemple** :
```js
const mockFn = jest.fn();
mockFn('hello');
expect(mockFn).toHaveBeenCalledWith('hello');
```

---

## Mocker les Modules et les Dépendances

**Définition** : Jest peut mocker les modules automatiquement ou manuellement en utilisant `jest.mock()`.

**Exemple** :
```js
jest.mock('./api');
import { fetchData } from './api';

fetchData.mockResolvedValue({ name: 'Test' });
```

---

## Gérer les Tests Asynchrones avec les Promesses et async/await

**Définition** : Utilisez `async/await` ou retournez une promesse pour gérer la logique asynchrone dans les tests.

**Exemple** :
```js
test('fetches data', async () => {
  const data = await getData();
  expect(data).toBeDefined();
});
```

---

## Tests de Snapshot

**Définition** : Jest peut sérialiser et enregistrer la sortie de l'UI pour comparer les rendus futurs.

**Exemple** :
```js
import { render } from '@testing-library/react';
import Button from './Button';

test('renders correctly', () => {
  const { asFragment } = render(<Button>Click</Button>);
  expect(asFragment()).toMatchSnapshot();
});
```

---

## Couverture du Code et Configuration

**Définition** : Jest peut suivre les lignes de code qui sont testées en utilisant `--coverage`.

**Exemple** :
```bash
npm test -- --coverage
```

Configuration via `jest.config.js` :
```js
module.exports = {
  collectCoverage: true,
  coverageDirectory: "coverage",
};
```

---

## Matchers Personnalisés et Extension de Jest

**Définition** : Vous pouvez écrire ou importer des matchers personnalisés pour améliorer la lisibilité.

**Exemple** :
```js
expect.extend({
  toBeWithinRange(received, min, max) {
    const pass = received >= min && received <= max;
    return {
      message: () => `expected ${received} to be within ${min} - ${max}`,
      pass,
    };
  },
});

expect(10).toBeWithinRange(5, 15);
```

---

## Conclusion

**Points Clés à Retenir** :
1. Jest est un framework de test complet avec des fonctionnalités de mocking, d'assertions et de couverture intégrées.
2. Structurez clairement les tests en utilisant `describe` et `test`.
3. Utilisez les mocks pour isoler le comportement et tester les cas limites.
4. Gérez le code asynchrone avec `async/await` ou les promesses retournées.
5. Les tests de snapshot et de couverture aident à valider et à mesurer l'efficacité des tests.

**Exercice Pratique** :
- Mettre en place une fonction utilitaire de base et la tester en utilisant Jest.
- Écrire un test de snapshot pour un petit composant.
- Mocker une fonction qui retourne une promesse et vérifier sa sortie.
