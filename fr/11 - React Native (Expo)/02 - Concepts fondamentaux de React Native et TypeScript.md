
# Concepts fondamentaux de React Native et TypeScript

Ce module explore les éléments constitutifs de base de React Native avec TypeScript, couvrant la manière dont les composants, l'état, les props et les interactions utilisateur sont gérés de manière type-safe.

## Table des matières
- [JSX et structure des composants dans React Native](#jsx-et-structure-des-composants-dans-react-native)
- [Composants fonctionnels et Hooks](#composants-fonctionnels-et-hooks)
- [Interfaces et types TypeScript dans les composants](#interfaces-et-types-typescript-dans-les-composants)
- [Gestion des Props et de l'état avec TypeScript](#gestion-des-props-et-de-létat-avec-typescript)
- [Gestion des événements et des entrées utilisateur](#gestion-des-événements-et-des-entrées-utilisateur)

---

## JSX et structure des composants dans React Native

**Définition :**
JSX est une extension de syntaxe qui vous permet d'écrire du code d'interface utilisateur dans un format familier de type HTML à l'intérieur des fichiers JavaScript/TypeScript.

**Exemple :**

```tsx
import { Text, View } from 'react-native';

const MyComponent = () => (
  <View>
    <Text>Hello, React Native!</Text>
  </View>
);
```

React Native utilise JSX pour décrire les hiérarchies d'interface utilisateur à l'aide de composants tels que `<View>`, `<Text>` et `<Image>`.

---

## Composants fonctionnels et Hooks

**Définition :**
Les composants fonctionnels sont des composants sans état qui s'appuient sur des hooks comme `useState`, `useEffect` et `useRef` pour la logique et les effets secondaires.

**Exemple :**

```tsx
import { useState, useEffect } from 'react';
import { Text, Button } from 'react-native';

const Counter = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log(`Count is ${count}`);
  }, [count]);

  return <Button title={`Count: ${count}`} onPress={() => setCount(count + 1)} />;
};
```

Les Hooks vous permettent de gérer l'état et le cycle de vie des composants sans les composants de classe.

---

## Interfaces et types TypeScript dans les composants

**Définition :**
Les interfaces et les types TypeScript fournissent une structure aux props des composants et à la logique interne, réduisant les erreurs et améliorant la prise en charge de l'éditeur.

**Exemple :**

```ts
type User = {
  id: number;
  name: string;
};

interface Props {
  user: User;
}
```

L'utilisation de types explicites garantit que les contrats des composants sont prévisibles et maintenables.

---

## Gestion des Props et de l'état avec TypeScript

**Définition :**
Les props et l'état sont fondamentaux pour contrôler le comportement de l'interface utilisateur et le flux de données dans les composants. TypeScript aide à définir clairement leur forme.

**Exemple :**

```tsx
type Props = {
  name: string;
};

const Greeting = ({ name }: Props) => {
  const [visible, setVisible] = useState(true);

  return visible ? <Text>Hello, {name}!</Text> : null;
};
```

Les props et l'état typés améliorent la réutilisabilité et la fiabilité des composants.

---

## Gestion des événements et des entrées utilisateur

**Définition :**
React Native prend en charge la gestion des gestes et des entrées utilisateur via des composants tels que `TextInput`, `Button` et les événements tactiles.

**Exemple :**

```tsx
import { useState } from 'react';
import { TextInput, Text, View } from 'react-native';

const InputExample = () => {
  const [text, setText] = useState('');

  return (
    <View>
      <TextInput
        placeholder="Type here"
        onChangeText={setText}
        value={text}
      />
      <Text>You typed: {text}</Text>
    </View>
  );
};
```

Utilisez des gestionnaires d'événements comme `onChangeText` et `onPress` avec un typage fort lorsque cela est applicable.

---

## Conclusion

**Points clés à retenir :**
1. JSX rend le code d'interface utilisateur déclaratif et intuitif.
2. Les composants fonctionnels sont la norme React moderne.
3. TypeScript applique des contrats stricts avec les props et l'état.
4. Les Hooks fournissent une logique de composant réactive et composable.
5. La gestion des événements intègre de manière transparente les entrées utilisateur dans les applications mobiles.

**Exercice pratique :**
- Create a component called `ProfileCard` that takes a typed `User` prop with `name`, `bio`, and `age`.
- Use `useState` to toggle showing the user's bio on button press.
