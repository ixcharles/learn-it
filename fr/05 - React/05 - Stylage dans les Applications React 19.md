
# Stylage dans les Applications React 19

Le stylage est un aspect essentiel des applications React, et React 19 offre divers outils et techniques pour créer des interfaces utilisateur dynamiques, réutilisables et maintenables. Ce cours couvre les méthodes de stylage populaires et les techniques avancées dans React 19.

---

## Table des Matières
- [Modules CSS](#css-modules)
- [Composants Stylisés](#styled-components)
- [Intégration de Tailwind CSS](#tailwind-css-integration)
- [Emotion et CSS-in-JS](#emotion-and-css-in-js)
- [Thèmes Dynamiques et Mode Sombre](#dynamic-theming-and-dark-mode)
- [Conception Réactive dans React](#responsive-design-in-react)
- [Animations avec Framer Motion](#animations-with-framer-motion)
- [Conclusion & Points Clés](#conclusion--key-takeaways)
- [Exercice Pratique](#practical-exercise)

---

## Modules CSS

**Définition :** Les Modules CSS permettent un stylage localisé en générant automatiquement des noms de classes uniques.
**Exemple :**
```jsx
// styles.module.css
.button {
  background-color: blue;
  color: white;
}

// Component.jsx
import styles from './styles.module.css';

const Button = () => <button className={styles.button}>Cliquez-moi</button>;
```

---

## Composants Stylisés

**Définition :** Styled Components est une librairie CSS-in-JS qui vous permet d'écrire du CSS directement dans vos fichiers JavaScript.
**Exemple :**
```jsx
import styled from 'styled-components';

const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px 20px;
`;

const App = () => <Button>Cliquez-moi</Button>;
```

---

## Intégration de Tailwind CSS

**Définition :** Tailwind CSS est un framework CSS utilitaire qui offre des classes prédéfinies pour le stylage.
**Exemple :**
```jsx
const App = () => (
  <div className="bg-blue-500 text-white p-4">
    <h1>Bienvenue dans React</h1>
  </div>
);
```

**Étapes d'Intégration :**
1. Installez Tailwind via npm :
   ```bash
   npm install tailwindcss
   ```
2. Configurez Tailwind :
   ```bash
   npx tailwindcss init
   ```
3. Ajoutez les directives Tailwind dans votre fichier CSS :
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

---

## Emotion et CSS-in-JS

**Définition :** Emotion est une librairie CSS-in-JS populaire qui permet de définir des styles en utilisant JavaScript, fournissant à la fois des styled-components et des noms de classes CSS traditionnels.
**Exemple :**
```jsx
/** @jsxImportSource @emotion/react */
import { css } from '@emotion/react';

const buttonStyle = css`
  background-color: green;
  color: white;
  padding: 10px 20px;
`;

const Button = () => <button css={buttonStyle}>Cliquez-moi</button>;
```

---

## Thèmes Dynamiques et Mode Sombre

**Définition :** Le thème dynamique implique de basculer entre différents thèmes (par exemple, clair et sombre) au moment de l'exécution.
**Exemple :**
```jsx
import { useState } from 'react';
import './App.css';

const App = () => {
  const [isDarkMode, setIsDarkMode] = useState(false);

  return (
    <div className={isDarkMode ? 'dark' : 'light'}>
      <button onClick={() => setIsDarkMode(!isDarkMode)}>
        Activer/Désactiver le Mode Sombre
      </button>
    </div>
  );
};

// CSS
.dark {
  background-color: black;
  color: white;
}

.light {
  background-color: white;
  color: black;
}
```

---

## Conception Réactive dans React

**Définition :** La conception réactive garantit qu'une application ajuste sa mise en page à différentes tailles d'écran, généralement en utilisant des media queries ou des frameworks CSS utilitaires comme Tailwind.
**Exemple :**
```jsx
const App = () => (
  <div className="container mx-auto p-4">
    <div className="md:flex md:justify-between">
      <div className="bg-blue-500 p-2">Élément 1</div>
      <div className="bg-green-500 p-2">Élément 2</div>
    </div>
  </div>
);
```
*Dans cet exemple, la mise en page change en fonction de la taille de l'écran en utilisant les utilitaires réactifs de Tailwind.*

---

## Animations avec Framer Motion

**Définition :** Framer Motion est une librairie puissante pour les animations dans React, permettant des transitions et des interactions fluides.
**Exemple :**
```jsx
import { motion } from 'framer-motion';

const App = () => (
  <motion.div
    initial={{ opacity: 0 }}
    animate={{ opacity: 1 }}
    transition={{ duration: 1 }}
  >
    <h1>Bienvenue dans l'Animation React !</h1>
  </motion.div>
);
```

**Fonctionnalités Clés de Framer Motion :**
- `initial` : État de départ d'une animation.
- `animate` : État final après l'animation.
- `transition` : Définit la progression de l'animation (par exemple, durée, easing).

---

## Conclusion & Points Clés

- Les **Modules CSS** assurent un stylage localisé et évitent les conflits de noms de classes.
- **Styled Components** et **Emotion** offrent une flexibilité avec les solutions CSS-in-JS pour écrire des styles directement dans les composants.
- **Tailwind CSS** simplifie la mise en page et le stylage avec des classes utilitaires, rendant les conceptions réactives et cohérentes.
- Le **thème dynamique** permet aux applications de changer de thème (par exemple, mode clair/sombre) au moment de l'exécution pour une meilleure expérience utilisateur.
- **Framer Motion** est un excellent outil pour créer des animations et des transitions fluides dans les applications React.

---

## Exercice Pratique

Construisez une simple application de `Liste de Tâches` :
1. Stylez les composants en utilisant les **Modules CSS** ou les **Composants Stylisés**.
2. Intégrez **Tailwind CSS** pour rendre l'application réactive pour mobile et bureau.
3. Implémentez un bouton de bascule de thème pour passer du **mode clair** au **mode sombre**.
4. Ajoutez une animation en utilisant **Framer Motion** lors de l'ajout d'une nouvelle tâche à la liste.
