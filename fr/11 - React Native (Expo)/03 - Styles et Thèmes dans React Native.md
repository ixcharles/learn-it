
# Styles et Thèmes dans React Native

Le stylage est un élément essentiel de la création d'interfaces utilisateur belles et réactives dans React Native. Ce module couvre les méthodes de stylage natives, le CSS-in-JS avec styled-components et la gestion des thèmes dans toute votre application.

## Table des matières
- [API StyleSheet de React Native](#api-stylesheet-de-react-native)
- [Styled-Components avec TypeScript](#styled-components-avec-typescript)
- [Thèmes globaux et API Context](#thèmes-globaux-et-api-context)
- [Conception réactive et mises en page Flexbox](#conception-réactive-et-mises-en-page-flexbox)
- [Mode sombre et thèmes dynamiques](#mode-sombre-et-thèmes-dynamiques)

---

## API StyleSheet de React Native

**Définition :**
L'API `StyleSheet` intégrée à React Native vous permet de définir des styles sous forme d'objets JavaScript, similaires à CSS.

**Exemple :**

```tsx
import { StyleSheet, Text, View } from 'react-native';

const styles = StyleSheet.create({
  container: { padding: 16 },
  text: { fontSize: 18, color: 'blue' },
});

const Box = () => (
  <View style={styles.container}>
    <Text style={styles.text}>Hello StyleSheet</Text>
  </View>
);
```

`StyleSheet.create` permet des optimisations de performances et une cohérence.

---

## Styled-Components avec TypeScript

**Définition :**
Styled-components est une librairie CSS-in-JS qui prend en charge le stylage dynamique et le typage TypeScript pour les props.

**Exemple :**

```tsx
import styled from 'styled-components/native';

type Props = { primary?: boolean };

const Button = styled.TouchableOpacity<Props>`
  background-color: ${({ primary }) => (primary ? 'blue' : 'gray')};
  padding: 10px;
`;

const Label = styled.Text`
  color: white;
`;

const StyledExample = () => (
  <Button primary>
    <Label>Click Me</Label>
  </Button>
);
```

Il permet de colocaliser les styles avec les composants pour une meilleure modularité.

---

## Thèmes globaux et API Context

**Définition :**
En utilisant React Context, vous pouvez créer et partager un objet de thème global dans toute votre application.

**Exemple :**

```tsx
// theme.ts
export const theme = {
  colors: {
    background: '#fff',
    text: '#333',
  },
};
```

```tsx
// ThemeContext.tsx
import { createContext, useContext } from 'react';
export const ThemeContext = createContext(theme);
export const useTheme = () => useContext(ThemeContext);
```

Encapsulez votre application dans un `ThemeProvider` et accédez aux valeurs via `useTheme()`.

---

## Conception réactive et mises en page Flexbox

**Définition :**
React Native utilise Flexbox par défaut pour la mise en page, ce qui facilite la création de conceptions réactives.

**Exemple :**

```tsx
import { View } from 'react-native';

const ResponsiveLayout = () => (
  <View style={{ flexDirection: 'row', justifyContent: 'space-between' }}>
    <View style={{ flex: 1, backgroundColor: 'red', height: 100 }} />
    <View style={{ flex: 2, backgroundColor: 'blue', height: 100 }} />
  </View>
);
```

Utilisez `flex`, `flexDirection`, `justifyContent` et `alignItems` pour contrôler la mise en page.

---

## Mode sombre et thèmes dynamiques

**Définition :**
React Native peut détecter les schémas de couleurs du système, vous permettant de basculer dynamiquement entre les thèmes clair et sombre.

**Exemple :**

```tsx
import { useColorScheme } from 'react-native';

const App = () => {
  const colorScheme = useColorScheme();
  const isDark = colorScheme === 'dark';

  return (
    <View style={{ backgroundColor: isDark ? '#000' : '#fff', flex: 1 }}>
      <Text style={{ color: isDark ? '#fff' : '#000' }}>Dark Mode Example</Text>
    </View>
  );
};
```

Combinez avec styled-components ou un fournisseur de thème personnalisé pour un contrôle total.

---

## Conclusion

**Points clés à retenir :**
1. L'API `StyleSheet` est rapide et native à React Native.
2. Styled-components permet un stylage dynamique etScoped utilisant TypeScript.
3. Les thèmes peuvent être gérés globalement à l'aide de Context pour la cohérence.
4. Flexbox alimente des mises en page d'interface utilisateur réactives et adaptables dans React Native.
5. Le thème au niveau du système permet une prise en charge transparente du mode sombre.

**Exercice pratique :**
- Create a reusable `ThemedButton` component.
- Use styled-components and access theme values from a context.
- Implement a toggle switch that switches between light and dark themes.
