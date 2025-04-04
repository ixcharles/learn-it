
# Syntaxe de Base et Types de Données en TypeScript

Ce cours présente la syntaxe de base et les types de données fondamentaux en TypeScript. Il explique comment TypeScript améliore JavaScript grâce aux annotations de type, à l'inférence de type, et plus encore.

## Table des Matières

1. [Comprendre les Types de Base](#understanding-basic-types)
2. [Inférence de Type vs. Typage Explicite](#type-inference-vs-explicit-typing)
3. [Tuples et Tableaux en TypeScript](#tuples-and-arrays-in-typescript)
4. [Types Enumérés et Enums Constantes](#enum-types-and-const-enums)
5. [Alias de Type et Interfaces](#type-aliases-and-interfaces)
6. [Null et Undefined en TypeScript](#null-and-undefined-in-typescript)

---

## Comprendre les Types de Base

TypeScript prend en charge les types de données de base courants en JavaScript, mais avec l'avantage supplémentaire des annotations de type pour une meilleure sécurité.

- **number** : Représente les nombres entiers et à virgule flottante.
- **string** : Représente les données textuelles.
- **boolean** : Représente les valeurs vrai ou faux.
- **undefined** : Représente une variable non initialisée.
- **null** : Représente une valeur explicitement vide.

### Exemple :

```typescript
let age: number = 30;
let name: string = "John Doe";
let isActive: boolean = true;
```

---

## Inférence de Type vs. Typage Explicite

TypeScript peut inférer le type d'une variable à partir de sa valeur, ou vous pouvez définir explicitement le type.

- **Inférence de Type** : TypeScript infère automatiquement le type.
- **Typage Explicite** : Vous définissez manuellement le type.

### Exemple d'Inférence de Type :

```typescript
let count = 10;  // TypeScript infère que count est un nombre
```

### Exemple de Typage Explicite :

```typescript
let count: number = 10;  // Définit explicitement le type comme nombre
```

---

## Tuples et Tableaux en TypeScript

- **Tableaux** : Listes de valeurs du même type.
- **Tuples** : Tableaux de taille fixe avec des types spécifiques pour chaque élément.

### Tableaux :

```typescript
let numbers: number[] = [1, 2, 3];
```

### Tuples :

```typescript
let person: [string, number] = ["John", 30];
```

---

## Types Enumérés et Enums Constantes

- **Enums** : Une façon de définir un ensemble de constantes nommées.
- **Enums Constantes** : Une version des enums qui supprime le code d'exécution supplémentaire en les remplaçant par des valeurs en ligne lors de la compilation.

### Exemple d'Enum :

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let direction: Direction = Direction.Up;
```

### Exemple d'Enum Constante :

```typescript
const enum Direction {
  Up,
  Down,
  Left,
  Right
}

let direction: Direction = Direction.Up;
```

La différence principale est qu'avec `const enum`, le compilateur insère directement les valeurs, supprimant ainsi la surcharge d'exécution.

---

## Alias de Type et Interfaces

- **Alias de Type** : Crée un nouveau nom pour un type.
- **Interfaces** : Définissent la structure d'un objet (propriétés et méthodes).

### Alias de Type :

```typescript
type Point = { x: number, y: number };
let point: Point = { x: 5, y: 10 };
```

### Interfaces :

```typescript
interface Point {
  x: number;
  y: number;
}

let point: Point = { x: 5, y: 10 };
```

Les interfaces sont généralement utilisées pour les objets et peuvent être étendues, tandis que les alias de type sont plus flexibles (par exemple, pour les unions, les intersections, etc.).

---

## Null et Undefined en TypeScript

En TypeScript, `null` et `undefined` sont des types distincts, et leur utilisation peut être contrôlée à l'aide de vérifications strictes de nullité.

- **undefined** : Indique une variable qui a été déclarée mais à laquelle aucune valeur n'a été attribuée.
- **null** : Représente une variable qui a été explicitement définie sur "aucune valeur".

### Exemple :

```typescript
let uninitialized: undefined = undefined;
let noValue: null = null;
```

Pour activer les vérifications strictes de nullité et rendre ces types plus prévisibles, vous pouvez utiliser l'indicateur `--strictNullChecks` dans `tsconfig.json`.

---

## Conclusion

### Points Clés à Retenir :
1. TypeScript offre une sécurité de type améliorée avec des types de base comme `number`, `string`, `boolean`, `null` et `undefined`.
2. L'inférence de type permet à TypeScript de déterminer automatiquement le type, mais le typage explicite assure des garanties plus fortes.
3. Les tuples et les tableaux aident à gérer les listes, les tuples offrant des tableaux de longueur fixe et de types spécifiques.
4. Les Enums et les Enums Constantes simplifient la gestion des ensembles de constantes avec ou sans surcharge d'exécution.
5. Les alias de type et les interfaces définissent des types personnalisés pour les objets et les structures, améliorant la lisibilité et la maintenabilité du code.

### Exercice Pratique :
1. Créez un type `Personne` en utilisant à la fois un `alias de type` et une `interface`. Utilisez le type `Personne` dans un tableau de plusieurs personnes.
2. Créez un simple enum pour un feu de circulation (`Rouge`, `Jaune`, `Vert`) et utilisez-le dans une fonction pour simuler les changements de feux de circulation.
3. Déclarez des variables avec des types explicites et laissez TypeScript inférer les types, puis comparez les résultats.
