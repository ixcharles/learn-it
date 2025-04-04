
# Modèles Avancés dans React Testing Library

Ce cours explore les stratégies de test avancées avec React Testing Library (RTL), en se concentrant sur des scénarios d'application réalistes comme le routage, la gestion d'état et la gestion du comportement complexe des composants.

---

## Table des Matières

- [Tester avec Router, Redux et la Gestion d'État Asynchrone](#tester-avec-router-redux-et-la-gestion-detat-asynchrone)
- [Tester les Limites d'Erreur et Suspense](#tester-les-limites-derreur-et-suspense)
- [Construire et Utiliser des Fonctions de Rendu Personnalisées](#construire-et-utiliser-des-fonctions-de-rendu-personnalisees)
- [Stratégies pour les Utilitaires de Test Réutilisables](#strategies-pour-les-utilitaires-de-test-reutilisables)
- [Tester les Composants Chargés Paresseusement](#tester-les-composants-charges-paresseusement)
- [Gérer les Conditions de Course et les Tests Instables](#gerer-les-conditions-de-course-et-les-tests-instables)
- [Structurer les Suites de Tests dans les Applications Complexes](#structurer-les-suites-de-tests-dans-les-applications-complexes)
- [Bonnes Pratiques et Anti-Modèles RTL](#bonnes-pratiques-et-anti-modeles-rtl)
- [Conclusion](#conclusion)

---

## Tester avec Router, Redux et la Gestion d'État Asynchrone

**Définition** : Enveloppez les composants avec les fournisseurs de router et Redux pour tester la navigation et l'état global.

**Exemple** :
```js
render(
  <Provider store={store}>
    <MemoryRouter initialEntries={['/profile']}>
      <App />
    </MemoryRouter>
  </Provider>
);
expect(screen.getByText(/profile/i)).toBeInTheDocument();
```

---

## Tester les Limites d'Erreur et Suspense

**Définition** : Testez les UIs de repli en déclenchant des erreurs ou des délais dans les composants chargés paresseusement.

**Exemple** :
```js
jest.spyOn(console, 'error').mockImplementation(() => {}); // supprimer la sortie d'erreur
render(<ErrorBoundary><ComponentThatThrows /></ErrorBoundary>);
expect(screen.getByText(/something went wrong/i)).toBeInTheDocument();
```

Test de Suspense :
```js
render(
  <Suspense fallback={<span>Loading...</span>}>
    <LazyComponent />
  </Suspense>
);
expect(screen.getByText(/loading/i)).toBeInTheDocument();
```

---

## Construire et Utiliser des Fonctions de Rendu Personnalisées

**Définition** : Les fonctions `render` personnalisées centralisent les fournisseurs pour des tests plus propres et réutilisables.

**Exemple** :
```js
const customRender = (ui, options) =>
  render(<AppProviders>{ui}</AppProviders>, options);

// utilisation
customRender(<Dashboard />);
```

---

## Stratégies pour les Utilitaires de Test Réutilisables

**Définition** : Extrayez la logique partagée, les requêtes et les assistants dans des fichiers d'utilitaires de test.

**Exemple** :
```js
// test-utils.js
export const getSubmitButton = () =>
  screen.getByRole('button', { name: /submit/i });
```

Utilisation dans le test :
```js
import { getSubmitButton } from './test-utils';
expect(getSubmitButton()).toBeEnabled();
```

---

## Tester les Composants Chargés Paresseusement

**Définition** : Enveloppez les composants paresseux dans `Suspense` et affirmez les états de repli avant la résolution.

**Exemple** :
```js
const LazyPage = React.lazy(() => import('./LazyPage'));
render(
  <Suspense fallback={<span>Loading...</span>}>
    <LazyPage />
  </Suspense>
);
expect(screen.getByText(/loading/i)).toBeInTheDocument();
```

---

## Gérer les Conditions de Course et les Tests Instables

**Définition** : Utilisez `waitFor`, affirmez les états intermédiaires et évitez les tests basés sur `setTimeout`.

**Conseils** :
- Affirmez toujours les indicateurs de chargement.
- Évitez de vous fier à des délais fixes.
- Préférez `findBy*` pour les requêtes asynchrones.

---

## Structurer les Suites de Tests dans les Applications Complexes

**Définition** : Regroupez logiquement les tests par domaine, fonctionnalité ou flux utilisateur.

**Exemple** :
```
/__tests__
  /auth
    login.test.js
  /dashboard
    widgets.test.js
```

Utilisez les blocs `describe()` pour le regroupement :
```js
describe('Dashboard Widgets', () => {
  test('loads metrics', () => {});
});
```

---

## Bonnes Pratiques et Anti-Modèles RTL

**Bonnes Pratiques** :
- Utilisez des requêtes qui reflètent l'interaction utilisateur (par exemple, `getByRole`, `getByLabelText`).
- Préférez `userEvent` à `fireEvent`.

**Anti-Modèles** :
- Évitez `getByTestId` sauf nécessité.
- Évitez les détails d'implémentation comme l'état interne ou les noms de classes.

---

## Conclusion

**Points Clés à Retenir** :
1. Utilisez des fournisseurs et des wrappers pour simuler des environnements d'application réalistes.
2. Abstrayez la configuration des tests avec des fonctions de rendu personnalisées réutilisables.
3. Gérez l'UI asynchrone en toute sécurité avec `waitFor`, `findBy` et les replis de Suspense.
4. Gardez les tests ciblés, organisés et lisibles avec des utilitaires partagés.
5. Évitez de vous fier aux détails d'implémentation du DOM et aux IDs de test instables.

**Exercice Pratique** :
- Créer une page de profil chargée paresseusement avec un repli.
- Tester son rendu avec `React.Suspense`.
- Simuler un bascule pilotée par Redux et affirmer les changements d'UI.
