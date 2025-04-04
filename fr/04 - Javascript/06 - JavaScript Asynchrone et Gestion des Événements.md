
# JavaScript Asynchrone et Gestion des Événements

La programmation asynchrone en JavaScript vous permet de gérer des tâches gourmandes en temps sans bloquer le thread principal, améliorant ainsi les performances et l'expérience utilisateur. Ce cours explore en profondeur les fonctions de rappel (callbacks), les promesses, la gestion des événements et les techniques asynchrones avancées telles que la boucle d'événements et les web workers.

## Table des Matières
1. [Callbacks et l'Enfer des Callbacks](#callbacks-et-l'enfer-des-callbacks)
2. [Promesses : Syntaxe, Chaînage et Gestion des Erreurs](#promesses-syntaxe-chaînage-et-gestion-des-erreurs)
3. [Syntaxe `async`/`await`](#asyncawait-syntax)
4. [La Boucle d'Événements et la File d'Attente](#la-boucle-d'événements-et-la-file-d'attente)
5. [Comprendre `setTimeout` et `setInterval`](#comprendre-settimeout-et-setinterval)
6. [Délégation d'Événements](#délégation-d'événements)
7. [Propagation des Événements : Bubbling et Capturing](#propagation-des-événements-bubbling-et-capturing)
8. [Throttling et Debouncing](#throttling-et-debouncing)
9. [Web Workers pour le Multithreading](#web-workers-pour-le-multithreading)

---

## Callbacks et l'Enfer des Callbacks
Un callback est une fonction passée en argument à une autre fonction, qui est invoquée une fois que la fonction externe a terminé son opération. L'enfer des callbacks se produit lorsque les callbacks sont imbriqués trop profondément, rendant le code difficile à lire et à maintenir.

Exemple :
```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback('Data fetched');
  }, 1000);
}

fetchData(function(response) {
  console.log(response);
});
```

Pour éviter l'enfer des callbacks, il est recommandé d'utiliser des promesses ou async/await pour un code plus propre.

---

## Promesses : Syntaxe, Chaînage et Gestion des Erreurs
Une promesse représente l'achèvement (ou l'échec) éventuel d'une opération asynchrone et sa valeur résultante. Les promesses vous permettent d'enchaîner plusieurs opérations et de gérer les erreurs plus élégamment.

Exemple :
```javascript
let fetchData = new Promise((resolve, reject) => {
  let success = true;  // simuler le succès ou l'échec
  if(success) {
    resolve('Data fetched successfully');
  } else {
    reject('Error fetching data');
  }
});

fetchData
  .then(response => console.log(response))  // gérer le succès
  .catch(error => console.log(error));  // gérer l'erreur
```

---

## Syntaxe `async`/`await`
Les fonctions `async` vous permettent d'écrire du code asynchrone qui ressemble à du code synchrone. `await` met en pause l'exécution d'une fonction async jusqu'à ce qu'une promesse soit résolue.

Exemple :
```javascript
async function fetchData() {
  let response = await new Promise(resolve => setTimeout(() => resolve('Data fetched'), 1000));
  console.log(response);
}

fetchData();  // Data fetched
```

---

## La Boucle d'Événements et la File d'Attente
La boucle d'événements JavaScript gère l'exécution du code, des événements et des messages. Elle vérifie continuellement la pile d'appels pour les tâches et les traite dans l'ordre où elles sont ajoutées, assurant un comportement non bloquant pour les opérations asynchrones.

Exemple :
```javascript
console.log('Start');

setTimeout(() => {
  console.log('Inside Timeout');
}, 0);

console.log('End');
```
Sortie :
```
Start
End
Inside Timeout
```
Ici, même si le délai d'attente est de 0, il est placé dans la file d'attente des événements et exécuté après le code synchrone.

---

## Comprendre `setTimeout` et `setInterval`
- `setTimeout()` est utilisé pour exécuter une fonction une seule fois après un délai spécifié.
- `setInterval()` est utilisé pour exécuter une fonction de manière répétée à des intervalles spécifiés.

Exemple :
```javascript
// Exemple setTimeout
setTimeout(() => {
  console.log('This runs after 2 seconds');
}, 2000);

// Exemple setInterval
let count = 0;
let interval = setInterval(() => {
  count++;
  console.log(`Count: ${count}`);
  if (count === 5) clearInterval(interval);  // arrêter après 5 comptes
}, 1000);
```

---

## Délégation d'Événements
La délégation d'événements est une technique où un seul écouteur d'événements est ajouté à un élément parent, et il gère les événements pour les éléments enfants. Ceci est particulièrement utile pour les éléments ajoutés dynamiquement.

Exemple :
```javascript
document.querySelector('#parent').addEventListener('click', function(event) {
  if (event.target && event.target.matches('button')) {
    console.log('Button clicked');
  }
});
```
Ici, l'écouteur d'événements est placé sur le parent `#parent`, mais il écoute les clics sur n'importe quel `button` à l'intérieur.

---

## Propagation des Événements : Bubbling et Capturing
La propagation des événements décrit le flux des événements à travers le DOM. Il existe deux phases :
- **Bubbling (remontée)** : L'événement commence à l'élément cible et remonte jusqu'à la racine.
- **Capturing (capture)** : L'événement commence à la racine et descend jusqu'à l'élément cible.

Exemple :
```javascript
document.querySelector('#child').addEventListener('click', () => {
  console.log('Child Clicked');
}, true);  // Utiliser `true` pour la phase de capture

document.querySelector('#parent').addEventListener('click', () => {
  console.log('Parent Clicked');
}, false);  // La valeur par défaut est la phase de bubbling
```
Sortie lorsque l'enfant est cliqué :
```
Child Clicked
Parent Clicked
```

---

## Throttling et Debouncing
- **Throttling (limitation)** garantit qu'une fonction est appelée au maximum une fois dans une période spécifiée, même si elle est invoquée plusieurs fois.
- **Debouncing (anti-rebond)** garantit qu'une fonction n'est appelée qu'après un délai spécifié, empêchant de multiples invocations rapides.

Exemple (Throttling) :
```javascript
let throttle = (func, delay) => {
  let lastCall = 0;
  return function() {
    let now = Date.now();
    if (now - lastCall >= delay) {
      func();
      lastCall = now;
    }
  };
};

let throttledFunction = throttle(() => console.log('Throttled!'), 2000);
window.addEventListener('scroll', throttledFunction);
```

Exemple (Debouncing) :
```javascript
let debounce = (func, delay) => {
  let timeout;
  return function() {
    clearTimeout(timeout);
    timeout = setTimeout(func, delay);
  };
};

let debouncedFunction = debounce(() => console.log('Debounced!'), 2000);
window.addEventListener('resize', debouncedFunction);
```

---

## Web Workers pour le Multithreading
Les Web Workers vous permettent d'exécuter des scripts dans des threads d'arrière-plan, déchargeant les calculs lourds pour éviter de bloquer le thread principal de l'interface utilisateur. Les Workers communiquent avec le thread principal via le passage de messages.

Exemple :
```javascript
// main.js
let worker = new Worker('worker.js');

worker.postMessage('start');

worker.onmessage = function(event) {
  console.log('Received from worker:', event.data);
};

// worker.js
onmessage = function(event) {
  if (event.data === 'start') {
    postMessage('Heavy computation completed');
  }
};
```

---

## Conclusion

### Points Clés à Retenir :
1. Les callbacks sont une partie fondamentale de la programmation asynchrone, mais ils peuvent mener à l'enfer des callbacks. Les promesses et async/await offrent de meilleures alternatives.
2. Les promesses aident avec le code asynchrone en permettant le chaînage et la gestion centralisée des erreurs.
3. `async/await` rend le code asynchrone plus facile à lire en imitant le flux synchrone.
4. La boucle d'événements assure un comportement non bloquant en gérant la pile d'appels et la file d'attente des événements.
5. Comprendre la délégation et la propagation des événements aide à gérer efficacement les événements DOM.
6. Le throttling et le debouncing améliorent les performances en limitant les appels de fonctions lors d'événements rapides.
7. Les Web Workers permettent le multithreading, exécutant des tâches en arrière-plan sans bloquer le thread principal.

### Exercice Pratique :
1. Créez une fonction qui récupère des données d'une API distante en utilisant `async/await` et les affiche.
2. Implémentez un écouteur d'événements sur un élément parent en utilisant la délégation d'événements pour gérer les clics sur des éléments enfants ajoutés dynamiquement.
3. Écrivez une fonction debounced pour gérer une entrée de recherche et récupérer les résultats uniquement après que l'utilisateur a cessé de taper pendant 1 seconde.
4. Créez une fonction throttled pour limiter le nombre de fois qu'un gestionnaire d'événements de défilement est exécuté.
5. Implémentez un simple web worker pour effectuer un calcul sans bloquer le thread principal.
