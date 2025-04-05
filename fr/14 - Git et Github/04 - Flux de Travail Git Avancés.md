
# Flux de Travail Git Avancés

Ce cours explore les flux de travail Git avancés qui amélioreront votre capacité à gérer des projets complexes, à collaborer efficacement et à utiliser pleinement le potentiel de Git dans des environnements d'équipe.

## Table des Matières

1. [Modèle et Stratégies Git Flow](#git-flow-model-and-strategies)
2. [Flux de Travail par Branches de Fonctionnalités (Feature Branch Workflow)](#feature-branch-workflow)
3. [GitHub Flow](#github-flow)
4. [Flux de Travail par Forking sur GitHub](#forking-workflow-on-github)
5. [Rebasage et Écrasement des Commits (Rebasing and Squashing Commits)](#rebasing-and-squashing-commits)
6. [Stratégies de Fusion Avancées (Advanced Merging Strategies)](#advanced-merging-strategies)
7. [Utilisation des Sous-modules Git (Using Git Submodules)](#using-git-submodules)

---

## Modèle et Stratégies Git Flow

Le modèle Git Flow est une stratégie de gestion des branches qui définit des rôles spécifiques pour les branches, assurant un développement organisé.

- **Branche Principale (Main Branch)** : Contient toujours le code prêt pour la production.
- **Branche de Développement (Develop Branch)** : Utilisée pour l'intégration des fonctionnalités.
- **Branches de Fonctionnalités (Feature Branches)** : Créées à partir de `develop` pour les nouvelles fonctionnalités.
- **Branches de Publication (Release Branches)** : Prépare les nouvelles versions à partir de `develop`.
- **Branches de Correctifs Urgents (Hotfix Branches)** : Créées à partir de `main` pour les corrections urgentes.

**Example:**
```bash
git checkout -b feature/nom-de-la-fonctionnalite develop
git checkout -b release/1.0 develop
git checkout -b hotfix/correction-urgente main
```

---

## Flux de Travail par Branches de Fonctionnalités (Feature Branch Workflow)

Le Flux de Travail par Branches de Fonctionnalités est un modèle de gestion des branches Git où chaque fonctionnalité ou tâche est développée dans sa propre branche, garantissant que la branche principale reste stable.

- Créer une branche de fonctionnalité : `git checkout -b feature/nom-de-la-fonctionnalite`
- Travailler sur la fonctionnalité et valider les modifications (commits).
- Fusionner dans la branche principale via une requête de tirage (pull request) ou `git merge`.

**Example:**
```bash
git checkout -b feature/formulaire-de-connexion
git add .
git commit -m "Implémenter le formulaire de connexion"
git checkout main
git merge feature/formulaire-de-connexion
```

---

## GitHub Flow

GitHub Flow est une version simplifiée de Git Flow, spécialement conçue pour la livraison continue et la collaboration sur GitHub. Il met l'accent sur les mises à jour rapides et fréquentes et les requêtes de tirage.

- Travailler sur une nouvelle fonctionnalité ou un correctif dans une nouvelle branche.
- Ouvrir une requête de tirage pour fusionner vos modifications dans la branche `main`.
- Examiner, tester et fusionner les modifications dans `main`.

**Example:**
```bash
git checkout -b feature/nouveau-bouton
git push origin feature/nouveau-bouton
```

Ensuite, créez une requête de tirage sur GitHub.

---

## Flux de Travail par Forking sur GitHub

Le Flux de Travail par Forking est généralement utilisé dans les projets open source. Les développeurs forquent le dépôt principal, apportent des modifications et soumettent des requêtes de tirage.

- Forkez le dépôt sur GitHub.
- Clonez votre dépôt forké sur votre machine locale.
- Créez une branche, apportez des modifications et poussez-les.
- Ouvrez une requête de tirage pour fusionner vos modifications dans le dépôt d'origine.

**Example:**
```bash
git clone https://github.com/votre-nom-utilisateur/repo.git
git checkout -b feature/nouvelle-fonctionnalite
git push origin feature/nouvelle-fonctionnalite
```

Ensuite, créez une requête de tirage sur GitHub.

---

## Rebasage et Écrasement des Commits (Rebasing and Squashing Commits)

- **Rebasage (Rebasing)** : Réapplique les commits au sommet d'une autre branche pour maintenir un historique de commits propre.
- **Écrasement (Squashing)** : Combine plusieurs commits en un seul commit pour simplifier l'historique.

**Example:**
- Rebasage :
```bash
git rebase main
```
- Écrasement :
```bash
git rebase -i HEAD~3  # Choisissez 'squash' pour les commits à combiner
```

---

## Stratégies de Fusion Avancées (Advanced Merging Strategies)

- **Fusion Fast-Forward** : Une fusion simple lorsque la branche courante est directement en avance sur la branche cible.
- **Fusion No-Fast-Forward** : Crée toujours un commit de fusion même si un fast-forward est possible, préservant l'historique des fusions.
- **Fusion Récursive** : La stratégie de fusion par défaut de Git, qui gère la plupart des cas en fusionnant les branches de manière récursive.

**Example:**
- Fast-Forward :
```bash
git merge branche-fonctionnalite
```
- No-Fast-Forward :
```bash
git merge --no-ff branche-fonctionnalite
```

---

## Utilisation des Sous-modules Git (Using Git Submodules)

Les sous-modules Git vous permettent d'inclure un dépôt Git à l'intérieur d'un autre en tant que sous-répertoire. Ceci est utile pour gérer les dépendances ou les bibliothèques partagées.

- `git submodule add <url_du_depot>`: Ajoute un sous-module au projet courant.
- `git submodule init`: Initialise les sous-modules.
- `git submodule update`: Met à jour le contenu des sous-modules.

**Example:**
```bash
git submodule add https://github.com/nom-utilisateur/repo.git sous-modules/repo
git submodule init
git submodule update
```

---

## Conclusion

### Points Clés à Retenir :
1. **Git Flow** : Organise le développement avec des branches dédiées pour les fonctionnalités, les publications et les correctifs urgents.
2. **Flux de Travail par Branches de Fonctionnalités** : Assure la stabilité en développant les fonctionnalités dans des branches isolées.
3. **GitHub Flow** : Un modèle de gestion des branches simple pour un déploiement rapide avec des requêtes de tirage.
4. **Flux de Travail par Forking** : Essentiel pour contribuer à des projets open source en travaillant dans un dépôt forké.
5. **Rebasage et Écrasement** : Aide à maintenir un historique de commits propre et concis.
6. **Sous-modules** : Permettent d'inclure des dépôts externes dans un projet, utile pour les bases de code partagées.

### Exercice Pratique :
1. Créez un modèle Git flow pour votre projet avec des branches pour les fonctionnalités, les publications et les correctifs urgents.
2. Utilisez le flux de travail par forking pour contribuer à un projet open source en forkant, clonant et soumettant une requête de tirage.
3. Entraînez-vous à rebaser et à écraser des commits dans une branche de fonctionnalité avant de la fusionner dans `main`.
