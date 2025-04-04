
# Fonctionnalités ES6 et JavaScript Moderne

Ce cours présente les fonctionnalités modernes de JavaScript introduites dans ES6 et au-delà. Ces fonctionnalités aident à écrire un code plus propre, plus efficace et plus facile à maintenir. En les maîtrisant, vous serez mieux équipé pour écrire des applications plus puissantes.

## Table des Matières
1. [Déclarations Let et Const](#déclarations-let-et-const)
2. [Fonctions Fléchées et `this` Lexical](#fonctions-fléchées-et-this-lexical)
3. [Gabarits Littéraux (Template Literals)](#gabarits-littéraux-template-literals)
4. [Paramètres par Défaut](#paramètres-par-défaut)
5. [Opérateurs Rest et Spread](#opérateurs-rest-et-spread)
6. [Affectation par Déstructuration (Objets, Tableaux)](#affectation-par-déstructuration-objets-tableaux)
7. [Modules : `import` et `export`](#modules-import-et-export)
8. [Littéraux d'Objet Améliorés](#littéraux-d'objet-améliorés)
9. [Itérateurs et Générateurs](#itérateurs-et-générateurs)
10. [Symboles et Itérables](#symboles-et-itérables)

---

## Déclarations Let et Const
`let` et `const` sont des déclarations de variables à portée de bloc introduites dans ES6. `let` vous permet de réassigner des variables, tandis que `const` définit des constantes qui ne peuvent pas être réassignées.

Exemple :
```javascript
let a = 5;
a = 10;  // Autorisé

const b = 15;
b = 20;  // Erreur : Affectation à une variable constante
```

---

## Fonctions Fléchées et `this` Lexical
Les fonctions fléchées offrent une syntaxe concise et lient lexicalement le mot-clé `this`, ce qui signifie qu'elles héritent de la valeur de `this` de leur contexte environnant.

Exemple :
```javascript
let obj = {
  value: 42,
  getValue: function() {
    return () => this.value;  // La fonction fléchée utilise 'this' lié lexicalement
  }
};

let getVal = obj.getValue();
console.log(getVal());  // 42
```

---

## Gabarits Littéraux (Template Literals)
Les gabarits littéraux permettent les expressions intégrées et les chaînes de caractères multi-lignes, améliorant la lisibilité et réduisant le besoin de concaténation de chaînes.

Exemple :
```javascript
let name = 'Alice';
let message = `Hello, ${name}!`;
console.log(message);  // Hello, Alice!

let multiline = `This is
a multiline string.`;
console.log(multiline);
```

---

## Paramètres par Défaut
Vous pouvez attribuer des valeurs par défaut aux paramètres de fonction, qui seront utilisées si aucune valeur n'est fournie lors de l'appel de la fonction.

Exemple :
```javascript
function greet(name = 'Guest') {
  console.log(`Hello, ${name}!`);
}

greet('Alice');  // Hello, Alice!
greet();         // Hello, Guest!
```

---

## Opérateurs Rest et Spread
- L'**opérateur rest** (`...`) vous permet de collecter plusieurs valeurs dans un seul tableau ou objet.
- L'**opérateur spread** (`...`) vous permet de décompresser les éléments de tableaux ou d'objets.

Exemples :
```javascript
// Opérateur Rest
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3));  // 6

// Opérateur Spread
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5];
console.log(arr2);  // [1, 2, 3, 4, 5]
```

---

## Affectation par Déstructuration (Objets, Tableaux)
La déstructuration vous permet de décompresser les valeurs de tableaux ou les propriétés d'objets dans des variables distinctes.

Exemples :
```javascript
// Déstructuration de Tableau
let arr = [1, 2, 3];
let [a, b] = arr;
console.log(a, b);  // 1 2

// Déstructuration d'Objet
let obj = { name: 'Alice', age: 25 };
let { name, age } = obj;
console.log(name, age);  // Alice 25
```

---

## Modules : `import` et `export`
Les modules vous permettent de diviser votre code en parties réutilisables. `export` rend des parties de votre code disponibles pour une utilisation dans d'autres fichiers, et `import` vous permet de les importer.

Exemple :
```javascript
// math.js (module)
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// main.js (importation)
import { add, subtract } from './math.js';
console.log(add(2, 3));  // 5
```

---

## Littéraux d'Objet Améliorés
ES6 a introduit une syntaxe abrégée pour les littéraux d'objet, ce qui facilite la définition des méthodes et des propriétés.

Exemple :
```javascript
let name = 'Alice';
let age = 25;

let person = {
  name,
  age,
  greet() {
    console.log(`Hello, ${this.name}!`);
  }
};

person.greet();  // Hello, Alice!
```

---

## Itérateurs et Générateurs
- Les **itérateurs** sont des objets qui permettent un comportement d'itération personnalisé.
- Les **générateurs** sont des fonctions qui peuvent produire plusieurs valeurs au fil du temps, en suspendant leur exécution.

Exemple :
```javascript
// Itérateur
let arr = [1, 2, 3];
let iterator = arr[Symbol.iterator]();
console.log(iterator.next());  // { value: 1, done: false }
console.log(iterator.next());  // { value: 2, done: false }

// Générateur
function* count() {
  yield 1;
  yield 2;
  yield 3;
}

let gen = count();
console.log(gen.next());  // { value: 1, done: false }
console.log(gen.next());  // { value: 2, done: false }
```

---

## Symboles et Itérables
- Les **symboles** sont des identifiants uniques et immuables utilisés pour créer des propriétés d'objet.
- Les **itérables** sont des objets qui définissent une méthode d'itérateur, ce qui leur permet d'être utilisés dans des boucles comme `for...of`.

Exemple :
```javascript
// Symbole
let unique = Symbol('description');
let obj = { [unique]: 'value' };
console.log(obj[unique]);  // value

// Itérable
let iterable = {
  data: [1, 2, 3],
  [Symbol.iterator]: function() {
    let index = 0;
    let data = this.data;
    return {
      next: function() {
        if (index < data.length) {
          return { value: data[index++], done: false };
        } else {
          return { done: true };
        }
      }
    };
  }
};

for (let num of iterable) {
  console.log(num);  // 1, 2, 3
}
```

---

## Conclusion

### Points Clés à Retenir :
1. **Let et Const** : Utilisez `let` pour les variables qui changent et `const` pour les constantes.
2. **Fonctions Fléchées** : Fournissent une syntaxe concise et lient lexicalement `this`.
3. **Gabarits Littéraux** : Facilitent la manipulation des chaînes avec des expressions intégrées.
4. **Opérateurs Rest et Spread** : Simplifient le travail avec les tableaux et les objets.
5. **Déstructuration** : Décompressez facilement les valeurs des tableaux et des objets.
6. **Modules** : Utilisez `import` et `export` pour organiser le code en unités réutilisables.
7. **Générateurs** : Créez des fonctions qui peuvent suspendre et reprendre leur exécution.
8. **Symboles** : Fournissent des identifiants uniques pour les propriétés d'objet.

### Exercice Pratique :
1. Utilisez la déstructuration pour extraire des valeurs d'un objet et d'un tableau.
2. Écrivez une fonction générateur qui produit une séquence infinie de nombres.
3. Créez un module qui exporte des fonctions pour les opérations arithmétiques de base (addition, soustraction) et importez-le dans un autre fichier.
4. Utilisez l'opérateur spread pour fusionner deux tableaux, puis utilisez l'opérateur rest pour créer une fonction qui additionne un nombre inconnu d'arguments.
5. Écrivez un programme qui utilise `let`, `const` et des `fonctions fléchées` pour un petit projet, tel qu'un gestionnaire de tâches ou une calculatrice.
