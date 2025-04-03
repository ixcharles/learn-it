
# **Éléments HTML et Structuration du Contenu**

## Introduction
Les éléments HTML définissent la structure et le contenu d'une page web. Ce cours couvre les éléments essentiels tels que les titres, les paragraphes, les listes, les liens, le multimédia, les tableaux et les formulaires pour une organisation efficace du contenu.

## Table des matières
- [Titres, Paragraphes et Listes](#titres-paragraphes-et-listes)
- [Liens, Balises d'Ancre et Navigation](#liens-balises-dancre-et-navigation)
- [Images et Éléments Multimédias](#images-et-éléments-multimédias)
- [Tableaux : Structure, Accessibilité et Bonnes Pratiques](#tableaux-structure-accessibilité-et-bonnes-pratiques)
- [Formulaires : Éléments d'Entrée, Étiquettes et Validation de Formulaire](#formulaires-éléments-dentree-étiquettes-et-validation-de-formulaire)
- [Conclusion et Exercice Pratique](#conclusion-et-exercice-pratique)

---

## **Titres, Paragraphes et Listes**
### Définition
Les titres définissent la structure du document, les paragraphes contiennent le texte et les listes organisent le contenu.

### Exemple
```html
<h1>Titre principal</h1>
<p>Ceci est un paragraphe avec un contenu important.</p>
<ul>
    <li>Élément 1</li>
    <li>Élément 2</li>
</ul>
<ol>
    <li>Première étape</li>
    <li>Deuxième étape</li>
</ol>
```
### Explication
Utilisez les titres (`<h1>`-`<h6>`) pour établir une hiérarchie, les paragraphes (`<p>`) pour un texte lisible et les listes (`<ul>`, `<ol>`) pour l'organisation.

---

## **Liens, Balises d'Ancre et Navigation**
### Définition
Les liens connectent les pages, les balises d'ancre permettent la navigation et les éléments `nav` définissent les menus.

### Exemple
```html
<a href="https://example.com">Visiter l'exemple</a>
<nav>
    <ul>
        <li><a href="home.html">Accueil</a></li>
        <li><a href="about.html">À propos</a></li>
    </ul>
</nav>
```
### Explication
Utilisez `<a>` pour les hyperliens et `<nav>` pour les structures de navigation.

---

## **Images et Éléments Multimédias**
### Définition
Le HTML prend en charge les images, l'audio et la vidéo pour un contenu riche.

### Exemple
```html
<img src="image.jpg" alt="Description de l'image">
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
</audio>
<video controls width="400">
    <source src="video.mp4" type="video/mp4">
</video>
```
### Explication
Utilisez `<img>` pour les images, `<audio>` pour le son et `<video>` pour les clips. Incluez toujours `alt` pour l'accessibilité.

---

## **Tableaux : Structure, Accessibilité et Bonnes Pratiques**
### Définition
Les tableaux organisent des données tabulaires à l'aide de lignes et de colonnes.

### Exemple
```html
<table>
    <caption>Liste de produits</caption>
    <tr>
        <th>Produit</th>
        <th>Prix</th>
    </tr>
    <tr>
        <td>Téléphone</td>
        <td>699 $</td>
    </tr>
</table>
```
### Explication
Utilisez `<table>` avec `<tr>` (lignes), `<th>` (en-têtes) et `<td>` (données). Ajoutez `<caption>` pour l'accessibilité.

---

## **Formulaires : Éléments d'Entrée, Étiquettes et Validation de Formulaire**
### Définition
Les formulaires collectent les entrées utilisateur via des champs et des boutons.

### Exemple
```html
<form action="submit.php" method="POST">
    <label for="name">Nom :</label>
    <input type="text" id="name" name="name" required>
    <input type="submit" value="Envoyer">
</form>
```
### Explication
Les formulaires utilisent `<form>` pour envelopper les entrées. Les étiquettes (`<label>`) améliorent l'accessibilité et `required` assure la validation.

---

## **Conclusion et Exercice Pratique**

### **Points clés à retenir**
1. Les titres et les paragraphes structurent le contenu.
2. Les liens et les éléments de navigation permettent la connectivité des pages.
3. Les images et le multimédia améliorent l'expérience utilisateur.
4. Les tableaux organisent efficacement les données tabulaires.
5. Les formulaires collectent les données utilisateur avec validation.

### **Exercice pratique**
Créez une page web contenant :
- Un titre (`<h1>`) et un paragraphe (`<p>`).
- Une barre de navigation (`<nav>`) avec trois liens.
- Une image (`<img>`) avec un attribut `alt`.
- Un tableau (`<table>`) avec trois lignes et deux colonnes.
- Un formulaire (`<form>`) avec un champ de texte et un bouton d'envoi.

Enregistrez sous le nom `content.html` et visualisez dans un navigateur.
