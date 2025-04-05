
# Travailler avec les API et l'intégration Backend

L'intégration de votre application avec un backend est essentielle pour le contenu dynamique, l'authentification et la communication en temps réel. Ce module couvre les techniques de base pour travailler avec REST, GraphQL et WebSockets dans React Native avec TypeScript.

## Table des matières
- [Récupération de données avec Fetch API et Axios](#récupération-de-données-avec-fetch-api-et-axios)
- [Gestion des réponses API et gestion des erreurs](#gestion-des-réponses-api-et-gestion-des-erreurs)
- [Authentification avec JWT et stockage sécurisé](#authentification-avec-jwt-et-stockage-sécurisé)
- [GraphQL avec Apollo Client](#graphql-avec-apollo-client)
- [WebSockets et gestion des données en temps réel](#websockets-et-gestion-des-données-en-temps-réel)

---

## Récupération de données avec Fetch API et Axios

**Définition :**
`fetch` est intégré à JavaScript, tandis qu'Axios est un client HTTP basé sur des promesses qui simplifie la gestion des requêtes et prend en charge les intercepteurs.

**Exemple (Axios) :**

```ts
import axios from 'axios';

const api = axios.create({ baseURL: 'https://api.example.com' });

type User = { id: number; name: string };

const getUser = async (): Promise<User> => {
  const response = await api.get<User>('/user');
  return response.data;
};
```

Utilisez des génériques dans Axios pour typer fortement les réponses.

---

## Gestion des réponses API et gestion des erreurs

**Définition :**
Gérez toujours les échecs de réseau et le comportement inattendu de l'API en utilisant try/catch et les intercepteurs Axios.

**Exemple :**

```ts
try {
  const user = await getUser();
  console.log(user.name);
} catch (error) {
  if (axios.isAxiosError(error)) {
    console.error('API Error:', error.response?.data);
  } else {
    console.error('Unexpected Error:', error);
  }
}
```

Affichez des messages d'erreur conviviaux et enregistrez les détails pour le débogage.

---

## Authentification avec JWT et stockage sécurisé

**Définition :**
Les JWT (JSON Web Tokens) sont couramment utilisés pour l'authentification sans état. Les tokens doivent être stockés en toute sécurité sur l'appareil.

**Exemple :**

```ts
import * as SecureStore from 'expo-secure-store';

const login = async (email: string, password: string) => {
  const res = await axios.post('/login', { email, password });
  const token = res.data.token;
  await SecureStore.setItemAsync('token', token);
};
```

Utilisez `SecureStore` pour conserver les tokens en toute sécurité au lieu de `AsyncStorage`.

---

## GraphQL avec Apollo Client

**Définition :**
Apollo Client est un outil puissant pour interagir avec les API GraphQL, prenant en charge la mise en cache, la pagination et les abonnements.

**Exemple :**

```tsx
import { ApolloClient, InMemoryCache, gql, useQuery } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://example.com/graphql',
  cache: new InMemoryCache(),
});

const GET_USER = gql`
  query GetUser {
    user {
      id
      name
    }
  }
`;

const UserComponent = () => {
  const { data, loading } = useQuery(GET_USER);
  if (loading) return <Text>Loading...</Text>;
  return <Text>{data.user.name}</Text>;
};
```

Encapsulez votre application dans un `ApolloProvider` pour activer les requêtes et mutations GraphQL.

---

## WebSockets et gestion des données en temps réel

**Définition :**
Les WebSockets permettent une communication bidirectionnelle en temps réel entre le client et le serveur.

**Exemple (socket.io-client) :**

```ts
import { io } from 'socket.io-client';

const socket = io('https://example.com');

socket.on('connect', () => {
  console.log('Connected');
});

socket.on('message', (data: string) => {
  console.log('New message:', data);
});

socket.emit('sendMessage', 'Hello Server');
```

Les WebSockets sont idéaux pour les chats, les notifications et les mises à jour en direct.

---

## Conclusion

**Points clés à retenir :**
1. Utilisez Axios ou `fetch` avec les génériques TypeScript pour des appels API propres et typés.
2. Gérez correctement les erreurs en utilisant try/catch et les intercepteurs Axios.
3. Sécurisez les tokens sensibles avec `expo-secure-store`, pas `AsyncStorage`.
4. Apollo Client rend le travail avec GraphQL simple et efficace.
5. Les WebSockets offrent des capacités en temps réel pour les fonctionnalités interactives.

**Exercice pratique :**
- Create a simple login form that calls a fake login API.
- Save the JWT securely using `SecureStore`.
- Fetch and display a protected user profile from the backend using the saved token.
