
# Testing and Deployment

Testing ensures your app works as expected, and deployment brings it to users. This module walks through unit/integration testing, end-to-end testing, automated deployment, and publishing apps using Expo and TypeScript.

## Table of Contents
- [Unit and Integration Testing with Jest and React Native Testing Library](#unit-and-integration-testing-with-jest-and-react-native-testing-library)
- [End-to-End Testing with Detox](#end-to-end-testing-with-detox)
- [Continuous Integration and Deployment (CI/CD) with Expo EAS](#continuous-integration-and-deployment-cicd-with-expo-eas)
- [Code Signing and App Store / Play Store Deployment](#code-signing-and-app-store--play-store-deployment)
- [Handling OTA Updates with Expo Updates](#handling-ota-updates-with-expo-updates)

---

## Unit and Integration Testing with Jest and React Native Testing Library

**Definition:**  
Jest is a JavaScript testing framework, and React Native Testing Library (RNTL) allows testing components with a focus on user behavior.

**Example:**

```tsx
// MyButton.tsx
export const MyButton = ({ onPress }: { onPress: () => void }) => (
  <Button title="Press me" onPress={onPress} />
);

// MyButton.test.tsx
import { render, fireEvent } from '@testing-library/react-native';
import { MyButton } from './MyButton';

test('calls onPress when tapped', () => {
  const mock = jest.fn();
  const { getByText } = render(<MyButton onPress={mock} />);
  fireEvent.press(getByText('Press me'));
  expect(mock).toHaveBeenCalled();
});
```

Use `jest.fn()` to mock functions and test user interaction.

---

## End-to-End Testing with Detox

**Definition:**  
Detox enables automated testing of real app behavior on simulators/devices.

**Setup Tips:**
- Requires a separate test build (`detox build`)
- Works with Android and iOS
- Runs in CI for full-device automation

**Example (basic test):**

```js
// e2e/firstTest.e2e.js
describe('Example', () => {
  beforeAll(async () => {
    await device.launchApp();
  });

  it('should show welcome screen', async () => {
    await expect(element(by.text('Welcome'))).toBeVisible();
  });
});
```

Run with `detox test` after building the app with `detox build`.

---

## Continuous Integration and Deployment (CI/CD) with Expo EAS

**Definition:**  
EAS (Expo Application Services) enables cloud builds and deployments for both development and production workflows.

**Basic EAS Setup:**

```bash
npx expo install eas-cli
eas login
eas build:configure
eas build --platform android
```

Add GitHub Actions or other CI tools to automate builds and deployments.

---

## Code Signing and App Store / Play Store Deployment

**Definition:**  
Code signing verifies app authenticity. EAS handles signing credentials and builds for submission.

**Steps:**
1. Generate/upload signing keys with `eas credentials`
2. Build with `eas build`
3. Submit to stores:

```bash
eas submit --platform android
eas submit --platform ios
```

Make sure `eas.json` includes production profiles for release builds.

---

## Handling OTA Updates with Expo Updates

**Definition:**  
Over-the-air (OTA) updates allow instant delivery of code changes without re-submitting to app stores.

**Example:**

```ts
import * as Updates from 'expo-updates';

const checkForUpdates = async () => {
  const update = await Updates.checkForUpdateAsync();
  if (update.isAvailable) {
    await Updates.fetchUpdateAsync();
    await Updates.reloadAsync();
  }
};
```

Configure `updates` in `app.json` to control update behavior.

---

## Conclusion

**Key Takeaways:**
1. Use Jest and RNTL for testing logic and components in isolation.
2. Detox enables automated full-app testing on real devices.
3. EAS Build simplifies CI/CD and native builds.
4. Use `eas submit` for app store deployments with code signing handled by Expo.
5. Deliver updates instantly using Expo OTA features.

**Practical Exercise:**
- Create a simple component (e.g., LoginForm).
- Write a unit test that checks if the login button triggers a mock function.
- Add an EAS build profile in `eas.json`.
- Add `Updates.checkForUpdateAsync()` to your app's startup logic.
