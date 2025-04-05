
# Gestion de l'état et manipulation des données

Gérer l'état de l'application et récupérer les données efficacement sont essentiels pour construire des applications React Native robustes et évolutives. Ce module couvre les principaux outils et modèles de gestion de l'état, tous utilisant TypeScript pour la sécurité des types.

## Table des matières
- [API Context avec TypeScript](#api-context-avec-typescript)
- [Redux Toolkit avec TypeScript](#redux-toolkit-avec-typescript)
- [React Query pour la récupération de données](#react-query-pour-la-récupération-de-données)
- [Zustand et Recoil pour une gestion d'état plus simple](#zustand-et-recoil-pour-une-gestion-détat-plus-simple)
- [Meilleures pratiques pour la gestion de l'état global et local](#meilleures-pratiques-pour-la-gestion-de-létat-global-et-local)

---

## API Context avec TypeScript

**Définition :**
L'API Context fournit un moyen de partager des valeurs telles que les thèmes, l'authentification ou les paramètres à travers l'arbre des composants.

**Exemple :**

```tsx
// AuthContext.tsx
import { createContext, useContext, useState } from 'react';

type AuthContextType = {
  user: string | null;
  login: (user: string) => void;
};

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export const AuthProvider = ({ children }: { children: React.ReactNode }) => {
  const [user, setUser] = useState<string | null>(null);
  const login = (name: string) => setUser(name);
  return <AuthContext.Provider value={{ user, login }}>{children}</AuthContext.Provider>;
};

export const useAuth = () => {
  const context = useContext(AuthContext);
  if (!context) throw new Error("useAuth must be used within AuthProvider");
  return context;
};
```

---

## Redux Toolkit avec TypeScript

**Définition :**
Redux Toolkit simplifie Redux avec moins de boilerplate et une forte prise en charge de TypeScript dès le départ.

**Exemple :**

```ts
// store.ts
import { configureStore, createSlice, PayloadAction } from '@reduxjs/toolkit';

type CounterState = { value: number };
const initialState: CounterState = { value: 0 };

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment: state => { state.value += 1; },
    set: (state, action: PayloadAction<number>) => { state.value = action.payload; }
  }
});

export const { increment, set } = counterSlice.actions;
export const store = configureStore({ reducer: { counter: counterSlice.reducer } });
export type RootState = ReturnType<typeof store.getState>;
```

Utilisez `useSelector` et `useDispatch` avec les types appropriés dans les composants.

---

## React Query pour la récupération de données

**Définition :**
React Query (TanStack Query) gère la récupération, la mise en cache et la synchronisation des données distantes de manière efficace.

**Exemple :**

```tsx
import { useQuery } from '@tanstack/react-query';
import axios from 'axios';

const fetchUser = async () => (await axios.get('/api/user')).data;

const Profile = () => {
  const { data, isLoading } = useQuery(['user'], fetchUser);
  if (isLoading) return <Text>Loading...</Text>;
  return <Text>{data.name}</Text>;
};
```

Typez vos réponses d'API pour une sécurité totale dans les composants consommateurs.

---

## Zustand et Recoil pour une gestion d'état plus simple

**Définition :**
Zustand et Recoil offrent des alternatives minimales et flexibles à Redux pour la gestion de l'état.

**Exemple Zustand :**

```ts
import create from 'zustand';

type Store = {
  count: number;
  increment: () => void;
};

export const useStore = create<Store>(set => ({
  count: 0,
  increment: () => set(state => ({ count: state.count + 1 })),
}));
```

**Exemple Recoil :**

```ts
import { atom, useRecoilState } from 'recoil';

const countAtom = atom<number>({ key: 'count', default: 0 });

const Counter = () => {
  const [count, setCount] = useRecoilState(countAtom);
  return <Button onPress={() => setCount(count + 1)} title={`Count: ${count}`} />;
};
```

Les deux s'intègrent facilement avec TypeScript et sont parfaits pour les applications de petite à moyenne taille.

---

## Meilleures pratiques pour la gestion de l'état global et local

**Définition :**
Utilisez la bonne stratégie de gestion de l'état selon que l'état est partagé (global) ou isolé (local).

**Recommandations :**

- **État de l'interface utilisateur locale :** useState ou useReducer.
- **État global de l'application :** Context, Redux, Zustand ou Recoil.
- **État du serveur :** React Query ou SWR.
- Gardez l'état colocalisé autant que possible.
- Évitez les rendus de contexte inutiles en divisant les fournisseurs.

---

## Conclusion

**Points clés à retenir :**
1. L'API Context est idéale pour un état global simple comme l'authentification et le thème.
2. Redux Toolkit réduit le boilerplate et fonctionne bien dans les grandes applications.
3. React Query simplifie la gestion des données asynchrones avec la mise en cache et la synchronisation.
4. Zustand et Recoil sont des alternatives légères avec une configuration minimale.
5. Adaptez votre outil de gestion d'état à la complexité et à la finalité des données.

**Exercice pratique :**
- Build a small app with a counter and user login system.
- Use Zustand for the counter and Context API for the user.
- Display the logged-in user's name and allow logging out.
