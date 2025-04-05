
# Fondamentaux de GitHub

Ce cours présente les fonctionnalités essentielles de GitHub qui améliorent la collaboration, le contrôle de version et l'automatisation, permettant aux développeurs de travailler plus efficacement dans des environnements d'équipe.

## Table des Matières

1. [Introduction à GitHub](#introduction-to-github)
2. [Création et Gestion des Dépôts sur GitHub](#creating-and-managing-repositories-on-github)
3. [Clonage des Dépôts GitHub](#cloning-github-repositories)
4. [Forking des Dépôts et Requêtes de Tirage (Pull Requests)](#forking-repositories-and-pull-requests)
5. [Tickets (Issues) et Suivi des Tickets sur GitHub](#issues-and-issue-tracking-on-github)
6. [Projets et Jalons (Milestones) GitHub](#github-projects-and-milestones)
7. [Collaboration avec les Équipes GitHub](#collaborating-with-github-teams)
8. [GitHub Actions et Bases de l'Intégration/Déploiement Continus (CI/CD)](#github-actions-and-cicd-basics)

---

## Introduction à GitHub

GitHub est une plateforme d'hébergement et de collaboration pour les dépôts Git. Elle permet aux développeurs de stocker du code, de suivre les problèmes et de collaborer via des requêtes de tirage.

**Example:**
Créez un compte gratuit sur [GitHub](https://github.com) pour commencer à collaborer sur des projets open source.

---

## Création et Gestion des Dépôts sur GitHub

Pour créer un dépôt sur GitHub :
1. Accédez à votre tableau de bord GitHub.
2. Cliquez sur le bouton "New" pour créer un nouveau dépôt.
3. Nommez le dépôt, ajoutez une description et initialisez-le avec un fichier README.

Vous pouvez gérer les paramètres d'un dépôt, tels que la visibilité (publique/privée), les collaborateurs et les règles de protection des branches.

**Example:**
1. Créez un nouveau dépôt sur [https://github.com/new](https://github.com/new).
2. Clonez le dépôt sur votre machine locale et poussez les modifications.

---

## Clonage des Dépôts GitHub

Pour cloner un dépôt GitHub sur votre machine locale :
1. Naviguez vers le dépôt sur GitHub.
2. Copiez l'URL du dépôt.
3. Exécutez `git clone <repo_url>`.

**Example:**
```bash
git clone https://github.com/username/repo.git
```

---

## Forking des Dépôts et Requêtes de Tirage (Pull Requests)

Le forking vous permet de créer une copie personnelle du dépôt de quelqu'un d'autre pour expérimenter des modifications sans affecter l'original.

1. Cliquez sur "Fork" sur la page du dépôt original.
2. Après avoir forké, clonez le dépôt sur votre machine locale.
3. Créez une nouvelle branche, apportez des modifications et poussez-les vers votre fork.
4. Ouvrez une requête de tirage pour proposer la fusion de vos modifications dans le dépôt original.

**Example:**
```bash
git clone https://github.com/your-username/repo.git
git checkout -b branche-fonctionnalite
git push origin branche-fonctionnalite
```
Ensuite, créez une requête de tirage sur GitHub.

---

## Tickets (Issues) et Suivi des Tickets sur GitHub

Les Issues GitHub vous permettent de suivre les bogues, les tâches et les améliorations. Vous pouvez créer, assigner, étiqueter et fermer des issues au sein d'un dépôt.

- **Créer une Issue** : Cliquez sur "Issues" dans le dépôt, puis sur "New Issue".
- **Assigner des Issues** : Assignez des issues aux membres de l'équipe pour résolution.
- **Étiqueter les Issues** : Organisez les issues avec des étiquettes comme "bug", "enhancement" ou "help wanted".

**Example:**
Créez une issue pour signaler un bug :
- Titre : "L'application plante lors de la connexion"
- Description : "Décrivez les étapes pour reproduire le problème."

---

## Projets et Jalons (Milestones) GitHub

- **Projets** : Les Projets GitHub vous permettent d'organiser les tâches, les bogues et les fonctionnalités dans un tableau de type Kanban.
- **Jalons (Milestones)** : Les jalons sont utilisés pour regrouper les issues et les requêtes de tirage liées à une version ou un objectif spécifique.

**Example:**
1. Créez un tableau de projet pour suivre les tâches dans le dépôt.
2. Utilisez des jalons pour suivre l'avancement d'une fonctionnalité ou d'une version.

---

## Collaboration avec les Équipes GitHub

Les Équipes GitHub offrent un moyen d'organiser les membres en groupes avec des permissions spécifiques pour les dépôts.

- **Créer une Équipe** : Accédez au dépôt ou à l'organisation, et cliquez sur "Teams".
- **Attribuer des Permissions** : Définissez les niveaux d'accès au dépôt pour chaque équipe (par exemple, lecture, écriture, administration).
- **Collaborer** : Les membres de l'équipe peuvent examiner les requêtes de tirage, créer des issues et contribuer au dépôt.

**Example:**
- Créez une équipe "frontend" pour les membres travaillant sur le code frontend avec un accès en écriture au dépôt.

---

## GitHub Actions et Bases de l'Intégration/Déploiement Continus (CI/CD)

GitHub Actions vous permet d'automatiser des flux de travail comme l'intégration continue (CI) et le déploiement continu (CD).

- **Créer un Flux de Travail** : Définissez un fichier YAML `.github/workflows` pour spécifier les déclencheurs, tels que lors d'un push ou d'une requête de tirage.
- **Construire et Tester** : Automatisez les processus de test et de construction pour qu'ils s'exécutent chaque fois que du code est poussé vers un dépôt.

**Example:**
Un flux de travail CI simple pour exécuter des tests :
```yaml
name: Node.js CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Configurer Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - run: npm install
      - run: npm test
```

---

## Conclusion

### Points Clés à Retenir :
1. GitHub permet la collaboration sur les dépôts Git, avec des fonctionnalités telles que les requêtes de tirage, le forking et le suivi des issues.
2. Vous pouvez créer et gérer des dépôts, assigner des issues et suivre l'avancement avec les Projets et les Jalons.
3. Le forking permet de contribuer à des projets open source sans affecter le dépôt original.
4. Les Équipes GitHub facilitent la collaboration avec différents niveaux de permission sur les dépôts.
5. GitHub Actions aide à automatiser les flux de travail CI/CD directement au sein de GitHub.

### Exercice Pratique :
1. Créez un dépôt sur GitHub, clonez-le sur votre machine locale et poussez les modifications.
2. Forkez un dépôt, apportez des modifications et soumettez une requête de tirage.
3. Créez une issue pour un bug, suivez-la à l'aide d'un projet et automatisez les tests à l'aide de GitHub Actions.
