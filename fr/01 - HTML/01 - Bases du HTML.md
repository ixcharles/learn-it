
# **Bases du HTML**

## Introduction
Le HTML (HyperText Markup Language) est le fondement du développement web, définissant la structure et le contenu des pages web. Ce cours couvre les concepts essentiels du HTML, des balises de base à la structuration sémantique.

## Table des matières
- [Introduction au HTML et son rôle dans le développement web](#introduction-au-html-et-son-rôle-dans-le-développement-web)
- [Configuration d'un environnement de développement](#configuration-dun-environnement-de-développement)
- [Comprendre la structure d'un document HTML](#comprendre-la-structure-dun-document-html)
- [Balises HTML essentielles et leur utilisation](#balises-html-essentielles-et-leur-utilisation)
- [Formatage de texte et HTML sémantique](#formatage-de-texte-et-html-sémantique)
- [Conclusion et exercice pratique](#conclusion-et-exercice-pratique)

---

## **Introduction au HTML et son rôle dans le développement web**
### Définition
Le HTML est le langage de balisage standard utilisé pour structurer le contenu web. Il définit des éléments tels que le texte, les images et les liens pour que les navigateurs les affichent.

### Exemple
```html
<!DOCTYPE html>
<html>
<head>
    <title>Ma première page web</title>
</head>
<body>
    <h1>Bienvenue au HTML</h1>
    <p>Ceci est une simple page web.</p>
</body>
</html>
```
### Explication
Chaque page web commence par le HTML. Il fonctionne avec le CSS pour le style et JavaScript pour l'interactivité.

---

## **Configuration d'un environnement de développement**
### Définition
Pour écrire du HTML, vous avez besoin d'un éditeur de texte et d'un navigateur web. Les éditeurs populaires incluent VS Code, Sublime Text et Notepad++.

### Exemple
1. Installez [VS Code](https://code.visualstudio.com/).
2. Créez un fichier `index.html`.
3. Ouvrez-le dans un navigateur.

### Explication
Un bon éditeur fournit la coloration syntaxique, l'auto-complétion et des extensions pour un meilleur flux de travail.

---

## **Comprendre la structure d'un document HTML**
### Définition
Un document HTML est constitué d'éléments qui définissent sa structure, y compris les balises `DOCTYPE`, `html`, `head` et `body`.

### Exemple
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Structure de la page</title>
</head>
<body>
    <h1>Exemple de structure de document</h1>
</body>
</html>
```
### Explication
L'`head` contient les métadonnées, tandis que le `body` contient le contenu visible.

---

## **Balises HTML essentielles et leur utilisation**
### Définition
Les éléments HTML définissent des types de contenu tels que les titres, les paragraphes, les liens, les images et les listes.

### Exemple
```html
<h1>Titre principal</h1>
<p>Ceci est un paragraphe.</p>
<a href="https://example.com">Visiter l'exemple</a>
<img src="image.jpg" alt="Image échantillon">
<ul>
    <li>Élément 1</li>
    <li>Élément 2</li>
</ul>
```
### Explication
Utilisez les balises appropriées pour organiser le contenu efficacement.

---

## **Formatage de texte et HTML sémantique**
### Définition
Le HTML sémantique améliore la lisibilité et l'accessibilité en utilisant des balises significatives comme `<article>`, `<section>` et `<aside>`.

### Exemple
```html
<article>
    <h2>Sémantique HTML</h2>
    <p>L'utilisation d'éléments sémantiques améliore le SEO et l'accessibilité.</p>
</article>
<section>
    <h2>Section d'exemple</h2>
    <p>Le contenu à l'intérieur des sections est structuré logiquement.</p>
</section>
```
### Explication
Les éléments sémantiques décrivent la signification du contenu, aidant les moteurs de recherche et les technologies d'assistance à interpréter les pages.

---

## **Conclusion et exercice pratique**

### **Points clés à retenir**
1. Le HTML est la base du développement web.
2. Un environnement de développement approprié améliore l'efficacité.
3. Les documents HTML suivent un format structuré.
4. Les balises essentielles définissent la mise en page et les éléments de contenu.
5. Le HTML sémantique améliore l'accessibilité et le SEO.

### **Exercice pratique**
Créez une simple page web en utilisant les exigences suivantes :
- Un `title` et un `meta charset="UTF-8"` dans le `<head>`.
- Un titre (`<h1>`) et un paragraphe (`<p>`).
- Un lien (`<a>`), une image (`<img>`) et une liste (`<ul>`).
- Utilisez des éléments sémantiques comme `<section>` et `<article>`.

Enregistrez le fichier sous le nom `index.html` et ouvrez-le dans un navigateur.
