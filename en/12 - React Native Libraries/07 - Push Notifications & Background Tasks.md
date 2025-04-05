
# Push Notifications & Background Tasks in React Native

**Introduction**  
This course covers integrating push notifications, background tasks, and sensor handling in React Native apps. Learn how to send push notifications, manage background tasks efficiently, and optimize performance for an enhanced user experience.

## Table of Contents  
1. [Push Notifications in React Native](#push-notifications-in-react-native)  
    - [Setting Up Push Notifications with expo-notifications](#setting-up-push-notifications-with-expo-notifications)  
    - [Handling Notification Events & Deep Linking](#handling-notification-events--deep-linking)  
2. [Background Services & Sensors](#background-services--sensors)  
    - [Working with Sensors using expo-sensors](#working-with-sensors-using-expo-sensors)  
    - [Running Background Tasks in React Native](#running-background-tasks-in-react-native)  
3. [Optimizing Performance & User Experience](#optimizing-performance--user-experience)  
    - [Managing Battery Consumption for Background Tasks](#managing-battery-consumption-for-background-tasks)  
    - [Handling Offline & Background Syncing](#handling-offline--background-syncing)  

---

## Push Notifications in React Native

### Setting Up Push Notifications with expo-notifications
**expo-notifications** allows you to send and receive push notifications in your React Native app. It integrates seamlessly with Expo and other services like Firebase Cloud Messaging.

**Example**  
```bash
expo install expo-notifications
```

```jsx
import * as Notifications from 'expo-notifications';
import { useEffect } from 'react';

const setupPushNotifications = async () => {
  // Request permissions
  await Notifications.requestPermissionsAsync();

  // Set notification handler
  Notifications.addNotificationReceivedListener(notification => {
    console.log('Notification received:', notification);
  });
};

useEffect(() => {
  setupPushNotifications();
}, []);
```

### Handling Notification Events & Deep Linking
Push notifications can trigger actions like deep linking or displaying in-app alerts when the user interacts with them.

**Example**  
Handling notification response and deep linking:
```jsx
Notifications.addNotificationResponseReceivedListener(response => {
  const { notification, actionIdentifier } = response;
  // Handle deep link or action
  if (actionIdentifier === 'open-app') {
    console.log('Deep link action triggered!');
    // Handle deep link navigation
  }
});
```

---

## Background Services & Sensors

### Working with Sensors using expo-sensors
**expo-sensors** allows access to device sensors like the accelerometer, gyroscope, and magnetometer. It’s useful for apps that rely on real-time sensor data.

**Example**  
Using the accelerometer to detect device movement:
```bash
expo install expo-sensors
```

```jsx
import { Accelerometer } from 'expo-sensors';

const subscribeToAccelerometer = () => {
  Accelerometer.addListener(accelerometerData => {
    console.log(accelerometerData);
  });
};

useEffect(() => {
  subscribeToAccelerometer();
  return () => {
    Accelerometer.removeAllListeners();
  };
}, []);
```

### Running Background Tasks in React Native
Running tasks in the background is essential for processes like location tracking, data sync, or ongoing notifications. Use libraries like **expo-task-manager** to execute tasks in the background.

**Example**  
Setting up a background task:
```bash
expo install expo-task-manager
```

```jsx
import * as TaskManager from 'expo-task-manager';
import * as BackgroundFetch from 'expo-background-fetch';

const BACKGROUND_TASK = 'background-fetch-task';

TaskManager.defineTask(BACKGROUND_TASK, () => {
  console.log('Background task executed!');
  return BackgroundFetch.Result.NewData;
});

BackgroundFetch.registerTaskAsync(BACKGROUND_TASK, {
  minimumInterval: 15 * 60, // Fetch every 15 minutes
});
```

---

## Optimizing Performance & User Experience

### Managing Battery Consumption for Background Tasks
Background tasks can drain the battery if not optimized properly. Using efficient intervals, throttling updates, and offloading tasks when the app is in the background are important techniques.

**Example**  
Reducing background task frequency to save battery:
```jsx
BackgroundFetch.registerTaskAsync(BACKGROUND_TASK, {
  minimumInterval: 60 * 60, // Only fetch once every hour
});
```

### Handling Offline & Background Syncing
Handling offline scenarios and syncing data in the background is critical for apps that rely on user data. Use background tasks to sync data when the network becomes available.

**Example**  
Syncing data in the background when online:
```jsx
import * as Network from 'expo-network';

const syncDataWhenOnline = async () => {
  const isOnline = await Network.getNetworkStateAsync();
  if (isOnline.isConnected) {
    // Perform data sync operations
    console.log('Syncing data...');
  } else {
    console.log('No internet connection');
  }
};

// Use background task to periodically sync
TaskManager.defineTask(BACKGROUND_TASK, syncDataWhenOnline);
```

---

## Conclusion

### Key Takeaways  
1. **expo-notifications** allows seamless push notifications integration and supports deep linking.  
2. **expo-sensors** provides access to real-time device sensors like the accelerometer, useful for sensor-based apps.  
3. Background tasks can be managed efficiently with **expo-task-manager** for operations like data syncing and location tracking.  
4. Optimize battery consumption by reducing the frequency of background tasks and syncing data only when necessary.  
5. Handle offline data syncing effectively using background tasks and network state checks.

### Practical Exercise  
1. Set up push notifications with **expo-notifications** and handle notification events like deep linking.  
2. Create an app that uses the accelerometer data and triggers actions based on device movement.  
3. Implement background tasks using **expo-task-manager** to sync data when the app is in the background, and optimize it for battery consumption.
