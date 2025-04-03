
# **HTML5 et Structuration Avancée des Documents**

## Introduction
HTML5 a introduit de nouveaux éléments sémantiques, la prise en charge multimédia et des API pour une structuration avancée des documents. Ce cours couvre le HTML sémantique, le multimédia, l'API Canvas et l'intégration de contenu externe.

## Table des matières
- [Éléments Sémantiques HTML5 et Leur Importance](#éléments-sémantiques-html5-et-leur-importance)
- [Articles, Sections et Flux du Document](#articles-sections-et-flux-du-document)
- [Multimédia HTML5 : Éléments Audio et Vidéo](#multimédia-html5-éléments-audio-et-vidéo)
- [API Canvas pour les Graphismes et les Animations](#api-canvas-pour-les-graphismes-et-les-animations)
- [Intégration de Contenu Externe (iFrames, SVG, Object)](#intégration-de-contenu-externe-iframes-svg-object)
- [Conclusion et Exercice Pratique](#conclusion-et-exercice-pratique)

---

## **Éléments Sémantiques HTML5 et Leur Importance**
### Définition
Les éléments sémantiques décrivent la signification du contenu, améliorant le SEO et l'accessibilité.

### Exemple
```html
<header>
    <h1>Titre du site web</h1>
</header>
<nav>
    <ul>
        <li><a href="#">Accueil</a></li>
        <li><a href="#">À propos</a></li>
    </ul>
</nav>
<main>
    <article>
        <h2>Titre de l'article</h2>
        <p>Contenu de l'article...</p>
    </article>
</main>
<footer>
    <p>&copy; 2025 Mon site web</p>
</footer>
```
### Explication
Les éléments tels que `<header>`, `<nav>`, `<article>` et `<footer>` améliorent la clarté et l'accessibilité du document.

---

## **Articles, Sections et Flux du Document**
### Définition
HTML5 introduit `<article>` et `<section>` pour une meilleure organisation du contenu.

### Exemple
```html
<section>
    <h2>Dernières nouvelles</h2>
    <article>
        <h3>Dernière heure</h3>
        <p>Détails de la nouvelle...</p>
    </article>
</section>
```
### Explication
Utilisez `<section>` pour le regroupement de contenu et `<article>` pour le contenu autonome.

---

## **Multimédia HTML5 : Éléments Audio et Vidéo**
### Définition
HTML5 prend en charge la lecture audio et vidéo native sans plugins externes.

### Exemple
```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
</audio>

<video controls width="400">
    <source src="video.mp4" type="video/mp4">
</video>
```
### Explication
Les éléments `<audio>` et `<video>` prennent en charge plusieurs formats et commandes.

---

## **API Canvas pour les Graphismes et les Animations**
### Définition
L'élément `<canvas>` permet le rendu dynamique de graphiques via JavaScript.

### Exemple
```html
<canvas id="myCanvas" width="200" height="100"></canvas>
<script>
    const canvas = document.getElementById("myCanvas");
    const ctx = canvas.getContext("2d");
    ctx.fillStyle = "blue";
    ctx.fillRect(20, 20, 150, 50);
</script>
```
### Explication
Utilisez l'API `<canvas>` pour des dessins et des animations personnalisés.

---

## **Intégration de Contenu Externe (iFrames, SVG, Object)**
### Définition
HTML5 permet d'intégrer d'autres pages web, des graphiques vectoriels et du contenu externe.

### Exemple
```html
<iframe src="https://example.com" width="600" height="400"></iframe>

<svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
</svg>

<object data="file.pdf" type="application/pdf" width="600" height="400"></object>
```
### Explication
Utilisez `<iframe>` pour intégrer des pages, `<svg>` pour les graphiques vectoriels et `<object>` pour les fichiers externes.

---

## **Conclusion et Exercice Pratique**

### **Points clés à retenir**
1. Les éléments sémantiques améliorent le SEO et l'accessibilité.
2. `<section>` et `<article>` organisent le contenu de manière significative.
3. HTML5 prend en charge la lecture audio et vidéo native.
4. L'API `<canvas>` permet des graphismes dynamiques.
5. `<iframe>`, `<svg>` et `<object>` intègrent du contenu externe.

### **Exercice pratique**
Créez une page web qui inclut :
- **Une structure sémantique** avec `<header>`, `<nav>`, `<main>` et `<footer>`.
- **Une section d'article** avec des titres et des paragraphes.
- **Une vidéo intégrée** en utilisant l'élément `<video>`.
- **Un dessin simple** en utilisant l'API `<canvas>`.
- **Un graphique SVG intégré** pour le rendu vectoriel.

Enregistrez sous le nom `advanced.html` et ouvrez dans un navigateur.
