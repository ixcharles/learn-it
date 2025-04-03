
# Notions de Base en CSS

Le CSS (Cascading Style Sheets) est un langage de feuille de style utilisé pour décrire la présentation d'un document écrit en HTML ou XML. Ce cours couvrira les concepts et propriétés essentiels que vous devez connaître pour commencer à styliser des sites web efficacement.

## Table des Matières
- [Introduction au CSS](#introduction-au-css)
- [Syntaxe CSS et Sélecteurs](#syntaxe-css-et-selecteurs)
- [Stylisation de Base : Couleurs, Polices et Texte](#stylisation-de-base-couleurs-polices-et-texte)
- [Le Modèle de Boîte : Contenu, Rembourrage, Bordure, Marge](#le-modele-de-boite-contenu-rembourrage-bordure-marge)
- [Positionnement : Statique, Relatif, Absolu, Fixe, Collant](#positionnement-statique-relatif-absolu-fixe-collant)
- [Propriété d'Affichage CSS : Block, Inline, Inline-Block, Flex, Grid](#propriete-daffichage-css-block-inline-inline-block-flex-grid)
- [Unités CSS : px, em, rem, %, vh, vw, fr, et autres](#unites-css-px-em-rem-vh-vw-fr-et-autres)
- [Spécificité et Héritage CSS](#specificite-et-heritage-css)
- [Bases de la Conception Réactive](#bases-de-la-conception-reactive)

---

## Introduction au CSS

Le CSS est utilisé pour contrôler la mise en page, le design et la présentation visuelle d'un site web. Il sépare le contenu (HTML) de la présentation, permettant plus de flexibilité et de contrôle sur le design.

---

## Syntaxe CSS et Sélecteurs

**Définition :**
La syntaxe CSS consiste en un sélecteur et un bloc de déclarations. Le sélecteur cible un élément HTML, tandis que le bloc de déclarations contient des propriétés de style et des valeurs.

**Exemple :**
```css
p {
  color: blue;
  font-size: 16px;
}
```
**Explication :**
Le sélecteur `p` cible tous les éléments `<p>`, appliquant les styles entre les accolades.

---

## Stylisation de Base : Couleurs, Polices et Texte

**Définition :**
Le CSS vous permet de contrôler les couleurs, les polices et les propriétés de texte d'un élément.

**Exemple :**
```css
h1 {
  color: #333;
  font-family: Arial, sans-serif;
  text-align: center;
}
```
**Explication :**
La propriété `color` change la couleur du texte, `font-family` spécifie la police, et `text-align` centre le texte.

---

## Le Modèle de Boîte : Contenu, Rembourrage, Bordure, Marge

**Définition :**
Le modèle de boîte CSS définit la structure de la boîte d'un élément, constituée du contenu, du rembourrage (padding), de la bordure (border) et de la marge (margin).

**Exemple :**
```css
div {
  width: 200px;
  padding: 10px;
  border: 1px solid black;
  margin: 20px;
}
```
**Explication :**
Le modèle de boîte ajoute un rembourrage à l'intérieur de l'élément, une bordure autour de celui-ci et une marge à l'extérieur, affectant la mise en page.

---

## Positionnement : Statique, Relatif, Absolu, Fixe, Collant

**Définition :**
Le positionnement CSS détermine comment un élément est positionné dans le document.

**Exemple :**
```css
div {
  position: absolute;
  top: 50px;
  left: 100px;
}
```
**Explication :**
`absolute` retire l'élément du flux normal et le positionne par rapport à l'ancêtre positionné le plus proche.

---

## Propriété d'Affichage CSS : Block, Inline, Inline-Block, Flex, Grid

**Définition :**
La propriété `display` contrôle la façon dont un élément est affiché sur la page.

**Exemple :**
```css
div {
  display: flex;
}
```
**Explication :**
L'utilisation de `flex` active une mise en page flexible pour les éléments enfants à l'intérieur du conteneur.

---

## Unités CSS : px, em, rem, %, vh, vw, fr, et autres

**Définition :**
Les unités CSS définissent la mesure des propriétés telles que la taille, l'espacement et le positionnement.

**Exemple :**
```css
p {
  font-size: 1.5em;
  width: 50%;
}
```
**Explication :**
`em` est relatif à la taille de la police de l'élément parent, tandis que `%` est relatif à la largeur de l'élément parent.

---

## Spécificité et Héritage CSS

**Définition :**
La spécificité détermine quels styles s'appliquent lorsque plusieurs styles ciblent le même élément. L'héritage permet aux propriétés d'être transmises aux éléments enfants.

**Exemple :**
```css
div p {
  color: red;
}
```
**Explication :**
Cette règle a une spécificité plus élevée que simplement `p` car elle est plus spécifique, ciblant les `p` à l'intérieur d'un `div`.

---

## Bases de la Conception Réactive

**Définition :**
La conception réactive garantit qu'un site web s'affiche correctement sur des appareils de différentes tailles en utilisant des mises en page flexibles et des requêtes média.

**Exemple :**
```css
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
**Explication :**
Cette requête média change la couleur de fond lorsque la largeur de la fenêtre d'affichage est inférieure ou égale à 600px.

---

## Conclusion

### Points Clés à Retenir :
1. Le CSS sépare le contenu de la présentation, offrant un contrôle sur la mise en page et le design.
2. Le modèle de boîte est essentiel pour comprendre les dimensions et l'espacement des éléments.
3. Les propriétés de positionnement et d'affichage sont cruciales pour contrôler le comportement de la mise en page.
4. Les unités CSS offrent une flexibilité dans la mesure, permettant une conception réactive.
5. La spécificité et l'héritage déterminent comment et quels styles sont appliqués aux éléments.

### Exercice Pratique :
1. Créez une page web simple avec un en-tête, deux colonnes et un pied de page.
2. Utilisez le modèle de boîte pour styliser la page, en appliquant du rembourrage, des bordures et des marges.
3. Rendez la mise en page réactive en utilisant des requêtes média pour l'adapter à différentes tailles d'écran.
