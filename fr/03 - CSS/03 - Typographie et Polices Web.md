
# Typographie et Polices Web

La typographie joue un rôle crucial dans la conception web, ayant un impact sur la lisibilité et l'expérience utilisateur. Ce cours couvre la manière d'utiliser efficacement les polices web et les techniques de typographie en CSS pour une conception optimale.

## Table des Matières
- [Comprendre la Typographie dans la Conception Web](#comprendre-la-typographie-dans-la-conception-web)
- [Familles de Polices et Pile de Polices](#familles-de-polices-et-pile-de-polices)
- [Définir les Tailles de Police : Relatif vs Absolu](#definir-les-tailles-de-police-relatif-vs-absolu)
- [Hauteur de Ligne, Espacement des Lettres et Espacement des Mots](#hauteur-de-ligne-espacement-des-lettres-et-espacement-des-mots)
- [Chargement et Optimisation des Polices Web](#chargement-et-optimisation-des-polices-web)
- [Intégration de Google Fonts et de Polices Personnalisées](#integration-de-google-fonts-et-de-polices-personnalisees)
- [Alignement, Transformation et Décoration du Texte](#alignement-transformation-et-decoration-du-texte)
- [Typographie Réactive avec les Unités CSS](#typographie-reactive-avec-les-unites-css)
- [Techniques de Typographie Avancées : Ligatures, Crénage et Polices Variables](#techniques-de-typographie-avancees-ligatures-crenage-et-polices-variables)

---

## Comprendre la Typographie dans la Conception Web

**Définition :**
La typographie est l'art d'agencer le texte d'une manière visuellement attrayante et lisible sur le web.

**Exemple :**
```css
body {
  font-family: 'Arial', sans-serif;
}
```
**Explication :**
Choisir la bonne `font-family` est essentiel pour créer un design cohérent et lisible, affectant à la fois l'esthétique et l'expérience utilisateur.

---

## Familles de Polices et Pile de Polices

**Définition :**
Une pile de polices définit une liste de choix de polices par ordre de préférence, permettant au navigateur de se rabattre sur des polices alternatives si la police principale n'est pas disponible.

**Exemple :**
```css
p {
  font-family: 'Roboto', 'Helvetica', sans-serif;
}
```
**Explication :**
Cet exemple définit 'Roboto' comme police principale, avec 'Helvetica' et 'sans-serif' comme solutions de repli au cas où la police principale ne serait pas disponible.

---

## Définir les Tailles de Police : Relatif vs Absolu

**Définition :**
Les tailles de police peuvent être définies à l'aide d'unités relatives (`em`, `rem`, `%`) ou d'unités absolues (`px`, `pt`).

**Exemple :**
```css
h1 {
  font-size: 2rem;
}
```
**Explication :**
`rem` (root em) est relatif à la taille de la police de l'élément racine, assurant une évolutivité sur différentes tailles d'écran et résolutions.

---

## Hauteur de Ligne, Espacement des Lettres et Espacement des Mots

**Définition :**
Ces propriétés contrôlent respectivement l'espace vertical entre les lignes de texte, l'espacement entre les lettres et l'espace entre les mots.

**Exemple :**
```css
p {
  line-height: 1.6;
  letter-spacing: 0.05em;
  word-spacing: 0.1em;
}
```
**Explication :**
Ces propriétés améliorent la lisibilité en améliorant le flux du texte et en ajustant l'espacement pour une meilleure apparence visuelle.

---

## Chargement et Optimisation des Polices Web

**Définition :**
Charger et optimiser efficacement les polices web assure un rendu de page plus rapide et une meilleure expérience utilisateur.

**Exemple :**
```css
@font-face {
  font-family: 'MyCustomFont';
  src: url('mycustomfont.woff2') format('woff2');
}
```
**Explication :**
L'utilisation de `@font-face` permet de charger des polices personnalisées, tandis que les formats de police comme `woff2` sont optimisés pour une utilisation web afin de minimiser le temps de chargement.

---

## Intégration de Google Fonts et de Polices Personnalisées

**Définition :**
Google Fonts fournit une bibliothèque de polices web gratuites, et les polices personnalisées peuvent être intégrées en créant un lien vers elles ou en téléchargeant les fichiers de police.

**Exemple :**
```html
<link href="https://fonts.googleapis.com/css2?family=Open+Sans&display=swap" rel="stylesheet">
```
**Explication :**
La balise `<link>` dans le HTML importe la police souhaitée, permettant de l'utiliser sur tout le site web.

---

## Alignement, Transformation et Décoration du Texte

**Définition :**
Ces propriétés contrôlent l'alignement, la transformation (comme les majuscules/minuscules) et la décoration (soulignement, barré) du texte.

**Exemple :**
```css
h2 {
  text-align: center;
  text-transform: uppercase;
  text-decoration: underline;
}
```
**Explication :**
`text-align` centre le texte, `text-transform` met le texte en majuscules et `text-decoration` souligne le texte.

---

## Typographie Réactive avec les Unités CSS

**Définition :**
La typographie réactive utilise des unités CSS comme `vw`, `vh` et `em` pour ajuster dynamiquement la taille du texte en fonction de la taille de l'écran.

**Exemple :**
```css
h1 {
  font-size: 5vw;
}
```
**Explication :**
`vw` (viewport width) permet à la taille de la police de s'adapter à la largeur de la fenêtre d'affichage, rendant la typographie plus réactive sur différents appareils.

---

## Techniques de Typographie Avancées : Ligatures, Crénage et Polices Variables

**Définition :**
Les ligatures, le crénage et les polices variables améliorent les détails typographiques pour une meilleure lisibilité et qualité de conception.

**Exemple :**
```css
h1 {
  font-kerning: normal;
  font-feature-settings: "liga" 1;
}
```
**Explication :**
`font-kerning` ajuste l'espace entre les caractères, et `font-feature-settings` active ou désactive les ligatures (caractères joints) pour une expérience de lecture plus fluide.

---

## Conclusion

### Points Clés à Retenir :
1. Une `font-family` et des piles de polices appropriées garantissent que le texte s'affiche correctement sur différents appareils et navigateurs.
2. Les tailles de police relatives comme `rem` sont plus évolutives et réactives que les tailles fixes comme `px`.
3. La hauteur de ligne, l'espacement des lettres et l'espacement des mots améliorent considérablement la lisibilité du texte.
4. Le chargement et l'optimisation des polices web améliorent les performances et l'expérience utilisateur.
5. Les fonctionnalités de typographie avancées telles que les ligatures, le crénage et les polices variables offrent un contrôle amélioré sur la conception.

### Exercice Pratique :
1. Créez une page web simple avec des titres et des paragraphes.
2. Utilisez Google Fonts pour styliser le texte et expérimentez avec diverses piles de polices.
3. Implémentez une typographie réactive à l'aide d'unités relatives (`em`, `rem`, `vw`).
4. Appliquez des techniques de typographie avancées telles que les ligatures et le crénage pour améliorer l'esthétique du texte.
