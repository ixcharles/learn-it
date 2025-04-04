
# Fonctions Avancées et Programmation Fonctionnelle

Ce cours explore les concepts avancés des fonctions JavaScript et de la programmation fonctionnelle, vous fournissant des outils puissants pour écrire du code propre, efficace et réutilisable. Les sujets abordés vont des fonctions d'ordre supérieur à la programmation asynchrone avec les promesses.

## Table des Matières
1. [Fonctions d'Ordre Supérieur](#fonctions-d'ordre-supérieur)
2. [Fermetures (Closures)](#fermetures-closures)
3. [Curryfication de Fonctions (Function Currying)](#curryfication-de-fonctions-function-currying)
4. [Récursion](#récursion)
5. [Méthodes `bind`, `call` et `apply`](#méthodes-bind-call-et-apply)
6. [Le Pattern Module](#le-pattern-module)
7. [IIFE (Immediately Invoked Function Expressions)](#iife-immediately-invoked-function-expressions)
8. [Fonctions Async et Promesses](#fonctions-async-et-promesses)

---

## Fonctions d'Ordre Supérieur
Les fonctions d'ordre supérieur sont des fonctions qui prennent d'autres fonctions comme arguments ou renvoient une fonction comme résultat.

Exemple :
```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

function sayHello(func, name) {
  return func(name);
}

console.log(sayHello(greet, 'Alice'));  // Hello, Alice!
```

---

## Fermetures (Closures)
Une fermeture est une fonction qui conserve l'accès à son environnement lexical, même après que la fonction externe a terminé son exécution.

Exemple :
```javascript
function outer() {
  let counter = 0;
  return function inner() {
    counter++;
    console.log(counter);
  };
}

let counterFunction = outer();
counterFunction();  // 1
counterFunction();  // 2
```

---

## Curryfication de Fonctions (Function Currying)
La curryfication est le processus de transformation d'une fonction qui prend plusieurs arguments en une séquence de fonctions qui prennent chacune un seul argument.

Exemple :
```javascript
function multiply(a) {
  return function(b) {
    return a * b;
  };
}

let multiplyBy2 = multiply(2);
console.log(multiplyBy2(3));  // 6
```

---

## Récursion
La récursion se produit lorsqu'une fonction s'appelle elle-même pour résoudre une instance plus petite du même problème. Elle est généralement utilisée pour les problèmes qui peuvent être divisés en sous-problèmes plus petits.

Exemple :
```javascript
function factorial(n) {
  if (n === 0) return 1;
  return n * factorial(n - 1);
}

console.log(factorial(5));  // 120
```

---

## Méthodes `bind`, `call` et `apply`
Ces méthodes vous permettent de contrôler le contexte (`this`) d'une fonction.

- `bind`: Renvoie une nouvelle fonction avec une valeur `this` spécifiée.
- `call`: Appelle une fonction avec une valeur `this` spécifiée et des arguments.
- `apply`: Similaire à `call`, mais les arguments sont passés sous forme de tableau.

Exemple :
```javascript
let person = { name: 'Alice' };

function greet(greeting) {
  console.log(`${greeting}, ${this.name}!`);
}

let greetAlice = greet.bind(person);
greetAlice('Hello');  // Hello, Alice!

greet.call(person, 'Hi');  // Hi, Alice!
greet.apply(person, ['Good evening']);  // Good evening, Alice!
```

---

## Le Pattern Module
Le pattern module est une façon d'organiser le code en JavaScript en créant des méthodes privées et publiques au sein d'un seul objet ou fonction. Il aide à l'encapsulation et à éviter la pollution de la portée globale.

Exemple :
```javascript
let counterModule = (function() {
  let count = 0;

  return {
    increment: function() {
      count++;
      console.log(count);
    },
    decrement: function() {
      count--;
      console.log(count);
    }
  };
})();

counterModule.increment();  // 1
counterModule.decrement();  // 0
```

---

## IIFE (Immediately Invoked Function Expressions)
Une IIFE est une expression de fonction qui est exécutée immédiatement après sa création, souvent utilisée pour créer une nouvelle portée afin d'éviter de polluer l'espace de noms global.

Exemple :
```javascript
(function() {
  let message = 'I am an IIFE!';
  console.log(message);
})();  // I am an IIFE!
```

---

## Fonctions Async et Promesses
Les fonctions async vous permettent d'écrire du code asynchrone dans un style synchrone en utilisant les mots-clés `async` et `await`. Les promesses représentent l'achèvement (ou l'échec) éventuel d'une opération asynchrone.

Exemple :
```javascript
// Using Promise
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve('Data fetched!'), 1000);
  });
}

fetchData().then(data => console.log(data));  // Data fetched!

// Using Async/Await
async function fetchDataAsync() {
  let data = await fetchData();
  console.log(data);  // Data fetched!
}

fetchDataAsync();
```

---

## Conclusion

### Points Clés à Retenir :
1. Les fonctions d'ordre supérieur permettent des paradigmes de programmation fonctionnelle en passant des fonctions comme arguments ou en renvoyant des fonctions.
2. Les fermetures permettent aux fonctions internes de conserver l'accès aux variables de leur fonction externe.
3. La curryfication de fonctions décompose les fonctions en parties plus petites et réutilisables.
4. La récursion est une technique puissante pour résoudre des problèmes qui peuvent être divisés en sous-problèmes plus petits.
5. Les méthodes `bind`, `call` et `apply` sont essentielles pour contrôler le contexte `this` des fonctions.
6. Le pattern module encapsule le code, offrant la confidentialité et évitant de polluer la portée globale.
7. IIFE permet l'exécution immédiate des fonctions, utile pour créer des portées isolées.
8. Async/await simplifie le travail avec le code asynchrone, le rendant plus facile à lire et à maintenir.

### Exercice Pratique :
1. Écrivez une fonction utilisant la récursion pour calculer le nième nombre de Fibonacci.
2. Implémentez une fonction de curryfication qui calcule la somme de plusieurs nombres.
3. Créez un module qui gère une liste de tâches, avec des méthodes pour ajouter, supprimer et lister les tâches.
4. Refactorisez une fonction asynchrone existante basée sur des callbacks en utilisant `async/await`.
