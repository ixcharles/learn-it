
# Programmation Asynchrone en TypeScript

Ce cours explore comment TypeScript améliore la programmation asynchrone grâce au typage fort des fonctions de rappel, des Promises et de `async/await`. Vous apprendrez également à gérer efficacement les erreurs et à intégrer TypeScript avec des API comme Fetch et Axios.

## Table des Matières

1. [Fonctions de Rappel, Promises et async/await en TypeScript](#callbacks-promises-and-asyncawait-in-typescript)
2. [Travailler avec les Types Promise de TypeScript](#working-with-typescripts-promise-types)
3. [Typage des fonctions async et des chaînes de Promises](#typing-async-functions-and-promise-chains)
4. [Gestion des Erreurs dans le Code Asynchrone](#error-handling-in-asynchronous-code)
5. [Utilisation de TypeScript avec l'API Fetch ou Axios](#using-typescript-with-fetch-api-or-axios)

---

## Fonctions de Rappel, Promises et async/await en TypeScript

TypeScript prend en charge plusieurs modèles asynchrones : les fonctions de rappel, les Promises et `async/await`, avec une sécurité de type complète.

### Exemple : Promises avec async/await

```typescript
function fetchData(): Promise<string> {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Données chargées"), 1000);
  });
}

async function load() {
  const result = await fetchData();
  console.log(result);
}

load();
```

---

## Travailler avec les Types Promise de TypeScript

Les fonctions renvoyant des Promises doivent avoir des types de retour comme `Promise<Type>` pour la clarté et l'inférence de type.

### Exemple :

```typescript
function getUser(): Promise<{ name: string; age: number }> {
  return Promise.resolve({ name: "Alice", age: 30 });
}

getUser().then(user => console.log(user.name));
```

---

## Typage des fonctions async et des chaînes de Promises

Les fonctions `async` renvoient automatiquement une `Promise<Type>`. Le typage explicite assure la clarté et la cohérence.

### Exemple :

```typescript
async function getMessage(): Promise<string> {
  return "Bonjour le monde !";
}

getMessage().then((msg: string) => console.log(msg));
```

---

## Gestion des Erreurs dans le Code Asynchrone

Utilisez `try/catch` pour `async/await` et `.catch()` pour les Promises afin de gérer les erreurs.

### Exemple :

```typescript
async function riskyTask(): Promise<void> {
  try {
    const result = await fetchData();
    console.log(result);
  } catch (error) {
    console.error("Une erreur est survenue :", error);
  }
}
```

---

## Utilisation de TypeScript avec l'API Fetch ou Axios

Fetch et Axios fonctionnent de manière transparente avec TypeScript. Vous pouvez définir des types de réponse pour garantir un accès sécurisé aux données.

### Exemple avec Fetch :

```typescript
interface Post {
  id: number;
  title: string;
}

async function getPost(): Promise<Post> {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts/1");
  const data: Post = await res.json();
  return data;
}
```

### Exemple avec Axios :

```typescript
import axios from "axios";

interface Post {
  id: number;
  title: string;
}

async function getPost(): Promise<Post> {
  const res = await axios.get<Post>("https://jsonplaceholder.typicode.com/posts/1");
  return res.data;
}
```

---

## Conclusion

### Points Clés à Retenir :
1. TypeScript prend en charge plusieurs paradigmes asynchrones avec la sécurité de type.
2. Utilisez `Promise<Type>` pour exprimer clairement les types de retour des opérations asynchrones.
3. Gérez toujours les erreurs dans le code asynchrone avec `try/catch` ou `.catch()`.
4. Le typage des fonctions `async` aide à prévenir les erreurs d'exécution.
5. Fetch et Axios s'intègrent facilement à TypeScript pour une gestion sécurisée des API.

### Exercice Pratique :
1. Écrivez une fonction `async` `getUserData` qui renvoie un objet `Utilisateur` typé après 1 seconde en utilisant une `Promise`.
2. Utilisez à la fois `.then()` et `async/await` pour l'appeler.
3. Ajoutez un échec simulé et gérez l'erreur correctement avec un bloc `try/catch`.
