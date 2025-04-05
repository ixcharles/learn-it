
# Collaboration et Revues de Code

Ce cours couvre les techniques fondamentales et les meilleures pratiques pour collaborer sur GitHub, depuis le forking des dépôts et la gestion des requêtes de tirage jusqu'à la réalisation des revues de code et la résolution des conflits.

## Table des Matières

1. [Forking, Requêtes de Tirage et Fusion sur GitHub](#forking-pull-requests-and-merging-on-github)
2. [Relecture de Code et Fourniture de Commentaires](#reviewing-code-and-providing-feedback)
3. [Gestion des Conflits de Fusion dans les Requêtes de Tirage](#managing-merge-conflicts-in-pull-requests)
4. [Gestion des Permissions de Branches et des Branches Protégées](#managing-branch-permissions-and-protected-branches)
5. [Utilisation des Étiquettes, des Assignations et des Jalons pour le Suivi des Issues](#using-labels-assignments-and-milestones-for-issue-tracking)
6. [Rebasage vs. Fusion dans les Requêtes de Tirage](#rebase-vs-merge-in-pull-requests)

---

## Forking, Requêtes de Tirage et Fusion sur GitHub

### Forking
Le forking crée une copie personnelle d'un dépôt, vous permettant d'expérimenter ou d'apporter des modifications sans affecter l'original.

- Pour forker, cliquez sur le bouton **Fork** en haut à droite du dépôt GitHub.

### Requêtes de Tirage (Pull Requests)
Une fois les modifications prêtes, ouvrez une requête de tirage (PR) pour fusionner votre branche dans le dépôt original.

1. **Créer une Requête de Tirage** : Après avoir poussé les modifications vers une branche, cliquez sur "New Pull Request" sur GitHub.
2. **Relecture et Fusion** : Les collaborateurs relisent la PR. Une fois approuvée, elle peut être fusionnée dans le dépôt principal.

**Example:**
```bash
git clone https://github.com/votre-nom-utilisateur/repo.git
git checkout -b branche-fonctionnalite
git push origin branche-fonctionnalite
```
Ensuite, créez une requête de tirage pour fusionner `branche-fonctionnalite` dans `main`.

---

## Relecture de Code et Fourniture de Commentaires

Les revues de code sont une partie essentielle de la collaboration. Voici comment vous pouvez relire et fournir des commentaires :

- **Relecture des Modifications** : Affichez les modifications dans l'onglet PR et vérifiez les fichiers modifiés.
- **Commentaires** : Fournissez des commentaires sur des lignes spécifiques en utilisant les commentaires en ligne.
- **Approbation** : Si les modifications sont satisfaisantes, approuvez la PR ou demandez des modifications si des améliorations sont nécessaires.

**Example:**
- Commentaire : "Pouvez-vous optimiser cette fonction ?"
- Approbation : "Cela semble bien, j'approuve."

---

## Gestion des Conflits de Fusion dans les Requêtes de Tirage

Les conflits de fusion se produisent lorsque les modifications dans deux branches entrent en conflit et que Git ne peut pas les fusionner automatiquement. GitHub fournit des outils pour aider à résoudre les conflits.

1. **Identification des Conflits** : GitHub marquera les fichiers en conflit dans la PR.
2. **Résolution Locale** : Récupérez les modifications sur votre dépôt local, résolvez les conflits et poussez la résolution.

**Example:**
```bash
git fetch origin
git checkout branche-fonctionnalite
git merge main
# Résolvez les conflits manuellement dans les fichiers en conflit
git add <fichier-résolu>
git commit -m "Résoudre les conflits de fusion"
git push origin branche-fonctionnalite
```

---

## Gestion des Permissions de Branches et des Branches Protégées

Les branches protégées sont utilisées pour appliquer des règles sur certaines branches (par exemple, `main`, `develop`) afin de garantir une haute qualité de code et d'empêcher les push directs.

- **Règles de Protection des Branches** : Définissez des règles telles que l'obligation de revues de PR, la réussite des vérifications de statut et la restriction des personnes autorisées à pousser vers la branche.
- **Application des Règles** : Définissez les règles sous les paramètres du dépôt → **Branches** → **Add Rule**.

**Example:**
- Vous pouvez exiger une vérification CI réussie avant la fusion ou imposer que seuls certains utilisateurs puissent pousser directement vers `main`.

---

## Utilisation des Étiquettes, des Assignations et des Jalons pour le Suivi des Issues

GitHub fournit plusieurs outils pour organiser et prioriser le travail à l'aide des **Étiquettes (Labels)**, des **Assignations (Assignments)** et des **Jalons (Milestones)**.

### Étiquettes (Labels)
- Les **étiquettes** catégorisent les issues (par exemple, `bug`, `enhancement`, `help wanted`).

### Assignations (Assignments)
- Assignez des issues aux collaborateurs pour résolution.

### Jalons (Milestones)
- Utilisez les **jalons** pour suivre l'avancement vers un objectif ou une version particulière.

**Example:**
- Étiquetez une issue `bug`, assignez-la à un membre de l'équipe et ajoutez-la à un jalon comme `Version 1.0`.

---

## Rebasage vs. Fusion dans les Requêtes de Tirage

- **Rebasage (Rebase)** : Réécriture de l'historique pour appliquer vos modifications au sommet de la branche cible, conservant un historique linéaire plus propre.
  - **Avantages** : Crée un historique de commits plus propre.
  - **Inconvénients** : Réécrit l'historique des commits, ce qui peut causer des problèmes dans les branches partagées.

- **Fusion (Merge)** : Combine les modifications de deux branches avec un commit de fusion, préservant les deux historiques.

**Quand Utiliser** :
- Utilisez le **Rebasage** pour maintenir un historique de commits propre (idéal pour les branches de fonctionnalités).
- Utilisez la **Fusion** pour préserver l'historique de la branche, en particulier dans les branches partagées ou publiques.

**Example:**
- Rebasage :
```bash
git fetch origin
git rebase origin/main
```
- Fusion :
```bash
git merge branche-fonctionnalite
```

---

## Conclusion

### Points Clés à Retenir :
1. Le **Forking et les Requêtes de Tirage** sont essentiels pour contribuer à des projets open source ou collaboratifs.
2. Les **revues de code** doivent se concentrer sur la fourniture de commentaires constructifs pour améliorer la qualité du code.
3. Les **conflits de fusion** peuvent être résolus localement avant de repousser les modifications vers le dépôt.
4. Les **permissions de branches** aident à appliquer le contrôle qualité en limitant les personnes autorisées à modifier les branches critiques.
5. Le **Rebasage** maintient l'historique linéaire, tandis que la **fusion** préserve la structure des branches.

### Exercice Pratique :
1. Forkez un dépôt, créez une branche, apportez des modifications et soumettez une requête de tirage.
2. Relisez une requête de tirage, laissez des commentaires et approuvez ou demandez des modifications.
3. Résolvez un conflit de fusion dans une requête de tirage, puis rebasez la branche avant de la fusionner.
