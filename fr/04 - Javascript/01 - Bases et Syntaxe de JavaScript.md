
# Bases et Syntaxe de JavaScript

JavaScript est le langage de programmation fondamental pour le développement web, utilisé pour créer des sites web interactifs et dynamiques. Ce cours couvre la syntaxe et les concepts essentiels nécessaires pour démarrer avec JavaScript.

## Table des Matières
1. [Introduction à JavaScript](#introduction-à-javascript)
2. [Variables et Types de Données](#variables-et-types-de-données)
3. [Opérateurs et Expressions](#opérateurs-et-expressions)
4. [Flux de Contrôle : if, else, switch](#flux-de-contrôle-if-else-switch)
5. [Boucles : for, while, do-while](#boucles-for-while-do-while)
6. [Fonctions : Déclaration, Expression, Fonctions Fléchées](#fonctions-déclaration-expression-fonctions-fléchées)
7. [Portée et Hoisting](#portée-et-hoisting)
8. [Gestion des Erreurs : try, catch, throw](#gestion-des-erreurs-try-catch-throw)
9. [Débogage avec la console et les DevTools](#débogage-avec-la-console-et-les-devtools)

---

## Introduction à JavaScript
JavaScript est un langage de programmation polyvalent de haut niveau utilisé pour créer des pages web dynamiques. Il permet l'interaction avec les éléments HTML, rendant les sites web plus interactifs.

Exemple :
```javascript
console.log("Hello, World!");
```

---

## Variables et Types de Données
Les variables stockent des valeurs de données. JavaScript possède plusieurs types de données, notamment les nombres, les chaînes de caractères, les booléens et les objets.

Exemple :
```javascript
let name = "John";   // String
let age = 30;        // Number
let isAdult = true;  // Boolean
```

---

## Opérateurs et Expressions
Les opérateurs effectuent des opérations sur des variables et des valeurs, telles que l'arithmétique ou la comparaison. Les expressions sont des combinaisons de valeurs, de variables et d'opérateurs qui donnent un résultat.

Exemple :
```javascript
let sum = 10 + 5;    // Arithmetic operator
let isEqual = (10 == 10); // Comparison operator
```

---

## Flux de Contrôle : if, else, switch
Le flux de contrôle détermine la direction de l'exécution du programme. `if`, `else` et `switch` sont des instructions conditionnelles utilisées pour contrôler le flux.

Exemple :
```javascript
if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

---

## Boucles : for, while, do-while
Les boucles sont utilisées pour exécuter du code de manière répétée tant qu'une condition est vraie. Les types courants sont `for`, `while` et `do-while`.

Exemple :
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

---

## Fonctions : Déclaration, Expression, Fonctions Fléchées
Les fonctions sont des blocs de code réutilisables. Elles peuvent être déclarées, définies comme des expressions ou écrites avec la syntaxe des fonctions fléchées.

Exemple :
```javascript
// Function Declaration
function greet(name) {
    console.log("Hello, " + name);
}

// Function Expression
const square = function(x) {
    return x * x;
};

// Arrow Function
const add = (a, b) => a + b;
```

---

## Portée et Hoisting
La portée définit la visibilité des variables. Le hoisting fait référence au comportement de JavaScript qui consiste à déplacer les déclarations en haut de leur portée.

Exemple :
```javascript
console.log(a); // undefined due to hoisting
var a = 10;
```

---

## Gestion des Erreurs : try, catch, throw
La gestion des erreurs permet aux développeurs de gérer les erreurs d'exécution à l'aide de `try`, `catch` et `throw` pour traiter les exceptions en toute sécurité.

Exemple :
```javascript
try {
    let result = 10 / 0;
    if (result === Infinity) throw "Cannot divide by zero";
} catch (error) {
    console.log(error);
}
```

---

## Débogage avec la console et les DevTools
`console.log()` aide à afficher les sorties pour le débogage. Les DevTools du navigateur fournissent des outils avancés tels que les points d'arrêt et le débogage pas à pas pour examiner le flux du code.

Exemple :
```javascript
let x = 5;
console.log("Value of x:", x);  // Debugging with console.log
```

---

## Conclusion

### Points Clés à Retenir :
1. JavaScript est crucial pour la création de pages web interactives.
2. Les variables, les types de données et les opérateurs sont fondamentaux pour la programmation en JavaScript.
3. Le flux de contrôle et les boucles permettent une exécution flexible du programme.
4. Les fonctions permettent la réutilisation et l'organisation du code.
5. Les outils de débogage et la gestion des erreurs améliorent la fiabilité du code.

### Exercice Pratique :
1. Créez un programme JavaScript simple qui :
   - Prend l'âge d'un utilisateur comme entrée.
   - Vérifie si l'utilisateur est majeur ou mineur à l'aide d'une instruction `if`.
   - Affiche un message dans la console à l'aide de `console.log()`.
2. Expérimentez avec différents types de boucles (`for`, `while`, `do-while`) pour afficher les nombres de 1 à 10.
