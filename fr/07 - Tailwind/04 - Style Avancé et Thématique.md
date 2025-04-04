
# Style Avancé et Thématique

Tailwind CSS offre des outils robustes pour une personnalisation approfondie, vous permettant d'étendre et d'adapter ses utilitaires pour qu'ils correspondent à l'image de marque et au système de conception de votre projet. Ce cours couvre la configuration avancée, les utilitaires personnalisés et la conception basée sur le thème.

---

## Table des Matières

- [Personnalisation Avancée via le Fichier de Configuration](#personnalisation-avancee-via-le-fichier-de-configuration)
  - [Étendre vs Remplacer les Valeurs par Défaut](#etendre-vs-remplacer-les-valeurs-par-defaut)
- [Création de Classes Utilitaires et de Plugins Personnalisés](#creation-de-classes-utilitaires-et-de-plugins-personnalises)
- [Stratégies de Mode Sombre](#strategies-de-mode-sombre)
  - [Stratégie de Classe vs Média](#strategie-de-classe-vs-media)
  - [Thématisation du Mode Sombre](#thematisation-du-mode-sombre)
- [Personnalisation du Thème pour l'Image de Marque](#personnalisation-du-theme-pour-l-image-de-marque)
  - [Couleurs, Polices, Espacement, Ombres](#couleurs-polices-espacement-ombres)
- [Utilisation de @apply pour les Styles de Composants](#utilisation-de-apply-pour-les-styles-de-composants)
- [Conclusion](#conclusion)

---

## Personnalisation Avancée via le Fichier de Configuration

### Étendre vs Remplacer les Valeurs par Défaut

**Définition** : Vous pouvez étendre la configuration par défaut de Tailwind en ajoutant des valeurs personnalisées, ou la remplacer entièrement pour répondre aux besoins de votre conception.

**Exemple** :
```js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: '#1F2937',
      },
    },
  },
}
```

Utilisez `extend` pour ajouter de nouvelles valeurs sans perdre les valeurs par défaut, ou modifiez directement `theme` pour les remplacer.

---

## Création de Classes Utilitaires et de Plugins Personnalisés

**Définition** : Tailwind vous permet de créer vos propres classes utilitaires et plugins pour des composants réutilisables ou des conceptions complexes.

**Exemple** :
```js
const plugin = require('tailwindcss/plugin');

module.exports = {
  plugins: [
    plugin(function({ addUtilities }) {
      addUtilities({
        '.rotate-15': {
          transform: 'rotate(15deg)',
        },
      });
    }),
  ],
}
```

Créez des classes personnalisées comme `.rotate-15` pour des styles spécifiques qui ne font pas partie de l'ensemble par défaut de Tailwind.

---

## Stratégies de Mode Sombre

### Stratégie de Classe vs Média

**Définition** : Tailwind propose deux stratégies pour le mode sombre : l'utilisation d'une classe ou de la media query `prefers-color-scheme`.

**Exemple (Stratégie de Classe)** :
```html
<div class="dark:bg-gray-800 dark:text-white">
  Contenu en mode sombre
</div>
```
```js
module.exports = {
  darkMode: 'class', // Activer le mode sombre basé sur une classe
}
```

**Exemple (Stratégie Média)** :
```js
module.exports = {
  darkMode: 'media', // Utiliser prefers-color-scheme
}
```

La stratégie basée sur une classe offre plus de contrôle, tandis que la stratégie média s'applique automatiquement en fonction des préférences de l'utilisateur.

### Thématisation du Mode Sombre

**Définition** : Tailwind prend en charge le style du mode sombre en appliquant des classes en fonction de la stratégie choisie (classe ou média).

**Exemple** :
```html
<div class="bg-white dark:bg-gray-800 text-black dark:text-white">
  Exemple de mode sombre
</div>
```

Vous pouvez personnaliser les styles du mode sombre dans votre fichier de configuration, ce qui permet différents schémas de couleurs et effets.

---

## Personnalisation du Thème pour l'Image de Marque

### Couleurs, Polices, Espacement, Ombres

**Définition** : Personnalisez le thème par défaut de Tailwind pour l'aligner sur l'image de marque de votre projet (couleurs, polices, espacement, etc.).

**Exemple** :
```js
module.exports = {
  theme: {
    extend: {
      colors: {
        brand: '#FF5722',
      },
      fontFamily: {
        sans: ['Poppins', 'sans-serif'],
      },
      spacing: {
        128: '32rem',
      },
      boxShadow: {
        custom: '0 4px 6px rgba(0, 0, 0, 0.1)',
      },
    },
  },
}
```

Adaptez le système de conception de base pour qu'il corresponde aux couleurs, à la typographie et aux conventions d'espacement de votre marque.

---

## Utilisation de @apply pour les Styles de Composants

**Définition** : La directive `@apply` vous permet de composer des utilitaires Tailwind en styles de composants réutilisables.

**Exemple** :
```css
.btn {
  @apply bg-blue-500 text-white p-2 rounded-md shadow-md;
}
```

Utilisez `@apply` dans vos fichiers CSS pour combiner plusieurs utilitaires pour une conception cohérente et réutilisable.

---

## Conclusion

### Points Clés à Retenir

- Étendre `tailwind.config.js` ajoute des valeurs personnalisées, tandis que remplacer les valeurs par défaut les supprime.
- Les plugins et les utilitaires personnalisés de Tailwind étendent ses fonctionnalités pour les besoins spécifiques du projet.
- Tailwind propose deux stratégies pour le mode sombre : basée sur une classe et basée sur une media query.
- La personnalisation du thème vous permet d'aligner Tailwind sur votre image de marque (couleurs, polices, etc.).
- Utilisez `@apply` pour consolider les classes utilitaires en composants réutilisables et maintenables.

---

### Exercice Pratique

Créez un composant de bouton personnalisé avec :
- Une couleur d'arrière-plan basée sur la couleur primaire de la marque
- Un effet de survol utilisant `@apply` pour des styles de bouton réutilisables
- Prise en charge des modes clair et sombre
