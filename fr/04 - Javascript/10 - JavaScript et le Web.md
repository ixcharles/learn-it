
# Cours 10 : JavaScript et le Web

Ce cours explore la manière dont JavaScript interagit avec le navigateur et le web. Vous apprendrez à gérer les requêtes HTTP, à utiliser des API comme Fetch et WebSockets, et à gérer le stockage web pour construire des applications web dynamiques.

## Table des Matières
1. [Introduction à l'Environnement du Navigateur](#introduction-à-l'environnement-du-navigateur)
2. [HTTP et l'API Fetch](#http-et-l'api-fetch)
3. [Comprendre REST et GraphQL](#comprendre-rest-et-graphql)
4. [JSON : Analyse et Sérialisation](#json-analyse-et-sérialisation)
5. [WebSockets pour la Communication en Temps Réel](#websockets-pour-la-communication-en-temps-réel)
6. [API de Stockage Web : LocalStorage et SessionStorage](#api-de-stockage-web-localstorage-et-sessionstorage)

---

## Introduction à l'Environnement du Navigateur
L'environnement du navigateur permet à JavaScript d'interagir avec le DOM, de gérer les événements et de communiquer avec le serveur. Composants clés :
- **DOM (Document Object Model)** : Représente la structure d'un document HTML.
- **Boucle d'Événements** : Assure que JavaScript s'exécute de manière asynchrone sans bloquer le thread principal.
- **API du Navigateur** : Fournissent des interfaces pour interagir avec le navigateur, comme `localStorage`, `fetch()` et `setTimeout()`.

---

## HTTP et l'API Fetch
L'**API Fetch** fournit une manière moderne d'effectuer des requêtes HTTP, remplaçant les méthodes plus anciennes comme `XMLHttpRequest`. Elle renvoie des Promesses et est facile à utiliser avec `async/await`.

Exemple :
```javascript
// Effectuer une requête GET avec Fetch
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Utilisation de `async/await` :
```javascript
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

---

## Comprendre REST et GraphQL
- **REST (Representational State Transfer)** : Un style architectural qui utilise les méthodes HTTP (GET, POST, PUT, DELETE) pour la communication entre les clients et les serveurs. Les API REST renvoient des données dans des formats comme JSON ou XML.
- **GraphQL** : Un langage de requête pour les API, permettant aux clients de demander des données spécifiques. Contrairement à REST, qui expose plusieurs points de terminaison, GraphQL expose un seul point de terminaison pour toutes les requêtes de données.

Exemple d'appel d'une API REST :
```javascript
fetch('https://api.example.com/items')
  .then(response => response.json())
  .then(data => console.log(data));
```

Exemple de requête GraphQL :
```javascript
const query = `
  query {
    users {
      name
      email
    }
  }
`;

fetch('https://api.example.com/graphql', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ query })
})
  .then(response => response.json())
  .then(data => console.log(data));
```

---

## JSON : Analyse et Sérialisation
JSON (JavaScript Object Notation) est un format de données léger pour stocker et échanger des données entre un serveur et un client.

- **`JSON.parse()`** : Convertit une chaîne JSON en un objet JavaScript.
- **`JSON.stringify()`** : Convertit un objet JavaScript en une chaîne JSON.

Exemple :
```javascript
// Analyse de JSON
let jsonString = '{"name":"Alice","age":25}';
let parsedData = JSON.parse(jsonString);
console.log(parsedData.name);  // Alice

// Sérialisation d'un Objet
let obj = { name: 'Bob', age: 30 };
let jsonStringified = JSON.stringify(obj);
console.log(jsonStringified);  // '{"name":"Bob","age":30}'
```

---

## WebSockets pour la Communication en Temps Réel
Les WebSockets fournissent des canaux de communication bidirectionnels (full-duplex) sur une seule connexion TCP, idéaux pour les applications en temps réel comme les applications de chat ou les flux de données en direct.

Exemple :
```javascript
// Création d'une connexion WebSocket
const socket = new WebSocket('wss://example.com/socket');

// Écoute des messages
socket.onmessage = function(event) {
  console.log('Message from server:', event.data);
};

// Envoi d'un message
socket.send('Hello, server!');
```

---

## API de Stockage Web : LocalStorage et SessionStorage
L'API de Stockage Web fournit des mécanismes pour stocker des données côté client.

- **LocalStorage** : Stocke les données sans date d'expiration, accessibles entre les sessions.
- **SessionStorage** : Stocke les données uniquement pour la durée de la session de la page.

Exemple d'utilisation de LocalStorage :
```javascript
// Stockage de données
localStorage.setItem('username', 'Alice');

// Récupération de données
let username = localStorage.getItem('username');
console.log(username);  // Alice

// Suppression de données
localStorage.removeItem('username');
```

Exemple d'utilisation de SessionStorage :
```javascript
// Stockage de données
sessionStorage.setItem('sessionID', '12345');

// Récupération de données
let sessionID = sessionStorage.getItem('sessionID');
console.log(sessionID);  // 12345
```

---

## Conclusion

### Points Clés à Retenir :
1. **Environnement du Navigateur** : JavaScript interagit avec le navigateur via le DOM et des API comme `localStorage` et `fetch()`.
2. **HTTP et l'API Fetch** : Utilisez `fetch()` pour effectuer des requêtes HTTP et gérer les réponses avec les Promesses et `async/await`.
3. **REST vs. GraphQL** : Les API REST utilisent plusieurs points de terminaison, tandis que GraphQL utilise un seul point de terminaison pour des requêtes de données plus flexibles.
4. **JSON** : Utilisez `JSON.parse()` pour analyser les chaînes JSON et `JSON.stringify()` pour convertir les objets en JSON.
5. **WebSockets** : Permet la communication en temps réel pour les applications qui ont besoin de mises à jour instantanées, comme les applications de chat.
6. **Stockage Web** : Stockez des données côté client avec `localStorage` (persistant) et `sessionStorage` (basé sur la session).

### Exercice Pratique :
1. Récupérez des données d'une API REST et affichez-les dans la console. Ensuite, implémentez la même fonctionnalité en utilisant GraphQL.
2. Créez une connexion WebSocket à un serveur et envoyez un message lors d'un clic sur un bouton.
3. Implémentez la fonctionnalité de stockage local pour enregistrer et récupérer les préférences de l'utilisateur (comme la couleur du thème) lors des rechargements de page.
4. Analysez et sérialisez des données JSON, puis enregistrez-les dans la console.
