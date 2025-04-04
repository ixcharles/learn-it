
# Modèles et Techniques Avancés en TypeScript

Ce cours explore les modèles avancés en TypeScript, en se concentrant sur la logique conditionnelle, les transformations de types et les capacités de métaprogrammation. Ces outils permettent un code sûr au niveau des types évolutif, expressif et réutilisable dans des applications complexes.

## Table des Matières

1. [Types Conditionnels et Mappés](#conditional-and-mapped-types)
2. [Types Utilitaires : Partial, Pick, Omit, etc.](#utility-types-partial-pick-omit-etc)
3. [Inférence Avancée et Manipulation de Types](#advanced-inference-and-type-manipulation)
4. [Décorateurs en TypeScript](#decorators-in-typescript)
5. [Mixins et Modèles de Composition](#mixins-and-composition-patterns)
6. [Types Littéraux Modèles et Mot-clé Infer](#template-literal-types-and-infer-keyword)

---

## Types Conditionnels et Mappés

Les types conditionnels permettent une ramification basée sur la logique de type, et les types mappés itèrent sur les propriétés pour les transformer.

### Exemple :

```typescript
type EstString<T> = T extends string ? true : false;

type PropsLectureSeule<T> = {
  readonly [K in keyof T]: T[K];
};

type Exemple = PropsLectureSeule<{ a: number; b: string }>;
// { readonly a: number; readonly b: string }
```

---

## Types Utilitaires : Partial, Pick, Omit, etc.

TypeScript inclut des assistants intégrés pour les transformations courantes comme rendre les propriétés optionnelles ou sélectionner des champs spécifiques.

### Exemples :

```typescript
type Utilisateur = { id: number; nom: string; email: string };

type UtilisateurPartiel = Partial<Utilisateur>;
type AperçuUtilisateur = Pick<Utilisateur, "id" | "nom">;
type SansEmail = Omit<Utilisateur, "email">;
```

---

## Inférence Avancée et Manipulation de Types

Le mot-clé `infer` extrait dynamiquement les types des structures, ce qui est utile dans les contraintes génériques et les types conditionnels.

### Exemple :

```typescript
type TypeRetour<T> = T extends (...args: any[]) => infer R ? R : never;

type Resultat = TypeRetour<() => number>;  // number
```

---

## Décorateurs en TypeScript

Les décorateurs sont des fonctions qui appliquent des métadonnées ou un comportement aux classes, méthodes, propriétés, etc. Nécessite `"experimentalDecorators": true` dans `tsconfig.json`.

### Exemple :

```typescript
function Log(target: any, key: string) {
  console.log(`Décoré : ${key}`);
}

class Personne {
  @Log
  direBonjour() {
    console.log("Bonjour");
  }
}
```

---

## Mixins et Modèles de Composition

Les mixins permettent de partager un comportement entre plusieurs classes sans héritage classique.

### Exemple :

```typescript
type Constructeur<T = {}> = new (...args: any[]) => T;

function Horodaté<TBase extends Constructeur>(Base: TBase) {
  return class extends Base {
    timestamp = Date.now();
  };
}

class Note {}
const NoteHorodatée = Horodaté(Note);
```

---

## Types Littéraux Modèles et Mot-clé Infer

Les types littéraux modèles permettent la construction dynamique de types de chaînes de caractères. Combinés avec `infer`, ils créent une logique de type puissante.

### Exemple :

```typescript
type NomEvenement = `on${Capitalize<string>}`;

type ExtraireValeur<T> = T extends { value: infer V } ? V : never;

type Test = ExtraireValeur<{ value: number }>;  // number
```

---

## Conclusion

### Points Clés à Retenir :
1. Les types conditionnels et mappés permettent des définitions de types flexibles et réutilisables.
2. Les types utilitaires simplifient les transformations d'objets courantes.
3. `infer` permet l'extraction des types internes pour une logique dynamique.
4. Les décorateurs fournissent des améliorations de métadonnées et de comportement en POO.
5. Les mixins et les modèles de composition aident à construire des classes modulaires et réutilisables.
6. Les types littéraux modèles apportent la manipulation de chaînes au moment de la compilation dans le système de types.

### Exercice Pratique :
1. Créez un type conditionnel `EstNombre<T>` qui renvoie `"oui"` si `T` est `number`, sinon `"non"`.
2. Écrivez un type mappé `Mutable<T>` qui supprime `readonly` de chaque propriété.
3. Utilisez un décorateur de classe pour enregistrer un message lorsqu'une classe est instanciée.
4. Implémentez un mixin qui ajoute une propriété `id` à n'importe quelle classe.
5. Utilisez un type littéral modèle pour définir des noms d'événements valides comme `onClick`, `onHover`.
