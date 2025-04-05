
# Opérations Git de Base

Ce cours couvre les opérations Git essentielles que tout développeur devrait connaître, de la création de dépôts à la gestion des branches et à la résolution des conflits.

## Table des Matières

1. [Création et Gestion des Dépôts](#creating-and-managing-repositories)
2. [Indexation et Validation des Modifications](#staging-and-committing-changes)
3. [Visualisation des Modifications](#viewing-changes)
4. [Annulation des Modifications](#undoing-changes)
5. [Bases du Branching Git](#git-branching-basics)
6. [Fusion des Branches](#merging-branches)
7. [Résolution des Conflits de Fusion](#resolving-merge-conflicts)

---

## Création et Gestion des Dépôts

Un dépôt dans Git stocke les fichiers de votre projet et leur historique des versions. Pour créer et gérer des dépôts :

- `git init`: Initialise un nouveau dépôt Git dans le répertoire courant.
- `git clone <repo_url>`: Crée une copie d'un dépôt existant à partir d'une source distante.

**Example:**
```bash
git init
git clone https://github.com/username/repo.git
```

---

## Indexation et Validation des Modifications

- **Indexation (Staging)** : Ajoute des fichiers à la zone de transit avant la validation.
  - `git add <fichier>`: Ajoute un fichier à la zone de transit.
- **Validation (Committing)** : Enregistre les modifications dans le dépôt avec un message.
  - `git commit -m "message"`: Enregistre les modifications dans le dépôt.

**Example:**
```bash
git add fichier.txt
git commit -m "Ajout de fichier.txt avec contenu initial"
```

---

## Visualisation des Modifications

- `git diff`: Affiche les différences entre le répertoire de travail et la zone de transit.
- `git log`: Affiche l'historique des validations (commits) dans le dépôt.

**Example:**
```bash
git diff
git log
```

---

## Annulation des Modifications

- **Annuler les Modifications Indexées**: Déplace les modifications de la zone de transit vers le répertoire de travail.
  - `git reset <fichier>`: Désindexe un fichier.
- **Annuler les Modifications Locales**: Annule les modifications dans le répertoire de travail.
  - `git checkout -- <fichier>`: Abandonne les modifications dans le répertoire de travail.

**Example:**
```bash
git reset fichier.txt
git checkout -- fichier.txt
```

---

## Bases du Branching Git

Le branching vous permet de travailler simultanément sur différentes versions d'un projet.

- `git branch`: Liste, crée ou supprime des branches.
- `git checkout -b <nom_de_la_branche>`: Crée une nouvelle branche et bascule vers celle-ci.

**Example:**
```bash
git branch
git checkout -b branche-fonctionnalite
```

---

## Fusion des Branches

La fusion combine les modifications d'une branche dans une autre.

- `git merge <nom_de_la_branche>`: Fusionne les modifications de la branche spécifiée dans la branche courante.

**Example:**
```bash
git checkout main
git merge branche-fonctionnalite
```

---

## Résolution des Conflits de Fusion

Les conflits de fusion se produisent lorsque les modifications dans différentes branches ne peuvent pas être fusionnées automatiquement.

- **Résolution Manuelle des Conflits**: Git marque les fichiers en conflit. Vous devez modifier ces fichiers pour résoudre les conflits.
- Après la résolution, ajoutez les fichiers résolus à la zone de transit et validez.

**Example:**
```bash
git add fichier-en-conflit.txt
git commit -m "Conflit de fusion résolu"
```

---

## Conclusion

### Points Clés à Retenir :
1. Les dépôts sont créés à l'aide de `git init` ou clonés avec `git clone`.
2. L'indexation et la validation des modifications garantissent que votre code est enregistré dans le dépôt.
3. La visualisation des modifications avec `git diff` et `git log` aide à suivre l'avancement.
4. L'annulation des modifications peut être effectuée à l'aide de `git reset` et `git checkout`.
5. Le branching et le merging sont essentiels pour travailler sur des fonctionnalités de manière isolée et combiner le travail.
6. Les conflits de fusion sont résolus en modifiant manuellement les fichiers et en validant la résolution.

### Exercice Pratique :
1. Créez un nouveau dépôt, ajoutez des fichiers et validez les modifications.
2. Créez une branche, effectuez des modifications et fusionnez-la dans la branche principale.
3. Créez un conflit entre les branches et résolvez-le manuellement.
