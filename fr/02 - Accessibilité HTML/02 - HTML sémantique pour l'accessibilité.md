
# HTML sémantique pour l'accessibilité

L'HTML sémantique est crucial pour rendre le contenu web accessible à tous les utilisateurs, y compris ceux qui s'appuient sur des technologies d'assistance comme les lecteurs d'écran. Ce cours couvrira les éléments clés de l'HTML sémantique et la manière dont ils améliorent l'accessibilité web.

## Table des matières
1. [Le rôle de l'HTML sémantique dans l'accessibilité](#the-role-of-semantic-html-in-accessibility)
2. [Utilisation appropriée des éléments HTML pour l'accessibilité](#proper-use-of-html-elements-for-accessibility)
3. [Formulaires accessibles : Labels, Fieldsets et Legends](#accessible-forms-labels-fieldsets-and-legends)
4. [Accessibilité des tableaux et de la présentation des données](#tables-and-data-presentation-accessibility)
5. [Titres et structure du contenu pour les lecteurs d'écran](#headings-and-content-structure-for-screen-readers)
6. [Liens et navigation accessibles](#accessible-links-and-navigation)

---

## Le rôle de l'HTML sémantique dans l'accessibilité

**Définition** : L'HTML sémantique utilise des balises HTML qui décrivent clairement la structure et la signification du contenu, le rendant plus accessible aux utilisateurs en situation de handicap.

**Example** : Using `<header>`, `<footer>`, `<article>`, and `<section>` tags instead of generic `<div>` or `<span>`.

**Explication** : L'HTML sémantique permet aux technologies d'assistance de mieux comprendre et naviguer dans le contenu web.

---

## Utilisation appropriée des éléments HTML pour l'accessibilité

**Définition** : L'utilisation correcte des éléments HTML tels que les titres, les listes et les paragraphes garantit que le contenu web est accessible et structuré de manière logique.

**Example** : Using `<ul>` for unordered lists and `<ol>` for ordered lists rather than styling with `<div>` elements.

**Explication** : Les éléments HTML appropriés aident les lecteurs d'écran et autres technologies d'assistance à interpréter le contenu de manière significative.

---

## Formulaires accessibles : Labels, Fieldsets et Legends

**Définition** : L'utilisation appropriée des éléments `<label>`, `<fieldset>` et `<legend>` garantit que les formulaires sont accessibles aux lecteurs d'écran et autres dispositifs d'assistance.

**Example** : `<label for="email">Email Address</label><input type="email" id="email" />`

**Explication** : Les labels associent des descriptions textuelles aux contrôles de formulaire, et les fieldsets et legends regroupent et décrivent les éléments de formulaire connexes.

---

## Accessibilité des tableaux et de la présentation des données

**Définition** : Les tableaux doivent être utilisés pour présenter des données tabulaires, avec des en-têtes et des associations appropriées, ce qui facilite la transmission des informations par les lecteurs d'écran.

**Example** : `<table><thead><tr><th>Product</th><th>Price</th></tr></thead><tbody><tr><td>Item 1</td><td>$10</td></tr></tbody></table>`

**Explication** : L'utilisation de `<th>` pour les en-têtes et d'une `<caption>` appropriée pour le contexte rend les tableaux compréhensibles pour les utilisateurs en situation de handicap.

---

## Titres et structure du contenu pour les lecteurs d'écran

**Définition** : L'utilisation appropriée des titres (de `<h1>` à `<h6>`) et une hiérarchie de contenu claire aident les lecteurs d'écran à naviguer et à interpréter la structure d'une page.

**Example** : `<h1>Main Heading</h1><h2>Subheading</h2><p>Paragraph content here.</p>`

**Explication** : Les titres fournissent un contexte et permettent aux utilisateurs de naviguer dans la page en passant aux sections pertinentes.

---

## Liens et navigation accessibles

**Définition** : Les liens et la navigation doivent être clairement définis, structurés de manière logique et facilement accessibles via le clavier et les lecteurs d'écran.

**Example** : `<a href="#about" title="Learn more about us">About Us</a>`

**Explication** : L'utilisation d'un texte de lien descriptif et la fourniture d'une navigation claire améliorent la convivialité pour tous les utilisateurs, en particulier ceux en situation de handicap.

---

## Conclusion

### Points clés à retenir :
1. L'HTML sémantique améliore l'accessibilité en fournissant une structure et une signification claires au contenu.
2. L'utilisation correcte des éléments de formulaire (labels, fieldsets et legends) améliore l'accessibilité des formulaires.
3. Les tableaux doivent être structurés correctement avec `<th>`, `<caption>` et des en-têtes appropriés pour une présentation claire des données.
4. Les titres et une hiérarchie de contenu appropriée aident les lecteurs d'écran et les utilisateurs à naviguer facilement dans la page.
5. Des liens et une navigation accessibles garantissent que les utilisateurs peuvent se déplacer efficacement dans le site, quelles que soient leurs capacités.

### Exercice pratique :
Take a form on a website and improve its accessibility by adding `<label>`, `<fieldset>`, and `<legend>` elements. Test the updated form with a screen reader or an accessibility tool to evaluate its effectiveness.
