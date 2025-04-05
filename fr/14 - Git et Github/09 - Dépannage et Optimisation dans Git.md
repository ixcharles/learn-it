
# Dépannage et Optimisation dans Git

Ce cours couvre les techniques de dépannage des problèmes Git courants, la récupération des commits perdus et l'optimisation des dépôts pour la performance et l'efficacité.

## Table des Matières

1.  [Résolution des Conflits de Fusion](#resolving-merge-conflicts)
2.  [Débogage Git et Récupération des Commits Perdus](#git-debugging-and-recovering-lost-commits)
3.  [Optimisation de l'Historique du Dépôt et Réduction de la Taille du Dépôt](#optimizing-repository-history-and-reducing-repo-size)
4.  [Utilisation de Reflog pour Récupérer des Données](#using-reflog-to-recover-data)
5.  [Analyse Avancée des Logs Git (`git log`, `git blame`, `git bisect`)](#advanced-git-log-analysis-git-log-git-blame-git-bisect)

---

## Résolution des Conflits de Fusion

Les conflits de fusion se produisent lorsque Git ne peut pas réconcilier automatiquement les modifications entre deux branches. Voici comment les résoudre.

### Étapes :

1.  **Identifier les Conflits** : Git marque les fichiers en conflit avec des marqueurs de conflit (`<<<<<<<`, `=======`, `>>>>>>>`).
2.  **Résoudre** : Modifiez manuellement les fichiers en conflit pour combiner les modifications.
3.  **Indexer les Modifications** : Après avoir résolu les conflits, indexez les fichiers à l'aide de `git add`.
4.  **Commiter** : Terminez la fusion avec `git commit`.

**Example:**

```bash
git merge branche-fonctionnalite
# Git affichera des marqueurs de conflit dans les fichiers concernés
# Modifiez et résolvez les conflits, puis :
git add fichier-en-conflit.txt
git commit -m "Conflits de fusion résolus"
```

---

## Débogage Git et Récupération des Commits Perdus

Si des commits sont accidentellement perdus, vous pouvez souvent les récupérer à l'aide des fonctionnalités de débogage de Git.

### Récupération des Commits Perdus :

1.  **Utilisation de `git reflog`** : Git enregistre l'historique de votre HEAD, ce qui vous permet de retrouver les commits perdus.
2.  **Annulation d'un Reset** : Si vous avez accidentellement fait un reset vers un commit antérieur, utilisez `git reflog` pour récupérer le commit perdu.

**Example:**

```bash
# Afficher le reflog et trouver le commit perdu
git reflog
# Réinitialiser vers le commit souhaité
git reset --hard <hash-du-commit>
```

---

## Optimisation de l'Historique du Dépôt et Réduction de la Taille du Dépôt

Les dépôts peuvent devenir volumineux et inefficaces avec le temps. Voici comment les optimiser.

### Optimiser l'Historique :

* **Écraser les Commits (Squash)** : Utilisez `git rebase -i` pour écraser plusieurs commits en un seul, nettoyant ainsi votre historique.
* **Supprimer les Branches Inutilisées** : Supprimez les branches dont vous n'avez plus besoin avec `git branch -d nom-de-la-branche`.

### Réduire la Taille du Dépôt :

* **Supprimer les Gros Fichiers** : Utilisez `git filter-branch` ou `BFG Repo-Cleaner` pour supprimer les gros fichiers de l'historique.
* **Nettoyer les Objets Inaccessibles** : Utilisez `git gc` (garbage collection) pour nettoyer les objets inutiles et réduire la taille du dépôt.

**Example (Écrasement des commits):**

```bash
git rebase -i HEAD~5
# Marquer les commits à écraser
git push --force
```

---

## Utilisation de Reflog pour Récupérer des Données

La commande `git reflog` fournit un historique des modifications apportées à vos branches locales et à HEAD, ce qui la rend inestimable pour la récupération du travail perdu.

### Comment Utiliser Reflog :

1.  **Afficher Reflog** : Utilisez `git reflog` pour afficher un historique des modifications.
2.  **Récupérer les Commits Perdus** : Trouvez le hash du commit perdu et réinitialisez votre branche vers ce commit.

**Example:**

```bash
git reflog
# Identifier le commit que vous souhaitez récupérer
git reset --hard <hash-du-commit>
```

---

## Analyse Avancée des Logs Git (`git log`, `git blame`, `git bisect`)

Git fournit plusieurs commandes pour analyser votre historique de commits et déboguer les problèmes.

### `git log` :

Utilisez `git log` pour afficher l'historique des commits. Vous pouvez personnaliser la sortie avec des options comme `--oneline`, `--graph` et `--author`.

**Example:**

```bash
git log --oneline --graph --decorate
```

### `git blame` :

Utilisez `git blame` pour identifier qui a modifié en dernier chaque ligne d'un fichier. Ceci est utile pour déboguer les problèmes et retrouver l'origine des bugs.

**Example:**

```bash
git blame fichier.txt
```

### `git bisect` :

Utilisez `git bisect` pour trouver le commit qui a introduit un bug en effectuant une recherche binaire dans votre historique de commits.

**Example:**

```bash
git bisect start
git bisect bad # Marquer le commit actuel comme mauvais
git bisect good <hash-du-commit> # Marquer un commit antérieur comme bon
# Git va extraire un commit intermédiaire, et vous continuez à le marquer comme bon ou mauvais
```

---

## Conclusion

### Points Clés à Retenir :

1.  Les **Conflits de Fusion** peuvent être résolus en modifiant manuellement les fichiers en conflit, en les indexant et en committant les modifications résolues.
2.  Le **Débogage Git** aide à récupérer les commits perdus à l'aide d'outils comme `git reflog`.
3.  L'**Optimisation de la Taille du Dépôt** implique l'écrasement des commits et la suppression des gros fichiers de l'historique Git.
4.  **Reflog** est inestimable pour le suivi et la récupération des données qui ont été perdues ou écrasées.
5.  L'**Analyse des Logs Git** avec `git log`, `git blame` et `git bisect` aide à identifier l'historique des modifications et à isoler les problèmes.

### Exercice Pratique :

1.  Créez un conflit en apportant des modifications différentes au même fichier dans deux branches, puis résolvez le conflit.
2.  Utilisez `git reflog` pour trouver et récupérer un commit perdu.
3.  Nettoyez un dépôt en écrasant les commits et en supprimant les gros fichiers à l'aide de `git filter-branch`.
4.  Utilisez `git blame` pour retrouver l'origine d'un bug dans un fichier.
5.  Effectuez un `git bisect` pour identifier le commit qui a introduit un bug.
