
# Notions Fondamentales de React 19 & Essentiels du JavaScript Moderne

React 19 introduit un modèle déclaratif puissant pour construire des interfaces utilisateur interactives, avec un fort accent sur la simplicité et la performance. Maîtriser les notions fondamentales et le JavaScript moderne est essentiel pour construire des applications React robustes.

---

## Table des Matières
- [Introduction à React 19 et JSX](#introduction-à-react-19-et-jsx)
- [JavaScript ESNext pour les Développeurs React](#esnext-javascript-for-react-developers)
  - [let, const, fonctions fléchées](#let-const-arrow-functions)
  - [Déstructuration, Spread/Rest](#destructuring-spreadrest)
  - [Modules et Imports](#modules-and-imports)
  - [Async/Await et Promises](#asyncawait-and-promises)
- [Composants React](#react-components)
  - [Composants Fonctionnels vs Composants Classe](#function-vs-class-components)
  - [Props et Enfants des Composants](#component-props-and-children)
  - [Rendu Conditionnel](#conditional-rendering)
- [Bases de la Gestion d'État](#state-management-basics)
  - [Hook useState](#usestate-hook)
  - [Gestion des Événements](#handling-events)
- [Listes et Clés dans React](#lists-and-keys-in-react)
- [Formulaires dans React](#forms-in-react)
  - [Composants Contrôlés vs Non Contrôlés](#controlled-vs-uncontrolled-components)
  - [Bases de la Validation de Formulaires](#form-validation-basics)
- [Conclusion & Points Clés](#conclusion--key-takeaways)
- [Exercice Pratique](#practical-exercise)

---

## Introduction à React 19 et JSX
**Définition :** JSX est une extension de syntaxe pour JavaScript qui permet d'écrire du code de type HTML dans les composants React.
**Exemple :**
```jsx
const Hello = () => <h1>Hello, React 19!</h1>;
```

---

## JavaScript ESNext pour les Développeurs React

### let, const, fonctions fléchées
**Définition :** `let` et `const` déclarent des variables à portée de bloc ; les fonctions fléchées fournissent des expressions de fonction concises.
**Exemple :**
```js
const add = (a, b) => a + b;
let counter = 0;
```

### Déstructuration, Spread/Rest
**Définition :** La déstructuration extrait des valeurs de tableaux/objets ; les opérateurs spread/rest gèrent des ensembles de variables.
**Exemple :**
```js
const { name } = user;
const newArr = [...oldArr, 4];
```

### Modules et Imports
**Définition :** Les modules JavaScript permettent l'organisation et la réutilisation du code via `import` et `export`.
**Exemple :**
```js
import React from 'react';
export const Button = () => <button>Click</button>;
```

### Async/Await et Promises
**Définition :** Les Promises gèrent les opérations asynchrones ; `async/await` simplifie la syntaxe.
**Exemple :**
```js
const fetchData = async () => {
  const res = await fetch('/api');
  const data = await res.json();
};
```

---

## Composants React

### Composants Fonctionnels vs Composants Classe
**Définition :** Les composants fonctionnels sont le standard moderne ; les composants classe sont hérités.
**Exemple :**
```jsx
const Hello = () => <p>Hello</p>; // Préféré
```

### Props et Enfants des Composants
**Définition :** Les Props transmettent des données aux composants ; `children` fait référence au contenu imbriqué.
**Exemple :**
```jsx
const Card = ({ title, children }) => <div><h2>{title}</h2>{children}</div>;
```

### Rendu Conditionnel
**Définition :** Afficher différents éléments d'interface utilisateur en fonction de conditions.
**Exemple :**
```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

---

## Bases de la Gestion d'État

### Hook useState
**Définition :** `useState` ajoute un état local aux composants fonctionnels.
**Exemple :**
```jsx
const [count, setCount] = useState(0);
```

### Gestion des Événements
**Définition :** Les événements gèrent les interactions utilisateur comme les clics et les entrées.
**Exemple :**
```jsx
<button onClick={() => setCount(count + 1)}>Increment</button>
```

---

## Listes et Clés dans React
**Définition :** Utilisez `.map()` pour afficher des listes ; fournissez une `key` unique à chaque élément.
**Exemple :**
```jsx
{items.map(item => <li key={item.id}>{item.name}</li>)}
```

---

## Formulaires dans React

### Composants Contrôlés vs Non Contrôlés
**Définition :** Les composants contrôlés stockent les valeurs d'entrée dans l'état ; les non contrôlés s'appuient sur les refs.
**Exemple (Contrôlé) :**
```jsx
<input value={value} onChange={e => setValue(e.target.value)} />
```

### Bases de la Validation de Formulaires
**Définition :** Valider les entrées utilisateur à l'aide de l'état ou de bibliothèques.
**Exemple :**
```jsx
if (!email.includes('@')) setError('Invalid email');
```

---

## Conclusion & Points Clés
- React 19 met l'accent sur les composants fonctionnels et les hooks.
- JSX rend la logique de l'interface utilisateur expressive et lisible.
- Les fonctionnalités JavaScript ESNext sont essentielles pour un code React propre.
- L'état et les props sont au cœur du flux de données dans React.
- Les composants contrôlés permettent une gestion robuste des formulaires.

---

## Exercice Pratique

Créez un petit composant React qui :
1. Affiche une entrée et un bouton.
2. Stocke l'entrée dans l'état en utilisant `useState`.
3. Au clic du bouton, affiche conditionnellement un message de salutation en utilisant la valeur de l'entrée.
4. Valide que l'entrée n'est pas vide avant d'afficher le message.
