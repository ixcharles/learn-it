
# Optimisation des performances et débogage

L'optimisation des performances et le débogage efficace sont essentiels pour une expérience utilisateur fluide dans les applications React Native de qualité production. Ce module se concentre sur l'efficacité du rendu, la gestion de la mémoire, les outils de débogage et le profilage réseau à l'aide de TypeScript.

## Table des matières
- [Optimisation des rendus et prévention des re-rendus](#optimisation-des-rendus-et-prévention-des-re-rendus)
- [Gestion de la mémoire et surveillance des performances](#gestion-de-la-mémoire-et-surveillance-des-performances)
- [Utilisation d'Hermes pour une exécution plus rapide](#utilisation-dhermes-pour-une-exécution-plus-rapide)
- [Outils de débogage (React DevTools, Flipper, débogage de la console)](#outils-de-débogage-react-devtools-flipper-débogage-de-la-console)
- [Profilage et optimisation des requêtes réseau](#profilage-et-optimisation-des-requêtes-réseau)

---

## Optimisation des rendus et prévention des re-rendus

**Définition :**
Empêchez les re-rendus de composants inutiles en utilisant la mémöisation, les références stables et les listes virtualisées.

**Exemple :**

```tsx
import React, { memo, useCallback, useState } from 'react';

type ButtonProps = { onPress: () => void };
const MyButton = memo(({ onPress }: ButtonProps) => <Button title="Tap" onPress={onPress} />);

const Parent = () => {
  const [count, setCount] = useState(0);
  const handlePress = useCallback(() => setCount(c => c + 1), []);
  return <MyButton onPress={handlePress} />;
};
```

Utilisez `React.memo`, `useCallback`, `useMemo` pour éviter les mises à jour inutiles.

---

## Gestion de la mémoire et surveillance des performances

**Définition :**
Libérez les ressources inutilisées et surveillez l'utilisation de la mémoire pour éviter les fuites et les plantages sur les appareils bas de gamme.

**Conseils :**
- Effacez les minuteurs, les abonnements et les écouteurs dans le nettoyage `useEffect`.
- Utilisez FlatList avec `initialNumToRender` et `windowSize` pour les grandes listes.
- Surveillez la mémoire avec l'onglet Performance de Flipper ou le Profileur d'Android Studio.

**Exemple de nettoyage :**

```tsx
useEffect(() => {
  const id = setInterval(() => console.log('tick'), 1000);
  return () => clearInterval(id);
}, []);
```

---

## Utilisation d'Hermes pour une exécution plus rapide

**Définition :**
Hermes est un moteur JavaScript léger optimisé pour React Native sur Android (également pris en charge sur iOS via Expo SDK 49+).

**Comment activer dans Expo :**

```json
// app.json
{
  "expo": {
    "jsEngine": "hermes"
  }
}
```

Hermes améliore le temps de démarrage, l'utilisation de la mémoire et les performances en production.

---

## Outils de débogage (React DevTools, Flipper, débogage de la console)

**Définition :**
React DevTools et Flipper sont des outils essentiels pour inspecter les arborescences de composants, l'état, les journaux et les performances en temps réel.

**Outils :**
- **React DevTools :** Inspectez la hiérarchie des composants et les props/l'état.
- **Flipper :** Inspectez les journaux, les performances, React DevTools, le réseau.
- **Console :** Utilisez `console.log`, `console.table`, `console.warn` pour un aperçu rapide.

**Configuration de Flipper :**

```bash
npx expo install react-native-flipper
```

Installez l'application Flipper et exécutez-la avec Metro connecté.

---

## Profilage et optimisation des requêtes réseau

**Définition :**
Suivez et réduisez le nombre et la taille des appels réseau à l'aide de Flipper ou d'intercepteurs Axios personnalisés.

**Exemple (intercepteur Axios pour la journalisation) :**

```ts
import axios from 'axios';

const api = axios.create();

api.interceptors.request.use(req => {
  console.log(`[REQUEST] ${req.method?.toUpperCase()} ${req.url}`);
  return req;
});

api.interceptors.response.use(res => {
  console.log(`[RESPONSE] ${res.status} - ${res.config.url}`);
  return res;
});
```

Regroupez les appels API, utilisez la mise en cache (par exemple, React Query) et évitez les récupérations redondantes.

---

## Conclusion

**Points clés à retenir :**
1. Utilisez la mémöisation et les composants purs pour éviter les re-rendus inutiles.
2. Nettoyez les ressources dans les composants pour éviter les fuites de mémoire.
3. Activez Hermes pour de meilleures performances sur Android (et éventuellement iOS).
4. Utilisez Flipper et React DevTools pour inspecter et déboguer efficacement.
5. Surveillez et optimisez l'utilisation de l'API pour réduire la latence et la surcharge.

**Exercice pratique :**
- Build a screen that lists items from a remote API using `FlatList`.
- Use `memo` for list items to avoid unnecessary re-renders.
- Add Axios interceptors to log each network request.
- Test with Flipper to observe performance and network activity.
