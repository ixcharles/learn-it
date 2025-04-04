
# Gestion des Erreurs et Débogage en JavaScript

Ce cours se concentre sur la gestion des erreurs en JavaScript et les techniques de débogage. Apprenez à gérer les erreurs, à utiliser les outils de débogage et à optimiser les performances pour construire des applications JavaScript robustes.

## Table des Matières
1. [Types d'Erreurs en JavaScript](#types-d'erreurs-en-javascript)
2. [Gestion des Erreurs Synchrones](#gestion-des-erreurs-synchrones)
3. [Gestion des Erreurs Asynchrones](#gestion-des-erreurs-asynchrones)
4. [Utilisation de `try`, `catch`, `finally`](#utilisation-de-try-catch-finally)
5. [Débogage avec des Points d'Arrêt](#débogage-avec-des-points-d'arrêt)
6. [Utilisation des Outils de Développement (DevTools) pour Déboguer](#utilisation-des-outils-de-développement-devtools-pour-déboguer)
7. [Journalisation avec `console`](#journalisation-avec-console)
8. [Profilage et Optimisation des Performances](#profilage-et-optimisation-des-performances)
9. [Création d'Erreurs Personnalisées](#création-d'erreurs-personnalisées)
10. [Écriture de Tests Unitaires pour JavaScript](#écriture-de-tests-unitaires-pour-javascript)

---

## Types d'Erreurs en JavaScript
JavaScript a trois principaux types d'erreurs :
1. **Erreurs de Syntaxe** : Erreurs dans la structure du code (par exemple, parenthèses manquantes).
2. **Erreurs d'Exécution** : Erreurs qui se produisent pendant l'exécution du script (par exemple, variables non définies).
3. **Erreurs Logiques** : Erreurs dans la logique du code, où le programme s'exécute sans plantage mais produit des résultats incorrects.

Exemple :
```javascript
// Erreur de Syntaxe
let x = (10 + 5;  // Parenthèse fermante manquante

// Erreur d'Exécution
let y;
console.log(y.someMethod());  // TypeError: Cannot read property 'someMethod' of undefined
```

---

## Gestion des Erreurs Synchrones
Les erreurs synchrones se produisent pendant l'exécution du code. Elles sont généralement gérées à l'aide de `try`, `catch` et `finally`.

Exemple :
```javascript
try {
  let result = 10 / 0;
  console.log(result);
} catch (error) {
  console.log('Caught an error:', error);
} finally {
  console.log('This will run no matter what');
}
```

---

## Gestion des Erreurs Asynchrones
Les erreurs asynchrones se produisent dans les promesses ou les callbacks. Gérez-les à l'aide de `.catch()` pour les promesses ou de `try...catch` avec `async/await`.

Exemple avec les Promesses :
```javascript
fetch('https://api.example.com')
  .then(response => response.json())
  .catch(error => console.log('Error fetching data:', error));
```

Exemple avec Async/Await :
```javascript
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.log('Error:', error);
  }
}
```

---

## Utilisation de `try`, `catch`, `finally`
Le bloc `try...catch` est utilisé pour gérer les erreurs dans le code synchrone et asynchrone. Le bloc `finally` exécute du code après le bloc `try` ou `catch`, quel que soit le résultat.

Exemple :
```javascript
try {
  let value = JSON.parse('invalid JSON');
} catch (error) {
  console.log('Parsing error:', error);
} finally {
  console.log('This always runs');
}
```

---

## Débogage avec des Points d'Arrêt
Les points d'arrêt vous permettent de mettre en pause l'exécution du code à une ligne spécifique pour inspecter les variables et le flux. Vous pouvez définir des points d'arrêt dans les outils de développement du navigateur (DevTools).

Étapes :
1. Ouvrez les DevTools (F12 ou Clic droit > Inspecter).
2. Naviguez vers l'onglet "Sources".
3. Trouvez la ligne de code souhaitée.
4. Cliquez sur le numéro de ligne pour définir un point d'arrêt.
5. Rechargez la page et l'exécution s'arrêtera au point d'arrêt, permettant l'inspection.

---

## Utilisation des Outils de Développement (DevTools) pour Déboguer
Les DevTools fournissent de puissantes fonctionnalités pour déboguer le code JavaScript :
1. **Console** : Affichez les erreurs, les avertissements et les instructions de journalisation.
2. **Débogueur** : Mettez le code en pause aux points d'arrêt et parcourez l'exécution pas à pas.
3. **Surveillance des Variables** : Surveillez les valeurs des variables en temps réel.
4. **Pile d'Appels** : Affichez la séquence d'appels de fonctions menant à une erreur.
5. **Onglet Réseau** : Vérifiez les requêtes et les réponses réseau.

---

## Journalisation avec `console`
L'objet `console` aide au débogage en enregistrant des informations dans la console.

Exemples :
```javascript
console.log('Hello, World!');
console.warn('This is a warning');
console.error('An error occurred');
console.table([{ name: 'Alice', age: 25 }, { name: 'Bob', age: 30 }]);
```

---

## Profilage et Optimisation des Performances
Utilisez l'onglet **Performance** des DevTools pour analyser les performances d'exécution de votre application. Il aide à identifier les goulots d'étranglement tels que les fuites de mémoire, les longues durées de tâches ou le rendu inefficace.

Étapes :
1. Ouvrez DevTools > Onglet Performance.
2. Cliquez sur "Démarrer le profilage" et interagissez avec votre application.
3. Cliquez sur "Arrêter" pour analyser les données enregistrées.

Optimisez les performances en réduisant les manipulations du DOM, en utilisant `requestAnimationFrame` pour les animations et en minimisant les tâches synchrones.

---

## Création d'Erreurs Personnalisées
Vous pouvez créer des types d'erreurs personnalisés en étendant la classe intégrée `Error`, ce qui vous permet de fournir des messages d'erreur et des traces de pile plus spécifiques.

Exemple :
```javascript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = 'ValidationError';
  }
}

try {
  throw new ValidationError('Invalid input');
} catch (error) {
  console.log(error.name);  // ValidationError
  console.log(error.message);  // Invalid input
}
```

---

## Écriture de Tests Unitaires pour JavaScript
Les tests unitaires vérifient que des parties individuelles de votre code se comportent comme prévu. Les frameworks comme Jest, Mocha et Jasmine aident à automatiser les tests.

Exemple avec Jest :
```javascript
function sum(a, b) {
  return a + b;
}

test('sum adds two numbers correctly', () => {
  expect(sum(1, 2)).toBe(3);
});
```

Étapes :
1. Installez Jest : `npm install --save-dev jest`
2. Exécutez les tests : `npx jest`

---

## Conclusion

### Points Clés à Retenir :
1. **Types d'Erreurs** : Connaissez la différence entre les erreurs de syntaxe, d'exécution et logiques.
2. **Gestion des Erreurs** : Utilisez `try`, `catch` et `finally` pour gérer les erreurs, et gérez les erreurs asynchrones avec `.catch()` ou `async/await`.
3. **DevTools** : Utilisez les points d'arrêt, la console et l'onglet Performance pour un débogage et une optimisation efficaces.
4. **Erreurs Personnalisées** : Créez des types d'erreurs personnalisés en étendant la classe `Error` pour une meilleure gestion des erreurs.
5. **Tests Unitaires** : Écrivez des tests unitaires à l'aide de frameworks comme Jest pour vous assurer que votre code fonctionne comme prévu.

### Exercice Pratique :
1. Écrivez une fonction qui récupère des données d'une API et gère les erreurs à l'aide de `async/await` et `try...catch`.
2. Utilisez les DevTools pour déboguer une simple fonction JavaScript, en définissant des points d'arrêt et en inspectant les variables.
3. Créez une classe d'erreur personnalisée, `DataNotFoundError`, et utilisez-la pour lancer et intercepter des erreurs dans une fonction qui recherche des données dans un tableau.
4. Écrivez un simple test unitaire pour une fonction qui calcule l'aire d'un rectangle.
