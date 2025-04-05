
# Tests et déploiement

Les tests garantissent que votre application fonctionne comme prévu, et le déploiement la met à disposition des utilisateurs. Ce module présente les tests unitaires/d'intégration, les tests de bout en bout, le déploiement automatisé et la publication d'applications à l'aide d'Expo et de TypeScript.

## Table des matières
- [Tests unitaires et d'intégration avec Jest et React Native Testing Library](#tests-unitaires-et-dintégration-avec-jest-et-react-native-testing-library)
- [Tests de bout en bout avec Detox](#tests-de-bout-en-bout-avec-detox)
- [Intégration et déploiement continus (CI/CD) avec Expo EAS](#intégration-et-déploiement-continus-cicd-avec-expo-eas)
- [Signature de code et déploiement sur l'App Store / Play Store](#signature-de-code-et-déploiement-sur-lapp-store--play-store)
- [Gestion des mises à jour OTA avec Expo Updates](#gestion-des-mises-à-jour-ota-avec-expo-updates)

---

## Tests unitaires et d'intégration avec Jest et React Native Testing Library

**Définition :**
Jest est un framework de test JavaScript, et React Native Testing Library (RNTL) permet de tester les composants en se concentrant sur le comportement de l'utilisateur.

**Exemple :**

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

Utilisez `jest.fn()` pour simuler des fonctions et tester l'interaction utilisateur.

---

## Tests de bout en bout avec Detox

**Définition :**
Detox permet de tester automatiquement le comportement réel de l'application sur des simulateurs/appareils.

**Conseils de configuration :**
- Nécessite une build de test séparée (`detox build`)
- Fonctionne avec Android et iOS
- S'exécute en CI pour une automatisation complète de l'appareil

**Exemple (test de base) :**

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

Exécutez avec `detox test` après avoir buildé l'application avec `detox build`.

---

## Intégration et déploiement continus (CI/CD) avec Expo EAS

**Définition :**
EAS (Expo Application Services) permet des builds et des déploiements dans le cloud pour les flux de travail de développement et de production.

**Configuration de base d'EAS :**

```bash
npx expo install eas-cli
eas login
eas build:configure
eas build --platform android
```

Ajoutez GitHub Actions ou d'autres outils CI pour automatiser les builds et les déploiements.

---

## Signature de code et déploiement sur l'App Store / Play Store

**Définition :**
La signature de code vérifie l'authenticité de l'application. EAS gère les informations d'identification de signature et les builds pour la soumission.

**Étapes :**
1. Générez/téléchargez les clés de signature avec `eas credentials`
2. Buildez avec `eas build`
3. Soumettez aux stores :

```bash
eas submit --platform android
eas submit --platform ios
```

Assurez-vous que `eas.json` inclut les profils de production pour les builds de release.

---

## Gestion des mises à jour OTA avec Expo Updates

**Définition :**
Les mises à jour OTA (Over-the-air) permettent la livraison instantanée des modifications de code sans resoumission aux app stores.

**Exemple :**

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

Configurez `updates` dans `app.json` pour contrôler le comportement des mises à jour.

---

## Conclusion

**Points clés à retenir :**
1. Utilisez Jest et RNTL pour tester la logique et les composants de manière isolée.
2. Detox permet des tests automatisés de l'application complète sur de vrais appareils.
3. EAS Build simplifie la CI/CD et les builds natifs.
4. Utilisez `eas submit` pour les déploiements sur les app stores avec la signature de code gérée par Expo.
5. Fournissez des mises à jour instantanément à l'aide des fonctionnalités OTA d'Expo.

**Exercice pratique :**
- Create a simple component (e.g., LoginForm).
- Write a unit test that checks if the login button triggers a mock function.
- Add an EAS build profile in `eas.json`.
- Add `Updates.checkForUpdateAsync()` to your app's startup logic.
