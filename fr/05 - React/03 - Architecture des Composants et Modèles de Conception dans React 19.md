
# Architecture des Composants et Modèles de Conception dans React 19

Maîtriser l'architecture des composants et les modèles de conception de React permet aux développeurs de construire des interfaces utilisateur évolutives, maintenables et réutilisables. Ce cours se concentre sur les stratégies structurelles et de composition clés dans React 19.

---

## Table des Matières
- [Modèles de Composition de Composants](#component-composition-patterns)
  - [Enfants en tant que Fonctions](#children-as-functions)
  - [Composants Composés](#compound-components)
- [Render Props vs Hooks Personnalisés](#render-props-vs-custom-hooks)
- [Composants d'Ordre Supérieur (HOCs)](#higher-order-components-hocs)
- [Composants Intelligents et Démunis](#smart-and-dumb-components)
- [Composants Conteneurs et de Présentation](#container-and-presentational-components)
- [Modèles Contrôlés vs Non Contrôlés](#controlled-vs-uncontrolled-patterns)
- [Bonnes Pratiques d'Organisation du Code et de Structure des Dossiers](#code-organization-and-folder-structure-best-practices)
- [Conclusion & Points Clés](#conclusion--key-takeaways)
- [Exercice Pratique](#practical-exercise)

---

## Modèles de Composition de Composants

### Enfants en tant que Fonctions
**Définition :** Un modèle où les composants acceptent une fonction comme enfant pour afficher du contenu dynamique.
**Exemple :**
```jsx
const MouseTracker = ({ children }) => {
  const [pos, setPos] = useState({ x: 0, y: 0 });
  return <div onMouseMove={e => setPos({ x: e.clientX, y: e.clientY })}>{children(pos)}</div>;
};

// Usage
<MouseTracker>{pos => <p>Souris en {pos.x}, {pos.y}</p>}</MouseTracker>
```

### Composants Composés
**Définition :** Un groupe de composants liés partageant un état via le contexte pour fonctionner comme un module unifié.
**Exemple :**
```jsx
const ToggleContext = createContext();

const Toggle = ({ children }) => {
  const [on, setOn] = useState(false);
  return (
    <ToggleContext.Provider value={{ on, toggle: () => setOn(o => !o) }}>
      {children}
    </ToggleContext.Provider>
  );
};

Toggle.Button = () => {
  const { toggle } = useContext(ToggleContext);
  return <button onClick={toggle}>Basculer</button>;
};

Toggle.Content = ({ children }) => {
  const { on } = useContext(ToggleContext);
  return on ? <div>{children}</div> : null;
};
```

---

## Render Props vs Hooks Personnalisés

**Définition :** Les deux modèles favorisent la réutilisation de la logique, mais les hooks personnalisés sont plus simples et plus composables dans React moderne.
**Exemple de Render Prop :**
```jsx
<DataFetcher render={data => <List items={data} />} />
```

**Exemple de Hook Personnalisé :**
```jsx
const data = useDataFetcher();
<List items={data} />
```

---

## Composants d'Ordre Supérieur (HOCs)

**Définition :** Fonctions qui enveloppent un composant pour l'améliorer avec des props ou une logique supplémentaires.
**Exemple :**
```jsx
const withUser = Component => props => {
  const user = useUser();
  return <Component {...props} user={user} />;
};

const ProfileWithUser = withUser(Profile);
```

---

## Composants Intelligents et Démunis

**Définition :** Les composants intelligents gèrent la logique et les données ; les composants démunis (de présentation) se concentrent uniquement sur le rendu de l'UI.
**Exemple :**
```jsx
// Intelligent
const CommentContainer = () => {
  const comments = useComments();
  return <CommentList comments={comments} />;
};

// Démuni
const CommentList = ({ comments }) => (
  <ul>{comments.map(c => <li key={c.id}>{c.text}</li>)}</ul>
);
```

---

## Composants Conteneurs et de Présentation

**Définition :** Un modèle intelligent/démuni formalisé où les conteneurs récupèrent/traitent les données et les passent aux composants de présentation sans état.
**Exemple :**
```jsx
const TodoContainer = () => {
  const todos = useTodos();
  return <TodoList todos={todos} />;
};

const TodoList = ({ todos }) => (
  <ul>{todos.map(todo => <li key={todo.id}>{todo.title}</li>)}</ul>
);
```

---

## Modèles Contrôlés vs Non Contrôlés

**Définition :** Les composants contrôlés sont liés à l'état via `value` et `onChange` ; les composants non contrôlés utilisent des refs pour un accès direct au DOM.
**Exemple Contrôlé :**
```jsx
<input value={text} onChange={e => setText(e.target.value)} />
```

**Exemple Non Contrôlé :**
```jsx
<input ref={inputRef} defaultValue="Hello" />
```

---

## Bonnes Pratiques d'Organisation du Code et de Structure des Dossiers

**Définition :** Organiser le code par fonctionnalité ou composant améliore l'évolutivité et la maintenabilité.
**Structure Recommandée :**
```
/src
  /components
    /Form
      Form.jsx
      Form.css
      index.js
  /hooks
    useForm.js
  /contexts
    ThemeContext.js
  /pages
    Home.jsx
    About.jsx
  /utils
    formatDate.js
```

---

## Conclusion & Points Clés

- La composition de composants (composés, enfants en tant que fonction) permet des structures d'UI flexibles.
- Les hooks personnalisés sont la solution moderne pour la réutilisation de la logique, remplaçant les HOCs et les render props.
- Les modèles intelligent/présentation séparent les préoccupations pour un code plus propre.
- Les composants contrôlés offrent une meilleure gestion de l'état des formulaires et de l'UI.
- Une structure de dossiers cohérente facilite la collaboration et l'évolutivité.

---

## Exercice Pratique

Créez un composant `Modal` en utilisant le modèle de **Composants Composés** :
1. Créez un composant racine `Modal` avec un état interne `isOpen`.
2. Ajoutez `Modal.OpenButton`, `Modal.CloseButton` et `Modal.Content`.
3. Utilisez le contexte pour coordonner les composants internes.
