
# Génériques en TypeScript

Ce cours explore en profondeur les génériques de TypeScript, une fonctionnalité puissante qui vous permet d'écrire du code réutilisable et sûr au niveau des types. Vous apprendrez à utiliser les génériques dans les fonctions, les interfaces, les classes et les modèles avancés pour rendre votre code plus flexible et robuste.

## Table des Matières

1. [Introduction aux Génériques](#introduction-to-generics)
2. [Fonctions Génériques et Contraintes](#generic-functions-and-constraints)
3. [Interfaces et Classes Génériques](#generic-interfaces-and-classes)
4. [Utilisation de Plusieurs Paramètres de Type](#using-multiple-type-parameters)
5. [Modèles Génériques Avancés : Types par Défaut et Types Conditionnels](#advanced-generic-patterns-default-types-and-conditional-types)
6. [Inférence de Type avec les Génériques](#type-inference-with-generics)

---

## Introduction aux Génériques

Les génériques offrent un moyen de définir des composants réutilisables qui fonctionnent avec une variété de types sans perdre la sécurité de type.

### Exemple :

```typescript
function identity<T>(value: T): T {
  return value;
}

const numberResult = identity<number>(42);
const stringResult = identity("hello"); // inféré comme string
```

---

## Fonctions Génériques et Contraintes

Vous pouvez contraindre les types génériques pour vous assurer qu'ils répondent à certains critères en utilisant `extends`.

### Exemple (avec contrainte) :

```typescript
function getLength<T extends { length: number }>(value: T): number {
  return value.length;
}

getLength("hello"); // valide
getLength([1, 2, 3]); // valide
// getLength(123); // erreur : number n'a pas de propriété length
```

---

## Interfaces et Classes Génériques

Les génériques peuvent être appliqués aux interfaces et aux classes pour définir des structures réutilisables.

### Interface Générique :

```typescript
interface Box<T> {
  value: T;
}

const stringBox: Box<string> = { value: "TypeScript" };
```

### Classe Générique :

```typescript
class Container<T> {
  private content: T;

  constructor(value: T) {
    this.content = value;
  }

  get(): T {
    return this.content;
  }
}

const numberContainer = new Container<number>(123);
```

---

## Utilisation de Plusieurs Paramètres de Type

Vous pouvez définir des fonctions, des classes ou des interfaces avec plus d'un paramètre de type.

### Exemple :

```typescript
function merge<T, U>(a: T, b: U): T & U {
  return { ...a, ...b };
}

const merged = merge({ name: "Alice" }, { age: 30 });
// merged est inféré comme { name: string; age: number }
```

---

## Modèles Génériques Avancés : Types par Défaut et Types Conditionnels

Vous pouvez attribuer des types par défaut et utiliser une logique conditionnelle dans les types génériques.

### Paramètres de Type par Défaut :

```typescript
type ApiResponse<T = any> = {
  data: T;
  error?: string;
};

const response: ApiResponse<string> = { data: "Success" };
```

### Types Conditionnels :

```typescript
type IsArray<T> = T extends any[] ? "array" : "not array";

type A = IsArray<number[]>; // "array"
type B = IsArray<number>;   // "not array"
```

---

## Inférence de Type avec les Génériques

TypeScript peut souvent inférer les types génériques à partir des arguments fournis, réduisant ainsi le besoin de les annoter explicitement.

### Exemple :

```typescript
function wrap<T>(value: T): { value: T } {
  return { value };
}

const wrapped = wrap("inferred"); // inféré comme string
```

Vous pouvez toujours fournir des types explicitement lorsque cela est nécessaire :

```typescript
const explicit = wrap<number>(42);
```

---

## Conclusion

### Points Clés à Retenir :
1. Les génériques permettent de créer des composants réutilisables et sûrs au niveau des types qui fonctionnent avec plusieurs types.
2. Vous pouvez contraindre les types génériques pour garantir une certaine structure ou un certain comportement.
3. Les interfaces et les classes peuvent être génériques, ce qui permet une modélisation de données puissante.
4. Plusieurs paramètres de type permettent de combiner et de fusionner différentes valeurs de type.
5. Les fonctionnalités génériques avancées incluent les types par défaut, les types conditionnels et les mécanismes d'inférence.

### Exercice Pratique :
1. Écrivez une fonction générique `premierElement<T>` qui renvoie le premier élément d'un tableau de type `T[]`.
2. Créez une interface générique `Resultat<T>` avec les propriétés `succès: boolean` et `données: T | null`.
3. Utilisez un type conditionnel pour créer `EstString<T>` qui se résout en `true` si `T` est une `string`, sinon `false`. Essayez-le avec plusieurs types.
