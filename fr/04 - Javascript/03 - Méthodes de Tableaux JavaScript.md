
# Méthodes de Tableaux JavaScript

Les tableaux sont une structure de données fondamentale en JavaScript, fournissant une collection d'éléments qui peuvent être consultés et manipulés. Ce cours explore en profondeur les méthodes de tableaux les plus couramment utilisées pour vous aider à maîtriser la manipulation des tableaux.

## Table des Matières
1. [Introduction aux Tableaux en JavaScript](#introduction-aux-tableaux-en-javascript)
2. [Accéder et Modifier les Éléments d'un Tableau](#accéder-et-modifier-les-éléments-d'un-tableau)
3. [Longueur du Tableau et Tableaux Multidimensionnels](#longueur-du-tableau-et-tableaux-multidimensionnels)
4. [Itérer à travers les Tableaux : `for`, `forEach()`, `map()`](#itérer-à-travers-les-tableaux-for-foreach-map)
5. [Filtrer les Tableaux : `filter()`](#filtrer-les-tableaux-filter)
6. [Réduire les Tableaux : `reduce()` et `reduceRight()`](#réduire-les-tableaux-reduce-et-reduceright)
7. [Mapper les Tableaux : `map()` et `flatMap()`](#mapper-les-tableaux-map-et-flatmap)
8. [Trier les Tableaux : `sort()` et `reverse()`](#trier-les-tableaux-sort-et-reverse)
9. [Trouver des Éléments : `find()`, `findIndex()`](#trouver-des-éléments-find-findindex)
10. [Vérifier la Présence d'Éléments : `includes()`, `indexOf()`](#vérifier-la-présence-d'éléments-includes-indexof)
11. [Diviser et Joindre les Tableaux : `split()`, `join()`](#diviser-et-joindre-les-tableaux-split-join)
12. [Aplatir les Tableaux : `flat()` et `flatMap()`](#aplatir-les-tableaux-flat-et-flatmap)
13. [Déstructuration de Tableaux](#déstructuration-de-tableaux)
14. [Utilisation de `some()` et `every()`](#utilisation-de-some-et-every)
15. [Travailler avec des Tableaux à partir d'Autres Structures de Données : `Array.from()` et `Array.isArray()`](#travailler-avec-des-tableaux-à-partir-d'autres-structures-de-données-arrayfrom-et-arrayisarray)
16. [Combiner les Tableaux : `concat()` et l'Opérateur Spread](#combiner-les-tableaux-concat-et-l'opérateur-spread)
17. [Comparaison de Tableaux : `Array.prototype.equals()`](#comparaison-de-tableaux-arrayprototypeequals)
18. [Performance des Méthodes de Tableaux et Optimisation](#performance-des-méthodes-de-tableaux-et-optimisation)

---

## Introduction aux Tableaux en JavaScript
Les tableaux sont des collections ordonnées de données et constituent une partie essentielle de la programmation JavaScript. Les tableaux peuvent stocker n'importe quel type de données et permettent diverses opérations pour manipuler leur contenu.

Exemple :
```javascript
let numbers = [1, 2, 3, 4, 5];
console.log(numbers[0]);  // 1
```

---

## Accéder et Modifier les Éléments d'un Tableau
Les éléments d'un tableau sont accessibles à l'aide d'indices, qui sont basés sur zéro. Vous pouvez modifier un élément directement en référençant son index.

Exemple :
```javascript
let fruits = ['apple', 'banana', 'cherry'];
fruits[1] = 'orange';  // Modification du deuxième élément
console.log(fruits);    // ["apple", "orange", "cherry"]
```

---

## Longueur du Tableau et Tableaux Multidimensionnels
La propriété `length` donne le nombre d'éléments dans un tableau. Les tableaux multidimensionnels sont des tableaux de tableaux.

Exemple :
```javascript
let arr = [1, 2, 3];
console.log(arr.length);  // 3

let matrix = [[1, 2], [3, 4], [5, 6]];
console.log(matrix[1][0]);  // 3
```

---

## Itérer à travers les Tableaux : `for`, `forEach()`, `map()`
Vous pouvez itérer à travers les tableaux en utilisant les boucles `for`, `forEach()` ou `map()`. `map()` crée un nouveau tableau basé sur le tableau original, tandis que `forEach()` ne renvoie rien.

Exemple :
```javascript
let numbers = [1, 2, 3];
numbers.forEach(num => console.log(num));  // 1, 2, 3

let squares = numbers.map(num => num * num);
console.log(squares);  // [1, 4, 9]
```

---

## Filtrer les Tableaux : `filter()`
La méthode `filter()` crée un nouveau tableau avec les éléments qui passent la condition fournie.

Exemple :
```javascript
let numbers = [1, 2, 3, 4, 5];
let evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);  // [2, 4]
```

---

## Réduire les Tableaux : `reduce()` et `reduceRight()`
La méthode `reduce()` traite chaque élément et accumule un seul résultat, tandis que `reduceRight()` fonctionne dans l'ordre inverse.

Exemple :
```javascript
let numbers = [1, 2, 3];
let sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum);  // 6
```

---

## Mapper les Tableaux : `map()` et `flatMap()`
La méthode `map()` crée un nouveau tableau en appliquant une fonction à chaque élément. `flatMap()` mappe et aplatit le résultat en un seul tableau.

Exemple :
```javascript
let numbers = [1, 2, 3];
let doubled = numbers.map(num => num * 2);
console.log(doubled);  // [2, 4, 6]

let nested = [[1, 2], [3, 4]];
let flat = nested.flatMap(arr => arr);
console.log(flat);  // [1, 2, 3, 4]
```

---

## Trier les Tableaux : `sort()` et `reverse()`
La méthode `sort()` trie les éléments d'un tableau sur place. `reverse()` inverse l'ordre des éléments.

Exemple :
```javascript
let numbers = [5, 3, 8, 1];
numbers.sort((a, b) => a - b);  // Tri ascendant
console.log(numbers);  // [1, 3, 5, 8]

numbers.reverse();
console.log(numbers);  // [8, 5, 3, 1]
```

---

## Trouver des Éléments : `find()`, `findIndex()`
La méthode `find()` renvoie le premier élément qui satisfait une condition. `findIndex()` renvoie l'index du premier élément qui satisfait la condition.

Exemple :
```javascript
let numbers = [1, 2, 3, 4];
let found = numbers.find(num => num > 2);
console.log(found);  // 3

let index = numbers.findIndex(num => num > 2);
console.log(index);  // 2
```

---

## Vérifier la Présence d'Éléments : `includes()`, `indexOf()`
La méthode `includes()` vérifie si un tableau contient un élément spécifique. `indexOf()` renvoie l'index de l'élément, ou `-1` s'il n'est pas trouvé.

Exemple :
```javascript
let numbers = [1, 2, 3];
console.log(numbers.includes(2));  // true
console.log(numbers.indexOf(3));   // 2
```

---

## Diviser et Joindre les Tableaux : `split()`, `join()`](#splitting-and-joining-arrays-split-join)
La méthode `split()` divise une chaîne de caractères en un tableau de sous-chaînes. La méthode `join()` combine les éléments d'un tableau en une chaîne de caractères.

Exemple :
```javascript
let str = "apple,banana,cherry";
let arr = str.split(",");
console.log(arr);  // ["apple", "banana", "cherry"]

let joined = arr.join(" - ");
console.log(joined);  // "apple - banana - cherry"
```

---

## Aplatir les Tableaux : `flat()` et `flatMap()`
La méthode `flat()` aplatit les tableaux imbriqués. `flatMap()` mappe chaque élément puis aplatit le résultat.

Exemple :
```javascript
let nested = [1, [2, 3], [4, 5]];
console.log(nested.flat());  // [1, 2, 3, 4, 5]

let result = nested.flatMap(arr => arr);
console.log(result);  // [1, 2, 3, 4, 5]
```

---

## Déstructuration de Tableaux
La déstructuration de tableaux vous permet de décompresser les valeurs des tableaux dans des variables individuelles.

Exemple :
```javascript
let arr = [1, 2, 3];
let [a, b] = arr;
console.log(a, b);  // 1 2
```

---

## Utilisation de `some()` et `every()`
La méthode `some()` vérifie si au moins un élément satisfait une condition, tandis que `every()` vérifie si tous les éléments répondent à la condition.

Exemple :
```javascript
let numbers = [1, 2, 3, 4];
console.log(numbers.some(num => num > 2));  // true
console.log(numbers.every(num => num > 0));  // true
```

---

## Travailler avec des Tableaux à partir d'Autres Structures de Données : `Array.from()` et `Array.isArray()`
`Array.from()` crée un tableau à partir d'objets de type tableau ou d'objets itérables. `Array.isArray()` vérifie si une variable est un tableau.

Exemple :
```javascript
let str = "hello";
let arrFromStr = Array.from(str);
console.log(arrFromStr);  // ["h", "e", "l", "l", "o"]

console.log(Array.isArray([1, 2, 3]));  // true
console.log(Array.isArray("hello"));    // false
```

---

## Combiner les Tableaux : `concat()` et l'Opérateur Spread
La méthode `concat()` combine deux ou plusieurs tableaux. L'opérateur spread (`...`) est une alternative qui peut également fusionner des tableaux.

Exemple :
```javascript
let arr1 = [1, 2];
let arr2 = [3, 4];
let combined = arr1.concat(arr2);
console.log(combined);  // [1, 2, 3, 4]

let spreadCombined = [...arr1, ...arr2];
console.log(spreadCombined);  // [1, 2, 3, 4]
```

---

## Comparaison de Tableaux : `Array.prototype.equals()`
La comparaison de tableaux nécessite une implémentation personnalisée, car JavaScript ne prend pas en charge nativement la comparaison approfondie de tableaux.

Exemple :
```javascript
Array.prototype.equals = function(arr) {
  return this.length === arr.length && this.every((value, index) => value === arr[index]);
};

let arr1 = [1, 2, 3];
let arr2 = [1, 2, 3];
console.log(arr1.equals(arr2));  // true
```

---

## Performance des Méthodes de Tableaux et Optimisation
Les méthodes de tableaux peuvent avoir des implications sur les performances, en particulier sur les grands ensembles de données. Soyez attentif à la complexité et utilisez des méthodes comme `map()`, `filter()` et `reduce()` de manière appropriée.

Exemple :
```javascript
let largeArray = new Array(1000000).fill(1);
console.time("map");
largeArray.map(num => num * 2);
console.timeEnd("map");  // temps pris pour l'opération map
```

---

## Conclusion

### Points Clés à Retenir :
1. JavaScript fournit un riche ensemble de méthodes de tableaux pour créer, manipuler et interroger les tableaux.
2. Les méthodes comme `map()`, `filter()` et `reduce()` sont essentielles pour la programmation de style fonctionnel.
3. La déstructuration de tableaux simplifie l'extraction d'éléments.
4. L'aplatissement et la combinaison de tableaux peuvent aider à gérer les données imbriquées.
5. Tenez compte des performances lorsque vous travaillez avec de grands tableaux et des opérations complexes.

### Exercice Pratique :
1. Écrivez une fonction pour trouver les éléments communs entre deux tableaux en utilisant `filter()`.
2. Implémentez une fonction qui inverse un tableau et supprime les doublons en utilisant `map()`, `filter()` et `reduce()`.
3. Créez un tableau imbriqué et aplatissez-le en utilisant `flat()` et `flatMap()`.
