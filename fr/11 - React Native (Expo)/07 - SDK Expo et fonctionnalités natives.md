
# SDK Expo et fonctionnalités natives

Expo donne accès aux capacités natives de l'appareil en utilisant JavaScript via son riche SDK. Ce module explore comment utiliser les modules Expo populaires, gérer les permissions, gérer le comportement natif et étendre les applications Expo avec des plugins personnalisés.

## Table des matières
- [Utilisation des modules Expo (Camera, ImagePicker, Notifications)](#utilisation-des-modules-expo-camera-imagepicker-notifications)
- [Gestion des permissions et du stockage sécurisé](#gestion-des-permissions-et-du-stockage-sécurisé)
- [Tâches en arrière-plan et événements du cycle de vie de l'application](#tâches-en-arrière-plan-et-événements-du-cycle-de-vie-de-lapplication)
- [Notifications push avec Expo](#notifications-push-avec-expo)
- [Personnalisation du code natif avec les plugins de configuration Expo](#personnalisation-du-code-natif-avec-les-plugins-de-configuration-expo)

---

## Utilisation des modules Expo (Camera, ImagePicker, Notifications)

**Définition :**
Expo fournit des API de haut niveau pour accéder au matériel de l'appareil tel que l'appareil photo, la bibliothèque multimédia et le système de notification.

**Exemple (Image Picker) :**

```tsx
import * as ImagePicker from 'expo-image-picker';

const pickImage = async () => {
  const result = await ImagePicker.launchImageLibraryAsync({ allowsEditing: true });
  if (!result.canceled) {
    console.log(result.assets[0].uri);
  }
};
```

Utilisez les modules tels que `expo-camera`, `expo-media-library` et `expo-notifications` selon vos besoins.

---

## Gestion des permissions et du stockage sécurisé

**Définition :**
Les permissions doivent être demandées au moment de l'exécution pour des fonctionnalités telles que l'appareil photo ou les notifications. `expo-secure-store` est utilisé pour stocker les données sensibles en toute sécurité.

**Exemple (Permissions + SecureStore) :**

```tsx
import * as Permissions from 'expo-permissions';
import * as SecureStore from 'expo-secure-store';

const requestCameraPermission = async () => {
  const { status } = await Permissions.askAsync(Permissions.CAMERA);
  if (status === 'granted') {
    console.log('Camera permission granted');
  }
};

await SecureStore.setItemAsync('token', 'abc123');
const token = await SecureStore.getItemAsync('token');
```

Vérifiez et gérez toujours les permissions de manière appropriée.

---

## Tâches en arrière-plan et événements du cycle de vie de l'application

**Définition :**
Expo permet la planification de tâches en arrière-plan et la gestion des événements du cycle de vie à l'aide de `expo-task-manager` et de l'API AppState.

**Exemple (AppState) :**

```tsx
import { AppState } from 'react-native';
import { useEffect } from 'react';

useEffect(() => {
  const subscription = AppState.addEventListener('change', state => {
    console.log('App is now', state);
  });
  return () => subscription.remove();
}, []);
```

Utilisez `expo-background-fetch` ou `expo-task-manager` pour les tâches en arrière-plan.

---

## Notifications push avec Expo

**Définition :**
Expo facilite l'envoi et la réception de notifications push à l'aide de son propre service de notifications push.

**Exemple :**

```tsx
import * as Notifications from 'expo-notifications';
import * as Device from 'expo-device';

const registerForPushNotifications = async () => {
  const { status } = await Notifications.requestPermissionsAsync();
  if (status !== 'granted') return;

  const token = (await Notifications.getExpoPushTokenAsync()).data;
  console.log('Expo Push Token:', token);
};
```

Vous pouvez envoyer des notifications à l'aide de l'API de notification d'Expo ou du SDK serveur.

---

## Personnalisation du code natif avec les plugins de configuration Expo

**Définition :**
Les plugins de configuration Expo vous permettent de modifier les configurations natives (comme `AndroidManifest.xml` ou `Info.plist`) sans éjecter d'Expo.

**Exemple :**

```js
// app.plugin.js
module.exports = function withCustomConfig(config) {
  return {
    ...config,
    android: {
      ...config.android,
      permissions: ['CAMERA'],
    },
  };
};
```

Ajoutez-le à `app.json` :

```json
{
  "plugins": ["./app.plugin"]
}
```

Utilisez les plugins de configuration pour étendre Expo en toute sécurité sans perdre les avantages du flux de travail géré.

---

## Conclusion

**Points clés à retenir :**
1. Le SDK Expo donne accès aux fonctionnalités de l'appareil avec une configuration minimale.
2. Gérez toujours les permissions d'exécution pour des applications sécurisées et stables.
3. Utilisez les API AppState et de tâches en arrière-plan pour gérer les événements du cycle de vie.
4. Les notifications push Expo sont simples à implémenter et multiplateformes.
5. Les plugins de configuration permettent une personnalisation native tout en restant dans le flux de travail géré.

**Exercice pratique :**
- Create a screen that:
  - Requests camera permission.
  - Picks an image from the media library.
  - Stores the image URI in secure storage.
  - Retrieves it and displays it when the screen mounts.
