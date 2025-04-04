
# Tests Pratiques avec React Testing Library

React Testing Library (RTL) encourage le test des composants d'une manière qui simule les interactions réelles de l'utilisateur. Ce cours se concentre sur l'utilisation efficace de RTL pour écrire des tests qui reflètent la manière dont les utilisateurs interagissent avec votre application React.

---

## Table des Matières

- [Configuration de React Testing Library (RTL)](#configuration-de-react-testing-library-rtl)
- [Requêtes : `getBy`, `queryBy`, `findBy` et leurs Variantes](#requetes-getby-queryby-findby-et-leurs-variantes)
- [Rendu des Composants et Utilisation de JSX](#rendu-des-composants-et-utilisation-de-jsx)
- [Simulation des Interactions Utilisateur avec `fireEvent` et `userEvent`](#simulation-des-interactions-utilisateur-avec-fireevent-et-userevent)
- [Tester les Formulaires et les Composants Contrôlés](#tester-les-formulaires-et-les-composants-controles)
- [Assertions pour les Éléments DOM et l'Accessibilité](#assertions-pour-les-elements-dom-et-laccessibilite)
- [Travailler avec les Portails et les Modales](#travailler-avec-les-portails-et-les-modales)
- [Tester les Hooks et les Hooks Personnalisés](#tester-les-hooks-et-les-hooks-personnalises)
- [Mocker les Contextes et les Fournisseurs](#mocker-les-contextes-et-les-fournisseurs)
- [Utiliser `waitFor`, `waitForElementToBeRemoved` et `act`](#utiliser-waitfor-waitforelementtoberemoved-et-act)
- [Conclusion](#conclusion)

---

## Configuration de React Testing Library (RTL)

**Définition** : RTL s'intègre à Jest et peut être installé dans n'importe quel projet React.

**Exemple** :
```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

---

## Requêtes : `getBy`, `queryBy`, `findBy` et leurs Variantes

**Définition** : Les requêtes sont des fonctions pour sélectionner des éléments dans le DOM.

- `getBy` : Lance une erreur si non trouvé.
- `queryBy` : Retourne null si non trouvé.
- `findBy` : Version asynchrone de `getBy`.

**Exemple** :
```js
const button = screen.getByRole('button', { name: /submit/i });
```

---

## Rendu des Composants et Utilisation de JSX

**Définition** : Utilisez `render()` pour rendre les composants à l'intérieur d'un DOM virtuel pour les tests.

**Exemple** :
```js
import { render, screen } from '@testing-library/react';
render(<button>Click Me</button>);
expect(screen.getByText('Click Me')).toBeInTheDocument();
```

---

## Simulation des Interactions Utilisateur avec `fireEvent` et `userEvent`

**Définition** : `userEvent` simule le comportement réel de l'utilisateur ; `fireEvent` déclenche directement les événements natifs.

**Exemple** :
```js
import userEvent from '@testing-library/user-event';
userEvent.type(input, 'hello');
userEvent.click(button);
```

---

## Tester les Formulaires et les Composants Contrôlés

**Définition** : Testez le comportement des formulaires en simulant les actions de saisie et de soumission.

**Exemple** :
```js
const input = screen.getByLabelText(/name/i);
userEvent.type(input, 'John');
expect(input).toHaveValue('John');
```

---

## Assertions pour les Éléments DOM et l'Accessibilité

**Définition** : Utilisez `@testing-library/jest-dom` pour des assertions sémantiques améliorées.

**Exemple** :
```js
expect(button).toBeEnabled();
expect(label).toHaveAccessibleName('Username');
```

---

## Travailler avec les Portails et les Modales

**Définition** : Testez les modales rendues en dehors de l'arbre DOM en interrogeant globalement.

**Exemple** :
```js
expect(screen.getByRole('dialog')).toBeVisible();
```

Si nécessaire, ajoutez un conteneur modal à `document.body` lors de la configuration.

---

## Tester les Hooks et les Hooks Personnalisés

**Définition** : Utilisez `@testing-library/react-hooks` (déprécié) ou enveloppez les hooks dans des composants de test.

**Exemple** :
```js
function TestComponent() {
  const value = useCustomHook();
  return <div>{value}</div>;
}
render(<TestComponent />);
expect(screen.getByText('expected value')).toBeInTheDocument();
```

---

## Mocker les Contextes et les Fournisseurs

**Définition** : Enveloppez les composants avec des fournisseurs de contexte pour fournir des valeurs mockées.

**Exemple** :
```js
render(
  <AuthContext.Provider value={{ user: 'Jane' }}>
    <Profile />
  </AuthContext.Provider>
);
```

---

## Utiliser `waitFor`, `waitForElementToBeRemoved` et `act`

**Définition** : Utilisez ces assistants pour gérer le comportement asynchrone et les mises à jour du DOM.

**Exemple** :
```js
await waitFor(() => {
  expect(screen.getByText(/loaded/i)).toBeInTheDocument();
});
await waitForElementToBeRemoved(() => screen.queryByText(/loading/i));
```

---

## Conclusion

**Points Clés à Retenir** :
1. RTL encourage les tests centrés sur l'utilisateur en interrogeant et en interagissant comme un utilisateur réel.
2. Utilisez `userEvent` pour des simulations plus précises.
3. Enveloppez les composants dans des fournisseurs de contexte lorsque cela est nécessaire.
4. Gérez les opérations asynchrones en utilisant `findBy`, `waitFor` et `act`.
5. Utilisez `jest-dom` pour des assertions meilleures et accessibles.

**Exercice Pratique** :
- Créer un formulaire simple avec un champ de texte et un bouton de soumission.
- Tester la saisie dans le champ et la soumission du formulaire.
- Utiliser `waitFor` pour tester le rendu asynchrone d'un message de validation.
