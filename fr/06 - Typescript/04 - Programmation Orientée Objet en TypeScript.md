
# Programmation Orientée Objet en TypeScript

Ce cours couvre les concepts essentiels de la Programmation Orientée Objet (POO) en TypeScript, y compris les classes, les interfaces, l'héritage, les modificateurs d'accès, les membres statiques, les classes abstraites, et plus encore. Vous apprendrez à tirer parti du système de types de TypeScript pour concevoir des applications orientées objet maintenables et évolutives.

## Table des Matières

1. [Classes et Interfaces](#classes-and-interfaces)
2. [Héritage et Surcharge de Méthodes](#inheritance-and-method-overriding)
3. [Modificateurs d'Accès (public, private, protected)](#access-modifiers-public-private-protected)
4. [Membres et Méthodes Statiques](#static-members-and-methods)
5. [Classes et Méthodes Abstraites](#abstract-classes-and-methods)
6. [Interfaces vs. Alias de Type pour la POO](#interfaces-vs-type-aliases-for-oop)

---

## Classes et Interfaces

- **Classes** : Plans pour créer des objets qui regroupent des données et des méthodes.
- **Interfaces** : Contrats qui définissent la structure d'un objet sans implémentation.

### Exemple de Classe :

```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): string {
    return `Bonjour, je m'appelle ${this.name} et j'ai ${this.age} ans.`;
  }
}

const person = new Person("Alice", 30);
console.log(person.greet());
```

### Exemple d'Interface :

```typescript
interface Greetable {
  name: string;
  greet(): string;
}

class Person implements Greetable {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  greet(): string {
    return `Bonjour, je m'appelle ${this.name}.`;
  }
}
```

---

## Héritage et Surcharge de Méthodes

L'héritage permet à une classe d'hériter des propriétés et des méthodes d'une autre, favorisant la réutilisation du code. La surcharge de méthodes permet à une sous-classe de fournir sa propre implémentation d'une méthode définie dans la classe parente.

### Exemple :

```typescript
class Animal {
  name: string;
  
  constructor(name: string) {
    this.name = name;
  }

  speak(): string {
    return `${this.name} fait un bruit.`;
  }
}

class Dog extends Animal {
  speak(): string {
    return `${this.name} aboie !`;
  }
}

const dog = new Dog("Buddy");
console.log(dog.speak());  // "Buddy aboie !"
```

---

## Modificateurs d'Accès (public, private, protected)

Les modificateurs d'accès contrôlent la visibilité et l'accessibilité des membres de la classe (propriétés et méthodes). TypeScript prend en charge les modificateurs d'accès `public`, `private` et `protected`.

- **public** : Les membres sont accessibles de n'importe où.
- **private** : Les membres ne sont accessibles qu'à l'intérieur de la classe elle-même.
- **protected** : Les membres sont accessibles à l'intérieur de la classe et de ses sous-classes.

### Exemple :

```typescript
class Person {
  public name: string;
  private age: number;
  protected address: string;

  constructor(name: string, age: number, address: string) {
    this.name = name;
    this.age = age;
    this.address = address;
  }

  getAge(): number {
    return this.age;
  }
}

const person = new Person("Alice", 30, "123 Main St");
console.log(person.name);  // Accessible
console.log(person.getAge());  // Accessible via une méthode publique
// console.log(person.age);  // Erreur : 'age' est privé
```

---

## Membres et Méthodes Statiques

Les membres statiques appartiennent à la classe elle-même, et non aux instances de la classe. Ils peuvent être consultés sans créer d'instance de la classe.

### Exemple :

```typescript
class MathUtility {
  static PI: number = 3.14;

  static area(radius: number): number {
    return MathUtility.PI * radius * radius;
  }
}

console.log(MathUtility.area(5));  // Accès à une méthode statique sans instance
```

---

## Classes et Méthodes Abstraites

- **Classes Abstraites** : Classes qui ne peuvent pas être instanciées directement mais qui peuvent être sous-classées. Elles peuvent contenir des méthodes abstraites qui doivent être implémentées par les sous-classes.
- **Méthodes Abstraites** : Méthodes déclarées dans des classes abstraites mais qui n'ont pas d'implémentation, forçant les sous-classes à fournir leur propre implémentation.

### Exemple :

```typescript
abstract class Shape {
  abstract area(): number;  // Méthode abstraite

  printArea(): void {
    console.log(`L'aire est de : ${this.area()}`);
  }
}

class Circle extends Shape {
  radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}

const circle = new Circle(5);
circle.printArea();  // Affiche : L'aire est de : 78.53981633974483
```

---

## Interfaces vs. Alias de Type pour la POO

- **Interfaces** : Principalement utilisées pour définir la structure des objets et des classes. Elles peuvent être étendues, ce qui les rend idéales pour la POO.
- **Alias de Type** : Plus flexibles que les interfaces, permettant de définir des unions, des intersections et d'autres types complexes.

### Exemple d'Interface en POO :

```typescript
interface Animal {
  name: string;
  sound(): string;
}

class Dog implements Animal {
  name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  sound(): string {
    return `${this.name} aboie.`;
  }
}
```

### Exemple d'Alias de Type en POO :

```typescript
type Animal = {
  name: string;
  sound(): string;
};

class Dog implements Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  sound(): string {
    return `${this.name} aboie.`;
  }
}
```

Dans la plupart des scénarios de POO, les interfaces sont généralement préférées, mais les alias de type peuvent être utiles dans des compositions de types plus complexes.

---

## Conclusion

### Points Clés à Retenir :
1. TypeScript prend en charge les classes et les interfaces pour implémenter les principes de la Programmation Orientée Objet, les classes définissant les plans des objets et les interfaces spécifiant les contrats.
2. L'héritage permet la réutilisation du code, et la surcharge de méthodes permet aux sous-classes de fournir des implémentations personnalisées.
3. Les modificateurs d'accès (`public`, `private`, `protected`) contrôlent la visibilité et aident à encapsuler la logique de la classe.
4. Les membres statiques sont accessibles sur la classe elle-même sans nécessiter d'instance.
5. Les classes et méthodes abstraites imposent une structure dans les sous-classes, s'assurant qu'elles fournissent des implémentations spécifiques.
6. Les interfaces sont mieux adaptées à la conception POO, tandis que les alias de type offrent plus de flexibilité pour les types complexes.

### Exercice Pratique :
1. Créez une classe de base `Forme` avec une méthode abstraite `aire()` et sous-classez-la en classes `Rectangle` et `Cercle`.
2. Définissez une interface `Jouable` avec une méthode `jouer()`, et implémentez-la dans deux classes, `Guitare` et `Piano`.
3. Expérimentez avec les méthodes statiques en créant une classe utilitaire pour la gestion des calculs mathématiques (par exemple, aire du cercle, volume de la sphère).
