
# Maîtrise de TypeScript dans les Projets Next.js

Une exploration approfondie des concepts avancés de TypeScript pour la construction d'applications évolutives et type-safe dans Next.js, se concentrant sur les motifs avancés, la gestion d'état et l'intégration d'API.

---

## Table des Matières

- [TypeScript Avancé dans React](#typescript-avancé-dans-react)
  - [Inférance de Type](#inférence-de-type)
  - [Énumérations, Unions, Intersections](#énumérations-unions-intersections)
  - [Types Utilitaires](#types-utilitaires)
- [Routes API Typées](#routes-api-typées)
  - [Création de Routes API](#création-de-routes-api)
  - [Typage de la Requête et de la Réponse](#typage-de-la-requête-et-de-la-réponse)
- [Types de Composants Réutilisables](#types-de-composants-réutilisables)
  - [Définitions de Types Personnalisées](#définitions-de-types-personnalisées)
  - [Composants Polymorphes](#composants-polymorphes)
- [Gestion des Formulaires et des Événements](#gestion-des-formulaires-et-des-événements)
  - [Typage des Éléments de Formulaire et des Événements](#typage-des-éléments-de-formulaire-et-des-événements)
  - [Entrées Contrôlées vs Non Contrôlées](#entrées-contrôlées-vs-non-contrôlées)
- [Gestion de l'État avec TypeScript](#gestion-de-létat-avec-typescript)
  - [`useState` et `useReducer` avec les Types](#usestate-et-usereducer-avec-les-types)
  - [`useContext` avec des Types Personnalisés](#usecontext-avec-des-types-personnalisés)

---

## TypeScript Avancé dans React

### Inférence de Type
TypeScript infère automatiquement les types pour les variables, les valeurs de retour des fonctions et les paramètres.

**Exemple:**
```ts
let name = "John";  // inféré comme string
const sum = (a: number, b: number) => a + b;  // type de retour inféré : number
```

### Énumérations, Unions, Intersections
Les énumérations définissent un ensemble de constantes nommées. Les unions combinent plusieurs types, et les intersections combinent des types.

**Exemple:**
```ts
enum Status { Pending, InProgress, Completed }

type User = { name: string; age: number };
type Admin = User & { role: string };
type AdminUser = Admin | { guest: boolean };
```

### Types Utilitaires
Les types utilitaires comme `Partial`, `Pick` et `Record` permettent la transformation de types.

**Exemple:**
```ts
type Person = { name: string; age: number };
type PartialPerson = Partial<Person>;  // toutes les propriétés sont optionnelles
type NameOnly = Pick<Person, "name">;  // seul "name" est requis
type RecordType = Record<string, number>;  // objet avec des clés de type string et des valeurs de type number
```

---

## Routes API Typées

### Création de Routes API
Les routes API de Next.js sont définies dans le répertoire `/pages/api`.

**Exemple:**
```tsx
// pages/api/user.ts
import { NextApiRequest, NextApiResponse } from 'next';

export default (req: NextApiRequest, res: NextApiResponse) => {
  res.status(200).json({ name: "John" });
};
```

### Typage de la Requête et de la Réponse
Typez `NextApiRequest` et `NextApiResponse` pour les points de terminaison API.

**Exemple:**
```tsx
// pages/api/login.ts
import { NextApiRequest, NextApiResponse } from 'next';

type Data = { message: string; success: boolean };

export default (req: NextApiRequest, res: NextApiResponse<Data>) => {
  res.status(200).json({ message: "Connexion réussie", success: true });
};
```

---

## Types de Composants Réutilisables

### Définitions de Types Personnalisées
Définissez des types pour les composants personnalisés pour une meilleure réutilisabilité et évolutivité.

**Exemple:**
```ts
type ButtonProps = { label: string; onClick: () => void };

const Button: React.FC<ButtonProps> = ({ label, onClick }) => (
  <button onClick={onClick}>{label}</button>
);
```

### Composants Polymorphes
Les composants polymorphes acceptent différents types d'éléments en fonction des props, permettant des éléments d'interface utilisateur flexibles.

**Exemple:**
```ts
type BoxProps<T extends React.ElementType> = {
  as?: T;
  children: React.ReactNode;
};

function Box<T extends React.ElementType>({ as: Component = 'div', children }: BoxProps<T>) {
  return <Component>{children}</Component>;
}

// Utilisation
<Box as="section">This is a section</Box>
```

---

## Gestion des Formulaires et des Événements

### Typage des Éléments de Formulaire et des Événements
Typez correctement les éléments de formulaire et leurs gestionnaires d'événements.

**Exemple:**
```tsx
const handleSubmit = (event: React.FormEvent<HTMLFormElement>) => {
  event.preventDefault();
  console.log("Formulaire soumis");
};

return <form onSubmit={handleSubmit}>Submit</form>;
```

### Entrées Contrôlées vs Non Contrôlées
Les entrées contrôlées ont leur valeur gérée par l'état React, tandis que les entrées non contrôlées sont gérées par le DOM.

**Exemple:**
```tsx
// Entrée Contrôlée
const [value, setValue] = useState<string>('');
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => setValue(e.target.value);

return <input value={value} onChange={handleChange} />;

// Entrée Non Contrôlée
const inputRef = useRef<HTMLInputElement>(null);
return <input ref={inputRef} />;
```

---

## Gestion de l'État avec TypeScript

### `useState` et `useReducer` avec les Types
Les deux hooks peuvent bénéficier d'annotations de type pour une meilleure gestion de l'état.

**Exemple:**
```tsx
const [count, setCount] = useState<number>(0);

const [state, dispatch] = useReducer(
  (state: number, action: { type: string; payload: number }) => {
    switch (action.type) {
      case 'increment': return state + action.payload;
      default: return state;
    }
  },
  0
);
```

### `useContext` avec des Types Personnalisés
Utilisez `useContext` avec des types personnalisés pour créer une gestion d'état global type-safe.

**Exemple:**
```tsx
type AppContextType = { user: string; setUser: (name: string) => void };
const AppContext = createContext<AppContextType | undefined>(undefined);

const MyComponent = () => {
  const context = useContext(AppContext);
  if (!context) throw new Error('useContext must be used within a provider');
  return <div>{context.user}</div>;
};
```

---

## Conclusion

**Points Clés à Retenir:**
- Les fonctionnalités avancées de TypeScript comme les énumérations, les unions et les types utilitaires rendent le code plus robuste et flexible.
- Le typage correct des routes API assure une meilleure sécurité et fiabilité.
- Les composants polymorphes améliorent la réutilisabilité et la flexibilité des composants.
- Le typage correct des formulaires et des événements assure une expérience développeur plus fluide et moins de bugs.
- La gestion de l'état avec TypeScript apporte clarté et maintenabilité aux applications complexes.

---

## Exercice Pratique

**Construire un Formulaire Typé avec Gestion d'État :**
1. Créez un formulaire avec les champs `name` et `email`.
2. Utilisez `useState` pour gérer l'état des entrées du formulaire, et typez-le avec `string`.
3. Créez une fonction de soumission qui affiche les données du formulaire dans la console.
4. Ajoutez une entrée contrôlée pour `name` et `email`, en assurant un typage d'événement approprié.
