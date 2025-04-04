
# Manipulation du DOM et API du Navigateur en JavaScript

Ce cours couvre les techniques fondamentales pour interagir avec le Document Object Model (DOM) en JavaScript. Apprenez à manipuler des éléments, à gérer des événements et à interagir avec diverses API du navigateur pour le développement web moderne.

## Table des Matières
1. [Sélectionner des Éléments : `getElementById`, `querySelector`, etc.](#sélectionner-des-éléments-getelementbyid-queryselector-etc)
2. [Modifier les Éléments et les Attributs du DOM](#modifier-les-éléments-et-les-attributs-du-dom)
3. [Gérer les Événements sur les Éléments du DOM](#gérer-les-événements-sur-les-éléments-du-dom)
4. [Navigation et Manipulation du DOM](#navigation-et-manipulation-du-dom)
5. [Création d'Éléments DOM : `createElement`, `appendChild`, etc.](#création-d'éléments-dom-createelement-appendchild-etc)
6. [Travailler avec les Formulaires et la Validation](#travailler-avec-les-formulaires-et-la-validation)
7. [Stockage Local et Stockage de Session](#stockage-local-et-stockage-de-session)
8. [L'API Fetch](#l'api-fetch)
9. [Géolocalisation et API de l'Appareil](#géolocalisation-et-api-de-l'appareil)

---

## Sélectionner des Éléments : `getElementById`, `querySelector`, etc.
En JavaScript, les éléments DOM peuvent être accédés à l'aide de méthodes telles que `getElementById`, `getElementsByClassName` et `querySelector`. La méthode `querySelector` est polyvalente et peut sélectionner des éléments à l'aide de sélecteurs CSS.

Exemple :
```javascript
// Sélection par ID
let elementById = document.getElementById('myElement');

// Sélection par classe
let elementsByClass = document.getElementsByClassName('myClass');

// Sélection avec des sélecteurs CSS
let elementBySelector = document.querySelector('.myClass');  // Première correspondance
let allElementsBySelector = document.querySelectorAll('.myClass');  // Toutes les correspondances
```

---

## Modifier les Éléments et les Attributs du DOM
Une fois les éléments sélectionnés, vous pouvez modifier leur contenu, leurs styles et leurs attributs à l'aide de JavaScript.

Exemple :
```javascript
let element = document.getElementById('myElement');

// Modifier le contenu
element.textContent = 'New Text Content';
element.innerHTML = '<span>New HTML Content</span>';

// Modifier les attributs
element.setAttribute('class', 'newClass');
element.style.color = 'blue';
```

---

## Gérer les Événements sur les Éléments du DOM
La gestion des événements tels que les clics, les changements de saisie, etc., peut être effectuée à l'aide de méthodes comme `addEventListener`.

Exemple :
```javascript
let button = document.getElementById('myButton');

// Écouteur d'événement pour le clic
button.addEventListener('click', function() {
  alert('Button clicked!');
});
```

---

## Navigation et Manipulation du DOM
La navigation dans le DOM vous permet de parcourir les éléments parents, enfants et frères, ce qui facilite la manipulation de la structure du DOM.

Exemple :
```javascript
let parent = document.getElementById('parent');
let child = parent.firstElementChild; // Accéder au premier élément enfant
let nextSibling = child.nextElementSibling; // Accéder à l'élément frère suivant
let parentElement = child.parentElement; // Accéder à l'élément parent
```

---

## Création d'Éléments DOM : `createElement`, `appendChild`, etc.
La création dynamique de nouveaux éléments et leur ajout au DOM peuvent être effectués à l'aide de `createElement` et `appendChild`.

Exemple :
```javascript
let newDiv = document.createElement('div');
newDiv.textContent = 'This is a new div element';

// Ajouter la nouvelle div au body
document.body.appendChild(newDiv);
```

---

## Travailler avec les Formulaires et la Validation
Les formulaires peuvent être manipulés et validés à l'aide de JavaScript. Accédez aux éléments de formulaire, obtenez les valeurs et validez la saisie de l'utilisateur.

Exemple :
```javascript
let form = document.getElementById('myForm');
let nameInput = document.getElementById('name');

// Accéder aux valeurs du formulaire
let nameValue = nameInput.value;

// Validation simple
form.addEventListener('submit', function(event) {
  if (nameValue === '') {
    event.preventDefault();
    alert('Name is required!');
  }
});
```

---

## Stockage Local et Stockage de Session
Le Stockage Local et le Stockage de Session sont utilisés pour stocker des données dans le navigateur. Le Stockage Local conserve les données même lorsque le navigateur est fermé, tandis que le Stockage de Session est effacé lorsque la session du navigateur se termine.

Exemple :
```javascript
// Stocker des données dans le stockage local
localStorage.setItem('username', 'JohnDoe');

// Récupérer des données du stockage local
let username = localStorage.getItem('username');
console.log(username);  // JohnDoe

// Stocker des données dans le stockage de session
sessionStorage.setItem('sessionKey', 'abc123');

// Récupérer des données du stockage de session
let sessionKey = sessionStorage.getItem('sessionKey');
console.log(sessionKey);  // abc123
```

---

## L'API Fetch
L'API Fetch vous permet d'effectuer des requêtes réseau, telles que la récupération de données d'un serveur. Elle renvoie une promesse, ce qui facilite la gestion des opérations asynchrones.

Exemple :
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log('Error:', error));
```

---

## Géolocalisation et API de l'Appareil
L'API de Géolocalisation vous permet de récupérer la position de l'utilisateur, tandis que les API de l'Appareil peuvent fournir des informations sur l'appareil de l'utilisateur, telles que la taille de l'écran ou l'état de la batterie.

Exemple :
```javascript
// Utilisation de l'API de Géolocalisation pour obtenir la position de l'utilisateur
navigator.geolocation.getCurrentPosition(function(position) {
  console.log('Latitude:', position.coords.latitude);
  console.log('Longitude:', position.coords.longitude);
});

// Utilisation de l'API de l'Appareil pour la taille de l'écran
console.log('Screen width:', window.screen.width);
console.log('Screen height:', window.screen.height);
```

---

## Conclusion

### Points Clés à Retenir :
1. Les éléments DOM peuvent être sélectionnés et manipulés à l'aide de méthodes telles que `getElementById`, `querySelector` et `querySelectorAll`.
2. Vous pouvez modifier dynamiquement le contenu, les attributs et les styles des éléments à l'aide de JavaScript.
3. La gestion des événements avec `addEventListener` vous permet de répondre aux interactions de l'utilisateur telles que les clics et les changements de saisie.
4. La navigation dans le DOM vous permet de vous déplacer entre les éléments, par exemple en accédant aux nœuds parents, enfants et frères.
5. Vous pouvez créer dynamiquement de nouveaux éléments à l'aide de méthodes telles que `createElement` et `appendChild`.
6. Les données de formulaire peuvent être consultées et validées à l'aide de JavaScript, ce qui permet un meilleur contrôle de la saisie de l'utilisateur.
7. Le Stockage Local et le Stockage de Session permettent le stockage persistant de données dans le navigateur.
8. L'API Fetch simplifie l'exécution de requêtes réseau et la gestion des données asynchrones.
9. L'API de Géolocalisation et les API de l'Appareil donnent accès aux informations de localisation et de l'appareil.

### Exercice Pratique :
1. Créez un formulaire avec des champs de saisie pour le nom et l'e-mail, et validez les champs avant la soumission.
2. Écrivez une fonction pour ajouter dynamiquement une liste d'éléments (par exemple, des éléments de la liste de tâches) au DOM.
3. Utilisez l'API Fetch pour récupérer et afficher les données d'utilisateur à partir d'une API publique (par exemple, JSONPlaceholder).
4. Stockez les préférences de l'utilisateur (par exemple, la couleur du thème) dans le stockage local et récupérez-les lorsque la page se charge.
5. Implémentez un bouton qui affiche la position actuelle de l'utilisateur à l'aide de l'API de Géolocalisation.
