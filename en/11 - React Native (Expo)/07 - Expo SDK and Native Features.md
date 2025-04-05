
# Expo SDK and Native Features

Expo provides access to native device capabilities using JavaScript through its rich SDK. This module explores how to use popular Expo modules, handle permissions, manage native behavior, and extend Expo apps with custom plugins.

## Table of Contents
- [Using Expo Modules (Camera, ImagePicker, Notifications)](#using-expo-modules-camera-imagepicker-notifications)
- [Handling Permissions and Secure Storage](#handling-permissions-and-secure-storage)
- [Background Tasks and App Lifecycle Events](#background-tasks-and-app-lifecycle-events)
- [Push Notifications with Expo](#push-notifications-with-expo)
- [Customizing Native Code with Expo Config Plugins](#customizing-native-code-with-expo-config-plugins)

---

## Using Expo Modules (Camera, ImagePicker, Notifications)

**Definition:**  
Expo provides high-level APIs for accessing device hardware such as camera, media library, and notification system.

**Example (Image Picker):**

```tsx
import * as ImagePicker from 'expo-image-picker';

const pickImage = async () => {
  const result = await ImagePicker.launchImageLibraryAsync({ allowsEditing: true });
  if (!result.canceled) {
    console.log(result.assets[0].uri);
  }
};
```

Use modules like `expo-camera`, `expo-media-library`, and `expo-notifications` as needed.

---

## Handling Permissions and Secure Storage

**Definition:**  
Permissions must be requested at runtime for features like camera or notifications. `expo-secure-store` is used for storing sensitive data securely.

**Example (Permissions + SecureStore):**

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

Always check and handle permissions gracefully.

---

## Background Tasks and App Lifecycle Events

**Definition:**  
Expo allows background task scheduling and handling of lifecycle events using `expo-task-manager` and AppState API.

**Example (AppState):**

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

Use `expo-background-fetch` or `expo-task-manager` for background jobs.

---

## Push Notifications with Expo

**Definition:**  
Expo makes it easy to send and receive push notifications using its own push notification service.

**Example:**

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

You can send notifications using Expo's notification API or server SDK.

---

## Customizing Native Code with Expo Config Plugins

**Definition:**  
Expo config plugins allow you to modify native configurations (like `AndroidManifest.xml` or `Info.plist`) without ejecting from Expo.

**Example:**

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

Add it to `app.json`:

```json
{
  "plugins": ["./app.plugin"]
}
```

Use config plugins to safely extend Expo without losing managed workflow benefits.

---

## Conclusion

**Key Takeaways:**
1. Expo SDK provides access to device features with minimal setup.
2. Always handle runtime permissions for secure and stable apps.
3. Use AppState and background task APIs to manage lifecycle events.
4. Expo Push Notifications are simple to implement and cross-platform.
5. Config plugins allow native customization while staying in the managed workflow.

**Practical Exercise:**
- Create a screen that:
  - Requests camera permission.
  - Picks an image from the media library.
  - Stores the image URI in secure storage.
  - Retrieves it and displays it when the screen mounts.
