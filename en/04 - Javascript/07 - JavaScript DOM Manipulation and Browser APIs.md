
# JavaScript DOM Manipulation and Browser APIs

This course covers the fundamental techniques for interacting with the Document Object Model (DOM) in JavaScript. Learn how to manipulate elements, handle events, and interact with various browser APIs for modern web development.

## Table of Contents
1. [Selecting Elements: `getElementById`, `querySelector`, etc.](#selecting-elements-getelementbyid-queryselector-etc)
2. [Modifying DOM Elements and Attributes](#modifying-dom-elements-and-attributes)
3. [Handling Events on DOM Elements](#handling-events-on-dom-elements)
4. [DOM Traversal and Manipulation](#dom-traversal-and-manipulation)
5. [DOM Creation: `createElement`, `appendChild`, etc.](#dom-creation-createelement-appendchild-etc)
6. [Working with Forms and Validation](#working-with-forms-and-validation)
7. [Local Storage and Session Storage](#local-storage-and-session-storage)
8. [The Fetch API](#the-fetch-api)
9. [Geolocation and Device APIs](#geolocation-and-device-apis)

---

## Selecting Elements: `getElementById`, `querySelector`, etc.
In JavaScript, DOM elements can be accessed using methods like `getElementById`, `getElementsByClassName`, and `querySelector`. The `querySelector` method is versatile and can select elements using CSS selectors.

Example:
```javascript
// Selecting by ID
let elementById = document.getElementById('myElement');

// Selecting by class
let elementsByClass = document.getElementsByClassName('myClass');

// Selecting with CSS selectors
let elementBySelector = document.querySelector('.myClass');  // First match
let allElementsBySelector = document.querySelectorAll('.myClass');  // All matches
```

---

## Modifying DOM Elements and Attributes
Once elements are selected, you can modify their content, styles, and attributes using JavaScript.

Example:
```javascript
let element = document.getElementById('myElement');

// Modify content
element.textContent = 'New Text Content';
element.innerHTML = '<span>New HTML Content</span>';

// Modify attributes
element.setAttribute('class', 'newClass');
element.style.color = 'blue';
```

---

## Handling Events on DOM Elements
Handling events like clicks, input changes, and others can be done using methods like `addEventListener`.

Example:
```javascript
let button = document.getElementById('myButton');

// Event listener for click
button.addEventListener('click', function() {
  alert('Button clicked!');
});
```

---

## DOM Traversal and Manipulation
DOM traversal allows you to navigate through parent, child, and sibling elements, making it easier to manipulate the DOM structure.

Example:
```javascript
let parent = document.getElementById('parent');
let child = parent.firstElementChild; // Access first child element
let nextSibling = child.nextElementSibling; // Access the next sibling
let parentElement = child.parentElement; // Access the parent element
```

---

## DOM Creation: `createElement`, `appendChild`, etc.
Creating new elements dynamically and adding them to the DOM can be done using `createElement` and `appendChild`.

Example:
```javascript
let newDiv = document.createElement('div');
newDiv.textContent = 'This is a new div element';

// Append the new div to the body
document.body.appendChild(newDiv);
```

---

## Working with Forms and Validation
Forms can be manipulated and validated using JavaScript. Access form elements, get values, and validate user input.

Example:
```javascript
let form = document.getElementById('myForm');
let nameInput = document.getElementById('name');

// Access form values
let nameValue = nameInput.value;

// Simple validation
form.addEventListener('submit', function(event) {
  if (nameValue === '') {
    event.preventDefault();
    alert('Name is required!');
  }
});
```

---

## Local Storage and Session Storage
Local Storage and Session Storage are used for storing data in the browser. Local Storage persists data even when the browser is closed, while Session Storage is cleared when the browser session ends.

Example:
```javascript
// Storing data in localStorage
localStorage.setItem('username', 'JohnDoe');

// Retrieving data from localStorage
let username = localStorage.getItem('username');
console.log(username);  // JohnDoe

// Storing data in sessionStorage
sessionStorage.setItem('sessionKey', 'abc123');

// Retrieving data from sessionStorage
let sessionKey = sessionStorage.getItem('sessionKey');
console.log(sessionKey);  // abc123
```

---

## The Fetch API
The Fetch API allows you to make network requests, such as fetching data from a server. It returns a promise, enabling easy handling of asynchronous operations.

Example:
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log('Error:', error));
```

---

## Geolocation and Device APIs
The Geolocation API allows you to retrieve the user's location, while the Device APIs can provide information about the user's device, such as screen size or battery status.

Example:
```javascript
// Using Geolocation API to get the user's position
navigator.geolocation.getCurrentPosition(function(position) {
  console.log('Latitude:', position.coords.latitude);
  console.log('Longitude:', position.coords.longitude);
});

// Using Device API for screen size
console.log('Screen width:', window.screen.width);
console.log('Screen height:', window.screen.height);
```

---

## Conclusion

### Key Takeaways:
1. DOM elements can be selected and manipulated using methods like `getElementById`, `querySelector`, and `querySelectorAll`.
2. You can modify element content, attributes, and styles dynamically using JavaScript.
3. Event handling with `addEventListener` allows you to respond to user interactions like clicks and input changes.
4. DOM traversal lets you navigate between elements, such as accessing parent, child, and sibling nodes.
5. You can create new elements dynamically using methods like `createElement` and `appendChild`.
6. Form data can be accessed and validated using JavaScript, providing better control over user input.
7. Local Storage and Session Storage enable the persistent storage of data in the browser.
8. The Fetch API simplifies making network requests and handling asynchronous data.
9. The Geolocation API and Device APIs provide access to location and device information.

### Practical Exercise:
1. Create a form with input fields for name and email, and validate the fields before submission.
2. Write a function to dynamically add a list of items (e.g., to-do items) to the DOM.
3. Use the Fetch API to fetch and display user data from a public API (e.g., JSONPlaceholder).
4. Store the user preferences (e.g., theme color) in localStorage and retrieve them when the page loads.
5. Implement a button that displays the user's current location using the Geolocation API.
