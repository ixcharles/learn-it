
# JavaScript and the Web

This course explores how JavaScript interacts with the browser and the web. You'll learn to handle HTTP requests, use APIs like Fetch and WebSockets, and manage web storage to build dynamic web applications.

## Table of Contents
1. [Introduction to the Browser Environment](#introduction-to-the-browser-environment)
2. [HTTP and Fetch API](#http-and-fetch-api)
3. [Understanding REST and GraphQL](#understanding-rest-and-graphql)
4. [JSON: Parsing and Stringifying](#json-parsing-and-stringifying)
5. [WebSockets for Real-Time Communication](#websockets-for-real-time-communication)
6. [Web Storage API: LocalStorage and SessionStorage](#web-storage-api-localstorage-and-sessionstorage)

---

## Introduction to the Browser Environment
The browser environment allows JavaScript to interact with the DOM, handle events, and communicate with the server. Key components:
- **DOM (Document Object Model)**: Represents the structure of an HTML document.
- **Event Loop**: Ensures JavaScript runs asynchronously without blocking the main thread.
- **Browser APIs**: Provide interfaces to interact with the browser, like `localStorage`, `fetch()`, and `setTimeout()`.

---

## HTTP and Fetch API
The **Fetch API** provides a modern way to make HTTP requests, replacing older methods like `XMLHttpRequest`. It returns Promises and is easy to use with `async/await`.

Example:
```javascript
// Making a GET request with Fetch
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Using `async/await`:
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

## Understanding REST and GraphQL
- **REST (Representational State Transfer)**: An architectural style that uses HTTP methods (GET, POST, PUT, DELETE) for communication between clients and servers. REST APIs return data in formats like JSON or XML.
- **GraphQL**: A query language for APIs, allowing clients to request specific data. Unlike REST, which exposes multiple endpoints, GraphQL exposes a single endpoint for all data queries.

Example of a REST API call:
```javascript
fetch('https://api.example.com/items')
  .then(response => response.json())
  .then(data => console.log(data));
```

Example of a GraphQL request:
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

## JSON: Parsing and Stringifying
JSON (JavaScript Object Notation) is a lightweight data format for storing and exchanging data between a server and a client. 

- **`JSON.parse()`**: Converts a JSON string into a JavaScript object.
- **`JSON.stringify()`**: Converts a JavaScript object into a JSON string.

Example:
```javascript
// Parsing JSON
let jsonString = '{"name":"Alice","age":25}';
let parsedData = JSON.parse(jsonString);
console.log(parsedData.name);  // Alice

// Stringifying an Object
let obj = { name: 'Bob', age: 30 };
let jsonStringified = JSON.stringify(obj);
console.log(jsonStringified);  // '{"name":"Bob","age":30}'
```

---

## WebSockets for Real-Time Communication
WebSockets provide full-duplex communication channels over a single TCP connection, ideal for real-time applications like chat apps or live data feeds.

Example:
```javascript
// Creating a WebSocket connection
const socket = new WebSocket('wss://example.com/socket');

// Listening for messages
socket.onmessage = function(event) {
  console.log('Message from server:', event.data);
};

// Sending a message
socket.send('Hello, server!');
```

---

## Web Storage API: LocalStorage and SessionStorage
The Web Storage API provides mechanisms for storing data on the client side. 

- **LocalStorage**: Stores data with no expiration date, accessible across sessions.
- **SessionStorage**: Stores data only for the duration of the page session.

Example using LocalStorage:
```javascript
// Storing data
localStorage.setItem('username', 'Alice');

// Retrieving data
let username = localStorage.getItem('username');
console.log(username);  // Alice

// Removing data
localStorage.removeItem('username');
```

Example using SessionStorage:
```javascript
// Storing data
sessionStorage.setItem('sessionID', '12345');

// Retrieving data
let sessionID = sessionStorage.getItem('sessionID');
console.log(sessionID);  // 12345
```

---

## Conclusion

### Key Takeaways:
1. **Browser Environment**: JavaScript interacts with the browser through the DOM and APIs like `localStorage` and `fetch()`.
2. **HTTP and Fetch API**: Use `fetch()` to make HTTP requests and handle responses with Promises and `async/await`.
3. **REST vs. GraphQL**: REST APIs use multiple endpoints, while GraphQL uses a single endpoint for more flexible data queries.
4. **JSON**: Use `JSON.parse()` to parse JSON strings and `JSON.stringify()` to convert objects to JSON.
5. **WebSockets**: Enables real-time communication for applications that need instant updates, like chat apps.
6. **Web Storage**: Store data on the client side with `localStorage` (persistent) and `sessionStorage` (session-based).

### Practical Exercise:
1. Fetch data from a REST API and display it in the console. Then, implement the same functionality using GraphQL.
2. Create a WebSocket connection to a server and send a message upon a button click.
3. Implement local storage functionality to save and retrieve user preferences (like theme color) across page reloads.
4. Parse and stringify JSON data, and log it to the console.
