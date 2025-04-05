
# Techniques Git Intermédiaires

Ce cours couvre les techniques Git intermédiaires qui vous aideront à gérer les dépôts distants, à optimiser votre flux de travail avec les étiquettes et la mise de côté (stashing), et à comprendre des concepts avancés comme le rebasage, le cherry-picking et l'index Git.

## Table des Matières

1. [Travailler avec les Dépôts Distants](#working-with-remote-repositories)
2. [Clonage des Dépôts Distants](#cloning-remote-repositories)
3. [Étiquettes Git (Tags)](#git-tags)
4. [Rebasage vs. Fusion (Merging)](#rebasing-vs-merging)
5. [Mise de Côté Git (Stash)](#git-stash)
6. [Cherry-Picking des Commits](#cherry-picking-commits)
7. [Comprendre l'Index Git et la Zone de Transit (Staging Area)](#understanding-the-git-index-and-staging-area)

---

## Travailler avec les Dépôts Distants

Les dépôts distants permettent la collaboration entre différentes machines. Pour interagir avec les dépôts distants :

- `git remote`: Liste ou modifie les dépôts distants.
- `git push`: Pousse les modifications locales vers un dépôt distant.
- `git pull`: Récupère et fusionne les modifications d'un dépôt distant.
- `git fetch`: Télécharge les modifications d'un dépôt distant sans les fusionner.

**Example:**
```bash
git remote -v
git push origin main
git pull origin main
git fetch origin
```

---

## Clonage des Dépôts Distants

Le clonage crée une copie locale d'un dépôt distant.

- `git clone <repo_url>`: Copie un dépôt distant sur votre machine locale.

**Example:**
```bash
git clone https://github.com/username/repo.git
```

---

## Étiquettes Git (Tags)

Les étiquettes Git sont utilisées pour marquer des points spécifiques dans l'historique du dépôt, généralement pour les versions ou les étapes importantes.

- `git tag`: Liste les étiquettes.
- `git tag <nom_de_l_étiquette>`: Crée une étiquette au commit actuel.
- `git push --tags`: Pousse les étiquettes vers un dépôt distant.

**Example:**
```bash
git tag v1.0
git push --tags
```

---

## Rebasage vs. Fusion (Merging)

- **Rebasage (Rebase)** : Réapplique les commits au sommet d'une autre branche de base. Il crée un historique linéaire.
- **Fusion (Merge)** : Combine les modifications de deux branches mais peut introduire des commits de fusion.

**Example:**
```bash
git rebase main
git merge branche-fonctionnalite
```

- Le rebasage est souvent utilisé pour un historique plus propre, tandis que la fusion est préférable pour préserver la structure des branches.

---

## Mise de Côté Git (Stash)

Git stash enregistre temporairement les modifications qui ne sont pas prêtes à être validées. Ceci est utile lorsque vous devez changer de tâche rapidement.

- `git stash`: Met de côté les modifications actuelles.
- `git stash apply`: Applique les dernières modifications mises de côté.
- `git stash list`: Liste toutes les modifications mises de côté.

**Example:**
```bash
git stash
git stash apply
git stash list
```

---

## Cherry-Picking des Commits

Le cherry-picking vous permet d'appliquer des commits spécifiques d'une branche à une autre.

- `git cherry-pick <hash_du_commit>`: Applique un commit d'une autre branche.

**Example:**
```bash
git cherry-pick abc1234
```

---

## Comprendre l'Index Git et la Zone de Transit (Staging Area)

L'index Git (zone de transit) est l'endroit où les modifications sont préparées avant la validation. Il contient les fichiers qui seront inclus dans le prochain commit.

- `git add <fichier>`: Ajoute les modifications à la zone de transit.
- `git reset <fichier>`: Supprime les modifications de la zone de transit mais les conserve dans le répertoire de travail.

**Example:**
```bash
git add fichier.txt
git reset fichier.txt
```

---

## Conclusion

### Points Clés à Retenir :
1. Les dépôts distants sont gérés avec des commandes comme `git remote`, `git push`, `git pull` et `git fetch`.
2. Le clonage crée une copie locale d'un dépôt distant.
3. Les étiquettes Git sont utiles pour marquer les commits importants, tels que les versions.
4. Le rebasage crée un historique de commits linéaire, tandis que la fusion préserve la structure des branches.
5. Git stash stocke temporairement les modifications, et le cherry-picking vous permet d'appliquer des commits spécifiques à d'autres branches.
6. L'index Git (zone de transit) est l'endroit où les modifications sont préparées avant la validation.

### Exercice Pratique :
1. Clonez un dépôt distant, créez une étiquette et poussez-la vers le dépôt distant.
2. Utilisez `git stash` pour enregistrer et réappliquer ultérieurement des modifications non validées.
3. Rebasez une branche de fonctionnalité sur la branche principale et résolvez les conflits éventuels.
