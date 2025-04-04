
# Techniques et Modèles Avancés de Jest

Ce cours explore les modèles de test avancés et les fonctionnalités de Jest pour améliorer la fiabilité, la maintenabilité et la performance des tests pour les applications React à grande échelle.

---

## Table des Matières

- [Tester avec les Fournisseurs de Context et les Hooks](#tester-avec-les-fournisseurs-de-context-et-les-hooks)
- [Mocker Fetch, Axios et les APIs](#mocker-fetch-axios-et-les-apis)
- [Gérer les Implémentations de Mocks Complexes](#gerer-les-implementations-de-mocks-complexes)
- [Travailler avec les Timers et les Intervals](#travailler-avec-les-timers-et-les-intervals)
- [Déboguer les Tests Jest](#debugger-les-tests-jest)
- [Optimisation des Performances dans les Grandes Suites de Tests](#optimisation-des-performances-dans-les-grandes-suites-de-tests)
- [Parallélisation et Exécution des Tests en CI/CD](#parallelisation-et-execution-des-tests-en-cicd)
- [Transformateurs et Sérialiseurs Jest Personnalisés](#transformateurs-et-serialiseurs-jest-personnalises)
- [Utiliser `jest-each` pour les Tests Pilotés par les Données](#utiliser-jest-each-pour-les-tests-pilotes-par-les-donnees)
- [Conclusion](#conclusion)

---

## Tester avec les Fournisseurs de Context et les Hooks

**Définition** : Lorsque les composants dépendent du contexte ou des hooks, enveloppez-les dans des fournisseurs pendant les tests.

**Exemple** :
```js
render(
  <AuthProvider>
    <Dashboard />
  </AuthProvider>
);
```

Wrapper de rendu personnalisé :
```js
const renderWithProvider = (ui) => render(<AuthProvider>{ui}</AuthProvider>);
```

---

## Mocker Fetch, Axios et les APIs

**Définition** : Mockez les requêtes externes en utilisant `jest.mock()` ou `jest.fn()` pour des tests contrôlés.

**Exemple** :
```js
jest.mock('axios');
import axios from 'axios';

axios.get.mockResolvedValue({ data: { user: 'John' } });
```

Pour fetch natif :
```js
global.fetch = jest.fn(() =>
  Promise.resolve({ json: () => Promise.resolve({ user: 'Jane' }) })
);
```

---

## Gérer les Implémentations de Mocks Complexes

**Définition** : Utilisez `mockImplementation`, `mockReturnValue` ou des mocks conditionnels pour une logique complexe.

**Exemple** :
```js
const mockApi = jest.fn()
  .mockImplementationOnce(() => Promise.resolve('first'))
  .mockImplementationOnce(() => Promise.resolve('second'));
```

---

## Travailler avec les Timers et les Intervals

**Définition** : Contrôlez le code basé sur le temps avec les faux timers de Jest.

**Exemple** :
```js
jest.useFakeTimers();
setTimeout(() => callback(), 1000);
jest.runAllTimers();
expect(callback).toHaveBeenCalled();
```

---

## Déboguer les Tests Jest

**Définition** : Utilisez `--detectOpenHandles`, `--runInBand` et les logs en ligne pour isoler les problèmes de test.

**Exemple** :
```bash
jest --detectOpenHandles
```
```js
console.log('Debug:', data);
```

Utilisez `.only` ou `.skip` :
```js
test.only('runs this test only', () => {});
```

---

## Optimisation des Performances dans les Grandes Suites de Tests

**Définition** : Améliorez la vitesse en utilisant les mocks de modules, les fichiers de configuration partagés et en évitant les rendus inutiles.

**Conseils** :
- Utilisez `--runInBand` localement pour déboguer les performances.
- Évitez les arbres profonds pour les tests unitaires.
- Partagez la configuration avec `beforeEach` et des utilitaires de rendu personnalisés.

---

## Parallélisation et Exécution des Tests en CI/CD

**Définition** : Jest exécute les tests en parallèle par défaut ; la configuration CI peut l'optimiser davantage.

**Exemple** :
```bash
jest --maxWorkers=50%
```

En CI :
```yaml
jobs:
  test:
    steps:
      - run: npm ci
      - run: npm test -- --coverage
```

---

## Transformateurs et Sérialiseurs Jest Personnalisés

**Définition** : Les transformateurs prétraitent les fichiers (comme JSX), et les sérialiseurs formatent les sorties de snapshot.

**Exemple** :
```js
// jest.config.js
module.exports = {
  snapshotSerializers: ['enzyme-to-json/serializer'],
  transform: {
    '^.+\\.jsx?$': 'babel-jest',
  },
};
```

---

## Utiliser `jest-each` pour les Tests Pilotés par les Données

**Définition** : Exécutez le même test avec plusieurs ensembles de données en utilisant `jest-each`.

**Exemple** :
```js
test.each([
  [1, 2, 3],
  [2, 3, 5],
])('adds %i + %i to equal %i', (a, b, expected) => {
  expect(a + b).toBe(expected);
});
```

---

## Conclusion

**Points Clés à Retenir** :
1. Les composants sensibles au contexte nécessitent des wrappers personnalisés dans les tests.
2. Utilisez des mocks détaillés pour un contrôle total sur les scénarios de test.
3. Les faux timers aident à tester les fonctionnalités basées sur le temps.
4. Optimisez les performances en isolant et en parallélisant les tests.
5. `jest-each` simplifie les tests répétitifs pilotés par les données.

**Exercice Pratique** :
- Écrire un test qui mocke `axios.get` avec plusieurs réponses.
- Créer un composant utilisant `useEffect` avec `setTimeout`, et le tester en utilisant les faux timers.
- Utiliser `jest-each` pour tester une fonction mathématique avec plusieurs combinaisons d'entrées/sorties.
