
# Stockage Hors Ligne dans React Native

Le stockage hors ligne dans React Native permet aux applications de stocker et de récupérer des données localement sur l'appareil, permettant à l'application de fonctionner de manière transparente même hors ligne. Ceci est essentiel pour offrir une expérience utilisateur fluide dans des environnements avec une connexion Internet intermittente ou inexistante.

## Table des Matières
- [Introduction](#introduction)
- [AsyncStorage](#asyncstorage)
- [Base de Données SQLite](#sqlite-database)
- [Base de Données Realm](#realm-database)
- [WatermelonDB](#watermelondb)
- [Conclusion](#conclusion)

## Introduction

Le stockage hors ligne dans React Native permet aux applications de rendre les données persistantes localement, garantissant que les utilisateurs peuvent continuer à interagir avec l'application sans connexion réseau. Il existe plusieurs bibliothèques et outils pour y parvenir, chacun offrant des avantages différents en fonction du cas d'utilisation.

## AsyncStorage

### Définition
`AsyncStorage` est un système de stockage asynchrone simple et non chiffré pour stocker des données sous forme de paires clé-valeur.

### Exemple
```javascript
import { AsyncStorage } from 'react-native';

// Sauvegarde des données
AsyncStorage.setItem('userToken', 'abc123');

// Récupération des données
AsyncStorage.getItem('userToken').then(value => console.log(value));
```

### Explication
`AsyncStorage` est idéal pour les besoins de stockage légers, tels que la sauvegarde des préférences ou des données de session. Il stocke les données sous forme de simples paires clé-valeur.

## Base de Données SQLite

### Définition
SQLite est un système de gestion de base de données relationnelle intégré aux applications mobiles pour le stockage de données structurées.

### Exemple
```javascript
import SQLite from 'react-native-sqlite-storage';

const db = SQLite.openDatabase({ name: 'app.db', location: 'default' });

// Création d'une table
db.transaction(tx => {
  tx.executeSql('CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY NOT NULL, name TEXT)');
});

// Insertion de données
db.transaction(tx => {
  tx.executeSql('INSERT INTO users (name) VALUES (?);', ['John']);
});
```

### Explication
SQLite est parfait pour les applications qui nécessitent des structures de données complexes avec des relations. Il prend en charge les requêtes SQL et peut gérer des ensembles de données plus volumineux.

## Base de Données Realm

### Définition
Realm est une base de données mobile qui offre un stockage local rapide et facile à utiliser avec prise en charge des données réactives et des requêtes complexes.

### Exemple
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

// Ajout de données
realm.write(() => {
  realm.create('User', { id: 1, name: 'Jane' });
});
```

### Explication
Realm est une alternative puissante à SQLite, avec des fonctionnalités telles que le stockage de données orienté objet et la synchronisation des données en temps réel.

## WatermelonDB

### Définition
WatermelonDB est une base de données haute performance, observable et flexible pour React Native, optimisée pour les applications complexes avec de grands ensembles de données.

### Exemple
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

// Ajout de données
db.collections.get('users').create(user => {
  user.name = 'Alice';
});
```

### Explication
WatermelonDB est conçu pour les applications complexes et à grande échelle où la performance et la réactivité sont essentielles. Il gère efficacement de grands ensembles de données avec un minimum de décalage.

## Conclusion

### Points Clés :
1. React Native offre plusieurs options de stockage hors ligne comme AsyncStorage, SQLite, Realm et WatermelonDB.
2. `AsyncStorage` est idéal pour le stockage léger de paires clé-valeur.
3. SQLite offre une prise en charge des bases de données relationnelles et est préférable pour les données structurées.
4. Realm permet le stockage orienté objet et la synchronisation en temps réel.
5. WatermelonDB est optimisé pour les applications haute performance avec des besoins de données complexes.

### Exercice Pratique
Créez une application React Native qui permet à un utilisateur de saisir et d'enregistrer le nom de son livre préféré à l'aide d'`AsyncStorage`. Assurez-vous que les données du livre persistent même après la fermeture et la réouverture de l'application.
