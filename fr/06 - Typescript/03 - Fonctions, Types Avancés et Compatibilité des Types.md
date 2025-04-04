
# Fonctions, Types Avancés et Compatibilité des Types

Ce cours couvre les concepts avancés de TypeScript, y compris les déclarations de fonctions, les paramètres optionnels, la surcharge de fonctions, les types avancés tels que l'union et l'intersection, et la compatibilité des types. Vous apprendrez également les assertions de type et les gardes de type pour une sécurité de type améliorée.

## Table des Matières

1. [Déclaration de Fonction, Expression et Fonctions Fléchées](#function-declaration-expression-and-arrow-functions)
2. [Paramètres Optionnels et Par Défaut](#optional-and-default-parameters)
3. [Surcharge de Fonctions en TypeScript](#function-overloading-in-typescript)
4. [Types Avancés : Union, Intersection, Littéraux et Conditionnels](#advanced-types-union-intersection-literal-and-conditional-types)
5. [Compatibilité des Types et Sous-typage Structurel](#type-compatibility-and-structural-subtyping)
6. [Assertion de Type et Gardes de Type](#type-assertion-and-type-guards)

---

## Déclaration de Fonction, Expression et Fonctions Fléchées

- **Déclaration de Fonction** : Déclaration de fonction standard.
- **Expression de Fonction** : Fonctions assignées à des variables.
- **Fonctions Fléchées** : Syntaxe plus courte pour écrire des fonctions avec liaison lexicale de `this`.

### Déclaration de Fonction :

```typescript
function add(x: number, y: number): number {
  return x + y;
}
```

### Expression de Fonction :

```typescript
const add = function(x: number, y: number): number {
  return x + y;
};
```

### Fonction Fléchée :

```typescript
const add = (x: number, y: number): number => x + y;
```

---

## Paramètres Optionnels et Par Défaut

- **Paramètres Optionnels** : Paramètres qui peuvent être omis lors des appels de fonction.
- **Paramètres Par Défaut** : Paramètres qui ont une valeur par défaut si aucune n'est fournie.

### Paramètres Optionnels :

```typescript
function greet(name: string, age?: number): string {
  return `Bonjour, ${name}${age ? ', Âge : ' + age : ''}`;
}
```

### Paramètres Par Défaut :

```typescript
function greet(name: string, age: number = 30): string {
  return `Bonjour, ${name}, Âge : ${age}`;
}
```

---

## Surcharge de Fonctions en TypeScript

La surcharge de fonctions vous permet de définir plusieurs signatures de fonction pour une seule fonction, offrant une flexibilité basée sur différents types d'entrée.

### Exemple :

```typescript
function greet(name: string): string;
function greet(name: string, age: number): string;
function greet(name: string, age?: number): string {
  return age ? `Bonjour, ${name}, Âge : ${age}` : `Bonjour, ${name}`;
}

greet("Alice");
greet("Bob", 30);
```

---

## Types Avancés : Union, Intersection, Littéraux et Conditionnels

- **Types Union** : Une variable peut contenir l'un de plusieurs types.
- **Types Intersection** : Combine plusieurs types en un seul.
- **Types Littéraux** : Restreint une variable à une valeur spécifique.
- **Types Conditionnels** : Types basés sur une condition.

### Types Union :

```typescript
let value: string | number = "Bonjour";
value = 10;
```

### Types Intersection :

```typescript
interface Nom {
  nom: string;
}

interface Age {
  age: number;
}

type Personne = Nom & Age;

let personne: Personne = { nom: "Alice", age: 25 };
```

### Types Littéraux :

```typescript
let status: "succès" | "erreur" = "succès";
```

### Types Conditionnels :

```typescript
type EstString<T> = T extends string ? "Oui" : "Non";
type Resultat = EstString<string>;  // Resultat est "Oui"
```

---

## Compatibilité des Types et Sous-typage Structurel

La compatibilité des types en TypeScript est basée sur le typage structurel, ce qui signifie que les types sont compatibles si leurs structures (c'est-à-dire les propriétés et les méthodes) correspondent, et non nécessairement leurs noms.

### Exemple :

```typescript
interface Animal {
  nom: string;
  son: string;
}

interface Chien extends Animal {
  race: string;
}

let chien: Chien = { nom: "Buddy", son: "Wouf", race: "Golden Retriever" };
let animal: Animal = chien;  // Valide en raison du sous-typage structurel
```

---

## Assertion de Type et Gardes de Type

- **Assertion de Type** : Indique à TypeScript de traiter une variable comme un type spécifique.
- **Gardes de Type** : Fonctions ou conditions utilisées pour restreindre le type d'une variable.

### Assertion de Type :

```typescript
let value: any = "Bonjour, TypeScript !";
let longueurChaine: number = (value as string).length;
```

### Gardes de Type :

```typescript
function estString(value: any): value is string {
  return typeof value === "string";
}

let value: string | number = "Bonjour";
if (estString(value)) {
  console.log(value.length);  // TypeScript sait que value est une chaîne ici
}
```

---

## Conclusion

### Points Clés à Retenir :
1. TypeScript prend en charge plusieurs façons de déclarer des fonctions : déclaration, expression et fonctions fléchées.
2. Vous pouvez utiliser des paramètres optionnels et par défaut pour rendre les fonctions plus flexibles.
3. La surcharge de fonctions vous permet de définir plusieurs signatures de fonction pour la même fonction.
4. Les types avancés tels que l'union, l'intersection, les littéraux et les conditionnels améliorent la flexibilité et la sécurité de TypeScript.
5. La compatibilité des types est basée sur le typage structurel, et les assertions et les gardes de type aident à garantir une gestion précise des types.

### Exercice Pratique :
1. Écrivez une fonction avec des paramètres à la fois optionnels et par défaut. Créez quelques cas de test pour valider son comportement.
2. Créez un type union pour différents rôles d'utilisateur (`"admin" | "utilisateur" | "invité"`) et utilisez-le dans une fonction qui effectue différentes actions en fonction du rôle.
3. Implémentez une fonction de garde de type pour vérifier si une valeur donnée est un tableau et accéder en toute sécurité aux méthodes de tableau.
