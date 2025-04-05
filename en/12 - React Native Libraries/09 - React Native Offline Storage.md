
# React Native Offline Storage

React Native Offline Storage enables applications to store and retrieve data locally on the device, allowing the app to function seamlessly even when offline. This is essential for providing a smooth user experience in environments with intermittent or no internet connection.

## Table of Contents
- [Introduction](#introduction)
- [AsyncStorage](#asyncstorage)
- [SQLite Database](#sqlite-database)
- [Realm Database](#realm-database)
- [WatermelonDB](#watermelondb)
- [Conclusion](#conclusion)

## Introduction

Offline storage in React Native allows apps to persist data locally, ensuring users can continue interacting with the app without a network connection. There are several libraries and tools to achieve this, each offering different advantages based on the use case.

## AsyncStorage

### Definition
`AsyncStorage` is a simple, unencrypted, asynchronous storage system for storing data in key-value pairs.

### Example
```javascript
import { AsyncStorage } from 'react-native';

// Saving data
AsyncStorage.setItem('userToken', 'abc123');

// Retrieving data
AsyncStorage.getItem('userToken').then(value => console.log(value));
```

### Explanation
`AsyncStorage` is ideal for lightweight storage needs, such as saving preferences or session data. It stores data as simple key-value pairs.

## SQLite Database

### Definition
SQLite is a relational database management system embedded into mobile apps for structured data storage.

### Example
```javascript
import SQLite from 'react-native-sqlite-storage';

const db = SQLite.openDatabase({ name: 'app.db', location: 'default' });

// Creating a table
db.transaction(tx => {
  tx.executeSql('CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY NOT NULL, name TEXT)');
});

// Inserting data
db.transaction(tx => {
  tx.executeSql('INSERT INTO users (name) VALUES (?);', ['John']);
});
```

### Explanation
SQLite is perfect for apps that require complex data structures with relationships. It supports SQL queries and can handle larger datasets.

## Realm Database

### Definition
Realm is a mobile database that offers fast and easy-to-use local storage with support for reactive data and complex queries.

### Example
```javascript
import Realm from 'realm';

const UserSchema = {
  name: 'User',
  properties: {
    id: 'int',
    name: 'string',
  },
};

const realm = new Realm({ schema: [UserSchema] });

// Adding data
realm.write(() => {
  realm.create('User', { id: 1, name: 'Jane' });
});
```

### Explanation
Realm is a powerful alternative to SQLite, with features like object-oriented data storage and real-time data synchronization.

## WatermelonDB

### Definition
WatermelonDB is a high-performance, observable, and flexible database for React Native, optimized for complex applications with large datasets.

### Example
```javascript
import { database } from '@nozbe/watermelondb';
import { appSchema, tableSchema } from '@nozbe/watermelondb/Schema';
import { Model } from '@nozbe/watermelondb';

const userSchema = tableSchema({
  name: 'users',
  columns: [{ name: 'name', type: 'string' }],
});

const db = database({
  schema: appSchema({
    version: 1,
    tables: [userSchema],
  }),
});

// Adding data
db.collections.get('users').create(user => {
  user.name = 'Alice';
});
```

### Explanation
WatermelonDB is designed for complex, large-scale apps where performance and reactiveness are critical. It efficiently handles large datasets with minimal lag.

## Conclusion

### Key Takeaways:
1. React Native provides multiple offline storage options like AsyncStorage, SQLite, Realm, and WatermelonDB.
2. `AsyncStorage` is ideal for lightweight, key-value pair storage.
3. SQLite offers relational database support and is best for structured data.
4. Realm allows object-oriented storage and real-time synchronization.
5. WatermelonDB is optimized for high-performance apps with complex data needs.

### Practical Exercise
Create a React Native app that allows a user to input and save their favorite book's name using `AsyncStorage`. Ensure that the book data persists even after the app is closed and reopened.
