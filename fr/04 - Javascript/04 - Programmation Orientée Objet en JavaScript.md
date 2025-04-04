
# Programmation Orientée Objet en JavaScript

JavaScript est un langage orienté objet, et la compréhension des concepts de la programmation orientée objet (POO) est essentielle pour écrire du code efficace, réutilisable et maintenable. Ce cours couvre les principes fondamentaux de la POO en JavaScript, y compris les objets, l'héritage et les fonctionnalités ES6.

## Table des Matières
1. [Objets : Création, Propriétés et Méthodes](#objets-création-propriétés-et-méthodes)
2. [Héritage Prototypal](#héritage-prototypal)
3. [Constructeurs et le Mot-Clé `new`](#constructeurs-et-le-mot-clé-new)
4. [Classes ES6 et Héritage](#classes-es6-et-héritage)
5. [Méthodes et Propriétés Statiques](#méthodes-et-propriétés-statiques)
6. [Méthodes Getter et Setter](#méthodes-getter-et-setter)
7. [Déstructuration d'Objets](#déstructuration-d'objets)
8. [`Object.freeze` et Immuabilité](#objectfreeze-et-immuabilité)
9. [Le Mot-Clé `this` et Son Contexte](#le-mot-clé-this-et-son-contexte)

---

## Objets : Création, Propriétés et Méthodes
Les objets sont des paires clé-valeur en JavaScript. Ils peuvent contenir divers types de données, y compris des tableaux, des fonctions et d'autres objets.

Exemple :
```javascript
let car = {
  make: 'Toyota',
  model: 'Corolla',
  year: 2020,
  startEngine: function() { console.log("Engine started!"); }
};

console.log(car.make);  // Toyota
car.startEngine();  // Engine started!
```

---

## Héritage Prototypal
En JavaScript, les objets peuvent hériter des propriétés et des méthodes d'autres objets via la chaîne de prototypes.

Exemple :
```javascript
let animal = { species: 'dog' };
let dog = Object.create(animal);
dog.bark = function() { console.log("Woof!"); };

console.log(dog.species);  // dog (hérité de animal)
dog.bark();  // Woof!
```

---

## Constructeurs et le Mot-Clé `new`
Les constructeurs sont des fonctions spéciales utilisées pour créer des objets. Le mot-clé `new` instancie un nouvel objet basé sur la fonction constructeur.

Exemple :
```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

let john = new Person('John', 25);
console.log(john.name);  // John
```

---

## Classes ES6 et Héritage
ES6 introduit la syntaxe `class`, qui simplifie la création d'objets et l'héritage.

Exemple :
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);  // Appelle le constructeur de la classe parent
  }

  speak() {
    console.log(`${this.name} barks`);
  }
}

let dog = new Dog('Buddy');
dog.speak();  // Buddy barks
```

---

## Méthodes et Propriétés Statiques
Les méthodes et propriétés statiques sont définies sur la classe elle-même, et non sur les instances de la classe.

Exemple :
```javascript
class MathUtil {
  static add(a, b) {
    return a + b;
  }
}

console.log(MathUtil.add(2, 3));  // 5
```

---

## Méthodes Getter et Setter
Les getters et les setters vous permettent de définir un comportement personnalisé pour la lecture et la définition des propriétés d'un objet.

Exemple :
```javascript
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  get area() {
    return Math.PI * this._radius * this._radius;
  }

  set radius(value) {
    if (value > 0) {
      this._radius = value;
    }
  }
}

let circle = new Circle(5);
console.log(circle.area);  // 78.53981633974483
circle.radius = 10;
console.log(circle.area);  // 314.1592653589793
```

---

## Déstructuration d'Objets
La déstructuration d'objets vous permet d'extraire des valeurs d'un objet et de les affecter à des variables de manière concise.

Exemple :
```javascript
let person = { name: 'Alice', age: 30 };
let { name, age } = person;
console.log(name);  // Alice
console.log(age);   // 30
```

---

## `Object.freeze` et Immuabilité
La méthode `Object.freeze()` empêche l'ajout de nouvelles propriétés à un objet et rend les propriétés existantes immuables.

Exemple :
```javascript
let user = { name: 'Alice' };
Object.freeze(user);

user.name = 'Bob';  // Ceci ne fonctionnera pas
console.log(user.name);  // Alice
```

---

## Le Mot-Clé `this` et Son Contexte
Le mot-clé `this` fait référence à l'objet qui appelle une fonction. Sa valeur peut changer en fonction du contexte dans lequel la fonction est appelée.

Exemple :
```javascript
let person = {
  name: 'Alice',
  greet: function() {
    console.log(`Hello, ${this.name}`);
  }
};

person.greet();  // Hello, Alice

let greetFunc = person.greet;
greetFunc();  // Hello, undefined (contexte perdu)
```

---

## Conclusion

### Points Clés à Retenir :
1. Les objets JavaScript sont des collections de paires clé-valeur qui peuvent contenir d'autres objets, des fonctions et des tableaux.
2. L'héritage prototypal permet aux objets d'hériter des propriétés et des méthodes d'autres objets.
3. Les classes ES6 simplifient la création d'objets et l'héritage, rendant le code plus lisible.
4. Les méthodes statiques appartiennent à la classe elle-même, et non à ses instances.
5. La valeur du mot-clé `this` est déterminée par le contexte d'invocation de la fonction.

### Exercice Pratique :
1. Créez une classe `Book` avec des propriétés telles que le titre, l'auteur et le nombre de pages. Ajoutez des méthodes pour obtenir et définir ces propriétés à l'aide de getters et de setters.
2. Utilisez la déstructuration d'objets pour extraire les propriétés d'un objet et les afficher dans la console.
3. Créez une fonction pour cloner un objet et le geler, en vous assurant qu'il ne peut pas être modifié.
