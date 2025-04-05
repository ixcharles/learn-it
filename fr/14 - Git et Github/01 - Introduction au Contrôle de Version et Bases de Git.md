
# Introduction au Contrôle de Version et Bases de Git

Le contrôle de version est essentiel pour gérer les modifications de code et collaborer avec d'autres dans le développement logiciel. Ce cours couvre les concepts fondamentaux de Git, un système de contrôle de version largement utilisé, y compris l'installation, les commandes de base et les flux de travail.

## Table des Matières

1. [Qu'est-ce que le Contrôle de Version ?](#what-is-version-control)
2. [Git vs. Autres Systèmes de Contrôle de Version](#git-vs-other-version-control-systems)
3. [Installation de Git](#installing-git)
4. [Commandes Git de Base](#basic-git-commands)
5. [Structure d'un Dépôt Git](#git-repository-structure)
6. [Comprendre le Flux de Travail Git (Local & Distant)](#understanding-git-workflow-local-remote)
7. [Configuration de Git](#configuring-git)
8. [Comprendre `.gitignore`](#understanding-gitignore)

---

## Qu'est-ce que le Contrôle de Version ?

Le contrôle de version est un système qui enregistre les modifications apportées à un fichier ou à un ensemble de fichiers au fil du temps, permettant aux utilisateurs de suivre, d'annuler et de collaborer sur les modifications.

**Example:**
When working on a project, version control allows you to see how a file has evolved, who changed it, and why.

---

## Git vs. Autres Systèmes de Contrôle de Version

Git est un système de contrôle de version distribué, ce qui signifie que chaque contributeur possède une copie complète du dépôt. D'autres systèmes comme SVN sont centralisés, nécessitant un accès à un serveur central.

**Example:**
Git allows offline work and full history access, unlike SVN, which requires a constant connection to a central server.

---

## Installation de Git

Pour installer Git, téléchargez-le depuis [git-scm.com](https://git-scm.com) et suivez les étapes d'installation pour votre système d'exploitation.

**Example:**
For macOS, use Homebrew:
```bash
brew install git
```

---

## Commandes Git de Base

- `git init`: Initialise un nouveau dépôt Git.
- `git clone <repo_url>`: Clone un dépôt existant depuis un serveur distant.
- `git status`: Affiche l'état actuel du dépôt (fichiers indexés, non indexés, non suivis).

**Example:**
```bash
git init
git clone https://github.com/username/repo.git
git status
```

---

## Structure d'un Dépôt Git

Un dépôt Git contient trois zones principales :
1. **Répertoire de Travail**: Fichiers sur votre machine locale.
2. **Zone de Transit (Staging Area)**: Fichiers marqués pour le prochain commit.
3. **Dépôt (Repository)**: La base de données où Git stocke toutes les versions des fichiers.

**Example:**
When you `git add` a file, it's moved from the working directory to the staging area.

---

## Comprendre le Flux de Travail Git (Local & Distant)

- **Flux de Travail Local**: Implique de travailler avec vos fichiers locaux, de valider les modifications (commits) et de gérer les branches.
- **Flux de Travail Distant**: Implique de pousser les commits locaux vers un serveur distant (par exemple, GitHub) et de récupérer les modifications apportées par d'autres.

**Example:**
```bash
git push origin master
git pull origin master
```

---

## Configuration de Git

Configurez votre nom et votre adresse e-mail pour Git en utilisant :
```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

**Example:**
This configuration ensures your commits are correctly attributed to you.

---

## Comprendre `.gitignore`

Un fichier `.gitignore` indique à Git les fichiers ou répertoires à ignorer lors de la validation des modifications (commits).

**Example:**
```bash
# Ignore all .log files
*.log
```

---

## Conclusion

### Points Clés à Retenir :
1. Le contrôle de version est crucial pour la gestion des modifications de code et la collaboration.
2. Git est un système de contrôle de version distribué qui prend en charge les flux de travail locaux et distants.
3. Les commandes Git de base (`git init`, `git clone`, `git status`) sont essentielles pour la gestion des dépôts.
4. Les dépôts Git sont constitués du répertoire de travail, de la zone de transit et du dépôt local.
5. `.gitignore` est utilisé pour exclure les fichiers inutiles du contrôle de version.

### Exercice Pratique :
1. Installez Git et configurez votre nom et votre adresse e-mail.
2. Créez un nouveau dépôt, ajoutez un fichier et validez les modifications.
3. Clonez un dépôt distant, effectuez des modifications et repoussez-les vers le dépôt distant.
