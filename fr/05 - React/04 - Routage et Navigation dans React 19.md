
# Routage et Navigation dans React 19

Le routage et la navigation sont des aspects clés de la construction d'applications monopages (SPA) dans React. Ce cours explore React Router v7 et les modèles de navigation avancés dans React 19.

---

## Table des Matières
- [React Router v7 (Dernière Version avec React 19)](#react-router-v7-latest-with-react-19)
  - [Route, Routes, Navigate, useNavigate](#route-routes-navigate-usenavigate)
  - [Routes Imbriquées](#nested-routes)
  - [Routage Dynamique](#dynamic-routing)
  - [Loaders et Actions de Route](#route-loaders-and-actions)
  - [Découpage du Code Basé sur les Routes](#route-based-code-splitting)
- [Gardes de Navigation et Flux d'Authentification](#navigation-guards-and-authentication-flows)
- [Chargement Paresseux des Routes](#lazy-loading-routes)
- [Limites d'Erreur dans le Routage](#error-boundaries-in-routing)
- [Conclusion & Points Clés](#conclusion--key-takeaways)
- [Exercice Pratique](#practical-exercise)

---

## React Router v7 (Dernière Version avec React 19)

### Route, Routes, Navigate, useNavigate

**Définition :** `Route` définit un chemin, `Routes` enveloppe plusieurs routes, `Navigate` redirige les utilisateurs, et `useNavigate` navigue de manière programmatique.
**Exemple :**
```jsx
import { Routes, Route, Navigate, useNavigate } from 'react-router-dom';

const App = () => {
  const navigate = useNavigate();

  const handleRedirect = () => {
    navigate('/home');
  };

  return (
    <div>
      <button onClick={handleRedirect}>Aller à la Page d'Accueil</button>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="home" element={<h2>Page d'Accueil</h2>} />
      </Routes>
    </div>
  );
};
```

---

### Routes Imbriquées

**Définition :** Les routes imbriquées permettent de définir des routes enfants à l'intérieur de routes parentes.
**Exemple :**
```jsx
<Routes>
  <Route path="dashboard" element={<Dashboard />}>
    <Route path="profile" element={<Profile />} />
    <Route path="settings" element={<Settings />} />
  </Route>
</Routes>
```

---

### Routage Dynamique

**Définition :** Les routes dynamiques sont créées en fonction de paramètres ou de données externes.
**Exemple :**
```jsx
<Routes>
  <Route path="user/:id" element={<UserDetail />} />
</Routes>

const UserDetail = () => {
  const { id } = useParams();
  return <div>ID Utilisateur : {id}</div>;
};
```

---

### Loaders et Actions de Route

**Définition :** Les loaders et les actions de route peuvent récupérer des données avant le rendu de la route ou effectuer des actions comme l'authentification.
**Exemple :**
```jsx
import { Route, useLoaderData } from 'react-router-dom';

const fetchData = async () => {
  const response = await fetch('/api/data');
  return response.json();
};

<Routes>
  <Route path="/data" element={<DataPage />} loader={fetchData} />
</Routes>

const DataPage = () => {
  const data = useLoaderData();
  return <div>{JSON.stringify(data)}</div>;
};
```

---

### Découpage du Code Basé sur les Routes

**Définition :** Le découpage du code charge uniquement les composants nécessaires lorsque la route est accédée.
**Exemple :**
```jsx
import { Suspense, lazy } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

<Routes>
  <Route
    path="/lazy"
    element={
      <Suspense fallback={<div>Chargement...</div>}>
        <LazyComponent />
      </Suspense>
    }
  />
</Routes>
```

---

## Gardes de Navigation et Flux d'Authentification

**Définition :** Les gardes de navigation protègent les routes contre les accès non autorisés, nécessitant souvent une authentification.
**Exemple :**
```jsx
const ProtectedRoute = ({ children }) => {
  const isAuthenticated = useAuth();
  return isAuthenticated ? children : <Navigate to="/login" />;
};

<Routes>
  <Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
</Routes>
```

---

## Chargement Paresseux des Routes

**Définition :** Les routes sont chargées paresseusement pour améliorer les performances en divisant le bundle.
**Exemple :**
```jsx
const HomePage = lazy(() => import('./HomePage'));

<Routes>
  <Route
    path="/home"
    element={
      <Suspense fallback={<div>Chargement...</div>}>
        <HomePage />
      </Suspense>
    }
  />
</Routes>
```

---

## Limites d'Erreur dans le Routage

**Définition :** Les limites d'erreur捕获 les erreurs dans les composants React et empêchent les plantages dans l'interface utilisateur.
**Exemple :**
```jsx
import { ErrorBoundary } from 'react-error-boundary';

<Routes>
  <Route
    path="/dashboard"
    element={
      <ErrorBoundary FallbackComponent={ErrorFallback}>
        <Dashboard />
      </ErrorBoundary>
    }
  />
</Routes>

const ErrorFallback = ({ error }) => <div>Erreur : {error.message}</div>;
```

---

## Conclusion & Points Clés

- `Route`, `Routes` et `Navigate` sont fondamentaux pour le flux de navigation de React Router.
- Les routes imbriquées et dynamiques offrent une flexibilité pour des structures d'application évolutives.
- Les loaders et les actions de route améliorent la récupération de données et la logique conditionnelle au sein des routes.
- Le chargement paresseux des routes et le découpage du code améliorent considérablement les performances.
- Les gardes de navigation protègent les routes sensibles en fonction de l'authentification ou d'autres conditions.
- Les limites d'erreur garantissent que la navigation ne casse pas l'application en cas d'erreur.

---

## Exercice Pratique

Construisez une application de blog basique avec React Router :
1. Créez une route pour la page d'accueil (`/`), une liste d'articles (`/posts`) et un article unique (`/posts/:id`).
2. Utilisez `useNavigate` pour rediriger vers une page de détails d'un article.
3. Implémentez le chargement paresseux pour la page de détails de l'article et des limites d'erreur pour捕获 les erreurs potentielles pendant la navigation.
