
# Modules et Espaces de Noms en TypeScript

Ce cours se concentre sur la manière d'organiser et de modulariser le code en TypeScript à l'aide des modules ES et des espaces de noms. Vous apprendrez également à travailler avec des bibliothèques tierces et à explorer des concepts avancés comme la fusion de déclarations.

## Table des Matières

1. [Travailler avec les Modules ES en TypeScript](#working-with-es-modules-in-typescript)
2. [Instructions Import et Export](#import-and-export-statements)
3. [Espace de Noms vs Module : Différences Clés](#namespace-vs-module-key-differences)
4. [Fusion de Déclarations](#declaration-merging)
5. [Utilisation de TypeScript avec des Bibliothèques Tierces (DefinitelyTyped, etc.)](#using-typescript-with-third-party-libraries-definitelytyped-etc)

---

## Travailler avec les Modules ES en TypeScript

TypeScript prend en charge les modules ECMAScript (`import`/`export`) pour diviser le code sur plusieurs fichiers et promouvoir la réutilisabilité et l'organisation.

### Exemple :

```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

// main.ts
import { add } from './math';

console.log(add(2, 3));
```

Assurez-vous que `tsconfig.json` inclut `"module": "esnext"` ou `"module": "commonjs"` selon votre environnement.

---

## Instructions Import et Export

Les modules peuvent exporter des valeurs (fonctions, classes, objets) en utilisant des exportations nommées ou par défaut, et celles-ci peuvent être importées ailleurs.

### Exportation Nommée :

```typescript
// utils.ts
export const PI = 3.14;

// app.ts
import { PI } from './utils';
```

### Exportation par Défaut :

```typescript
// logger.ts
export default function log(msg: string): void {
  console.log(msg);
}

// app.ts
import log from './logger';
```

---

## Espace de Noms vs Module : Différences Clés

- **Modules** : Basés sur des fichiers ; dépendent de `import`/`export`. Utilisés dans les bases de code modernes.
- **Espaces de Noms** : Modèle de module interne utilisant le mot-clé `namespace` ; utile lorsque vous n'utilisez pas de chargeur de modules.

### Exemple d'Espace de Noms :

```typescript
namespace Utils {
  export function greet(name: string): string {
    return `Bonjour, ${name}`;
  }
}

console.log(Utils.greet("Alice"));
```

**Note :** Évitez les espaces de noms lorsque vous utilisez des modules ES — préférez la syntaxe des modules pour l'évolutivité.

---

## Fusion de Déclarations

TypeScript permet aux interfaces et aux espaces de noms portant le même nom de fusionner en une seule déclaration, ce qui améliore la flexibilité.

### Exemple :

```typescript
interface User {
  name: string;
}

namespace User {
  export function create(name: string): User {
    return { name };
  }
}

const newUser = User.create("Bob");
```

---

## Utilisation de TypeScript avec des Bibliothèques Tierces (DefinitelyTyped, etc.)

Pour les bibliothèques sans types intégrés, TypeScript utilise les packages **@types/** de [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

### Installation et Utilisation :

```bash
npm install lodash
npm install --save-dev @types/lodash
```

### Exemple :

```typescript
import _ from 'lodash';

const nums = [1, 2, 3];
console.log(_.reverse(nums));  // [3, 2, 1]
```

Si aucun type n'est disponible, vous pouvez utiliser un fichier `*.d.ts` avec des déclarations personnalisées.

---

## Conclusion

### Points Clés à Retenir :
1. Utilisez les modules ES (`import`/`export`) pour structurer les projets TypeScript modernes.
2. Les exportations nommées et par défaut offrent des moyens flexibles d'exposer et d'utiliser du code dans différents fichiers.
3. Évitez `namespace` au profit des modules, sauf si vous travaillez dans un environnement sans module.
4. La fusion de déclarations améliore la flexibilité, en particulier avec les interfaces et les espaces de noms.
5. TypeScript s'intègre facilement aux bibliothèques JS tierces en utilisant `@types`.

### Exercice Pratique :
1. Créez deux fichiers distincts et exportez une fonction de l'un, en l'important et en l'utilisant dans l'autre.
2. Définissez un espace de noms avec une fonction et une interface, puis fusionnez-les.
3. Installez et utilisez une bibliothèque tierce comme `lodash` et utilisez TypeScript pour appeler l'une de ses méthodes avec la sécurité de type.
