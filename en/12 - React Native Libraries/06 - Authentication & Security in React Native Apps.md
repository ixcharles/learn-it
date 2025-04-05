
# Authentication & Security in React Native Apps

**Introduction**  
This course covers essential techniques for handling user authentication and securing data in React Native apps. You will learn how to implement OAuth authentication, Firebase authentication, secure storage, and follow best practices for security.

## Table of Contents  
1. [Authentication Basics](#authentication-basics)  
    - [Authentication Strategies in Mobile Apps](#authentication-strategies-in-mobile-apps)  
    - [Setting Up OAuth with expo-auth-session](#setting-up-oauth-with-expo-auth-session)  
2. [Advanced Authentication Techniques](#advanced-authentication-techniques)  
    - [Firebase Authentication with react-native-firebase/auth](#firebase-authentication-with-react-native-firebase-auth)  
    - [Securing User Credentials with react-native-keychain](#securing-user-credentials-with-react-native-keychain)  
3. [Security Best Practices](#security-best-practices)  
    - [Implementing Secure Storage & Encryption](#implementing-secure-storage--encryption)  
    - [Protecting APIs & User Data in React Native Apps](#protecting-apis--user-data-in-react-native-apps)  

---

## Authentication Basics

### Authentication Strategies in Mobile Apps
Mobile apps typically use **OAuth**, **JWT tokens**, and **Social Media Logins** to authenticate users securely. OAuth allows third-party services (Google, Facebook, etc.) to authenticate users without storing passwords locally.

**Example**  
OAuth flow using **expo-auth-session**:
```bash
expo install expo-auth-session
```
```jsx
import * as AuthSession from 'expo-auth-session';

const authenticateUser = async () => {
  const result = await AuthSession.startAsync({
    authUrl: 'https://auth-server.com/oauth',
  });

  if (result.type === 'success') {
    console.log('User authenticated:', result.params);
  }
};
```

### Setting Up OAuth with expo-auth-session
**expo-auth-session** simplifies OAuth integration with third-party authentication services like Google and Facebook.

**Example**  
```jsx
import * as AuthSession from 'expo-auth-session';

const oauthRedirectUri = AuthSession.makeRedirectUri();

const authenticateWithGoogle = async () => {
  const result = await AuthSession.startAsync({
    authUrl: `https://accounts.google.com/o/oauth2/v2/auth?client_id=YOUR_CLIENT_ID&redirect_uri=${oauthRedirectUri}&response_type=token&scope=email`,
  });

  if (result.type === 'success') {
    console.log('Access Token:', result.params.access_token);
  }
};
```

---

## Advanced Authentication Techniques

### Firebase Authentication with react-native-firebase/auth
**react-native-firebase/auth** allows for easy integration with Firebase authentication services, including email/password login, social logins, and more.

**Example**  
```bash
npm install @react-native-firebase/auth
```

```jsx
import auth from '@react-native-firebase/auth';

const loginUser = async (email, password) => {
  try {
    const userCredential = await auth().signInWithEmailAndPassword(email, password);
    console.log('User signed in:', userCredential.user);
  } catch (error) {
    console.log('Error logging in:', error);
  }
};
```

### Securing User Credentials with react-native-keychain
**react-native-keychain** is used to store sensitive data securely on the device, such as passwords or authentication tokens, using the device's secure storage system.

**Example**  
```bash
npm install react-native-keychain
```

```jsx
import * as Keychain from 'react-native-keychain';

const storeCredentials = async (username, password) => {
  await Keychain.setGenericPassword(username, password);
};

const getCredentials = async () => {
  const credentials = await Keychain.getGenericPassword();
  console.log('Stored credentials:', credentials);
};
```

---

## Security Best Practices

### Implementing Secure Storage & Encryption
Using **react-native-keychain** for secure storage and **encryption** is essential for protecting sensitive information such as authentication tokens and user credentials.

**Example**  
Storing an encrypted token:
```jsx
import * as Keychain from 'react-native-keychain';
import { AES } from 'crypto-js';

const secureStoreToken = async (token) => {
  const encryptedToken = AES.encrypt(token, 'secret-key').toString();
  await Keychain.setGenericPassword('user', encryptedToken);
};

const secureRetrieveToken = async () => {
  const credentials = await Keychain.getGenericPassword();
  const bytes = AES.decrypt(credentials.password, 'secret-key');
  const decryptedToken = bytes.toString(CryptoJS.enc.Utf8);
  console.log('Decrypted token:', decryptedToken);
};
```

### Protecting APIs & User Data in React Native Apps
When building apps, it’s important to protect APIs and sensitive user data. This can be achieved by:
- Encrypting data before storage or transmission.
- Using secure, token-based authentication (JWT) for API communication.
- Implementing proper role-based access control (RBAC) for sensitive data.

**Example**  
Encrypting API requests with **JWT tokens**:
```jsx
import axios from 'axios';

const fetchData = async () => {
  const token = await Keychain.getGenericPassword();
  const response = await axios.get('https://api.example.com/data', {
    headers: {
      Authorization: `Bearer ${token}`,
    },
  });
  console.log(response.data);
};
```

---

## Conclusion

### Key Takeaways  
1. **expo-auth-session** allows you to integrate OAuth for third-party authentication services like Google and Facebook.  
2. **react-native-firebase/auth** simplifies Firebase authentication for mobile apps.  
3. **react-native-keychain** provides a secure way to store user credentials and sensitive data on the device.  
4. **Encryption** and **secure storage** are essential for protecting sensitive user data in mobile apps.  
5. Protect APIs and user data by using secure transmission methods like JWT tokens and encrypting sensitive information.

### Practical Exercise  
1. Implement email/password authentication using **react-native-firebase/auth**.  
2. Use **expo-auth-session** to authenticate users with Google OAuth.  
3. Securely store authentication tokens using **react-native-keychain** and implement encryption for storing sensitive data.
