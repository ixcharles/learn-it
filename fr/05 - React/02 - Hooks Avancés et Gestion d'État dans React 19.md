
# Hooks Avancés et Gestion d'État dans React 19

React 19 s'appuie sur des Hooks puissants pour gérer les effets secondaires, l'état et la logique applicative. Ce cours explore en profondeur les Hooks avancés et les stratégies pour une gestion d'état évolutive et optimisée.

---

## Table des Matières
- [Exploration Approfondie du Hook useEffect](#useeffect-hook-deep-dive)
  - [Simulation du Cycle de Vie](#lifecycle-simulation)
  - [Fonctions de Nettoyage](#cleanup-functions)
- [useMemo et useCallback](#usememo-and-usecallback)
  - [Optimisation des Performances](#performance-optimization)
- [useRef et Accès au DOM](#useref-and-dom-access)
- [Hooks Personnalisés](#custom-hooks)
  - [Création de Logique Réutilisable](#building-reusable-logic)
- [useReducer et Machines à États](#usereducer-and-state-machines)
- [API Context](#context-api)
  - [État Global avec useContext](#global-state-with-usecontext)
  - [Modèles de Performance du Context](#context-performance-patterns)
- [Conclusion & Points Clés](#conclusion--key-takeaways)
- [Exercice Pratique](#practical-exercise)

---

## Exploration Approfondie du Hook useEffect

### Simulation du Cycle de Vie
**Définition :** `useEffect` réplique le comportement de montage, de mise à jour et de démontage.
**Exemple :**
```jsx
useEffect(() => {
  console.log('Mounted or updated');
}, [dependency]);
```

### Fonctions de Nettoyage
**Définition :** Les fonctions de nettoyage s'exécutent au démontage ou avant la réexécution de l'effet.
**Exemple :**
```jsx
useEffect(() => {
  const timer = setInterval(...);
  return () => clearInterval(timer);
}, []);
```

---

## useMemo et useCallback

### Optimisation des Performances
**Définition :** `useMemo` met en cache les valeurs calculées ; `useCallback` met en cache les fonctions.
**Exemple :**
```jsx
const expensiveResult = useMemo(() => compute(data), [data]);
const memoizedFn = useCallback(() => doSomething(), []);
```

---

## useRef et Accès au DOM
**Définition :** `useRef` accède aux nœuds DOM ou persiste des valeurs sans déclencher de nouvelles rendus.
**Exemple :**
```jsx
const inputRef = useRef();
<input ref={inputRef} />;
inputRef.current.focus();
```

---

## Hooks Personnalisés

### Création de Logique Réutilisable
**Définition :** Les Hooks personnalisés encapsulent la logique pour une réutilisation à travers les composants.
**Exemple :**
```jsx
function useToggle(initial = false) {
  const [value, setValue] = useState(initial);
  const toggle = () => setValue(v => !v);
  return [value, toggle];
}
```

---

## useReducer et Machines à États
**Définition :** `useReducer` est utile pour les transitions d'état complexes et la logique d'état fini.
**Exemple :**
```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
  }
}
const [state, dispatch] = useReducer(reducer, { count: 0 });
```

---

## API Context

### État Global avec useContext
**Définition :** `useContext` accède à l'état partagé à travers les composants.
**Exemple :**
```jsx
const ThemeContext = createContext();
const theme = useContext(ThemeContext);
```

### Modèles de Performance du Context
**Définition :** Empêchez les rendus inutiles avec des fournisseurs mis en cache et la division du contexte.
**Exemple :**
```jsx
const MemoizedProvider = React.memo(({ children }) => (
  <ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>
));
```

---

## Conclusion & Points Clés
- `useEffect` gère les effets secondaires et imite les méthodes de cycle de vie.
- `useMemo` et `useCallback` améliorent les performances de rendu.
- `useRef` fournit un stockage mutable et des références au DOM.
- Les Hooks personnalisés favorisent une logique modulaire et réutilisable.
- `useReducer` et l'API Context alimentent des systèmes d'état global évolutifs.

---

## Exercice Pratique

Créez un commutateur de thème activable/désactivable en utilisant Context et des Hooks personnalisés :
1. Créez un `ThemeContext` avec les valeurs `"light"` ou `"dark"`.
2. Utilisez un hook personnalisé pour basculer le thème.
3. Affichez un bouton qui bascule le thème en utilisant le contexte.
