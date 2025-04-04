
# Introduction aux Commandes Linux et Notions de Base du Shell Bash

Ce cours fournit un aperçu essentiel des commandes Linux et des notions de base du shell Bash, offrant des connaissances fondamentales pour travailler avec le terminal Linux. La maîtrise de ces commandes est cruciale pour tout développeur travaillant sur des systèmes basés sur Linux.

## Table des Matières
1. [Introduction à la Ligne de Commande Linux](#introduction-a-la-ligne-de-commande-linux)
2. [Navigation dans le Système de Fichiers](#navigation-dans-le-systeme-de-fichiers)
3. [Comprendre et Gérer les Permissions de Fichiers](#comprendre-et-gerer-les-permissions-de-fichiers)
4. [Travailler avec les Répertoires](#travailler-avec-les-repertoires)
5. [Afficher et Manipuler le Contenu des Fichiers](#afficher-et-manipuler-le-contenu-des-fichiers)
6. [Introduction aux Caractères Génériques et à la Globbing de Fichiers](#introduction-aux-caracteres-generiques-et-a-la-globbing-de-fichiers)
7. [Opérations de Base sur les Fichiers](#operations-de-base-sur-les-fichiers)
8. [Redirection et Tubes](#redirection-et-tubes)
9. [Comprendre les Variables d'Environnement](#comprendre-les-variables-denvironnement)
10. [Édition de Texte de Base avec Nano et Vim](#edition-de-texte-de-base-avec-nano-et-vim)

## 1. Introduction à la Ligne de Commande Linux
- **Définition**: La ligne de commande sous Linux permet aux utilisateurs d'interagir avec le système d'exploitation via des commandes textuelles.
- **Exemple**: Opening a terminal window and typing `ls` to list files.
- **Explication**: Le terminal est une interface puissante pour gérer les fichiers, exécuter des applications et configurer les paramètres du système.

## 2. Navigation dans le Système de Fichiers
- **Définition**: La ligne de commande permet la navigation dans la structure des répertoires à l'aide de commandes telles que `cd`, `pwd` et `ls`.
- **Exemple**:
  - `cd /home/user/Documents` (change directory)
  - `pwd` (print current working directory)
  - `ls` (list files in the current directory)
- **Explication**: Ces commandes permettent un déplacement efficace entre les répertoires et la visualisation du contenu de votre système de fichiers.

## 3. Comprendre et Gérer les Permissions de Fichiers
- **Définition**: Les fichiers et répertoires Linux ont des permissions pour le propriétaire, le groupe et les autres pour lire, écrire et exécuter.
- **Exemple**:
  - `chmod 755 file.txt` (set permissions to rwx for owner, rx for group and others)
  - `chown user:group file.txt` (change file ownership)
  - `chgrp group file.txt` (change file group)
- **Explication**: Les permissions contrôlent l'accès aux fichiers et répertoires, assurant la sécurité et un contrôle d'accès approprié.

## 4. Travailler avec les Répertoires
- **Définition**: Les répertoires organisent les fichiers sous Linux, et des commandes comme `mkdir`, `rmdir` et `ln` aident à les gérer.
- **Exemple**:
  - `mkdir new_directory` (create a directory)
  - `rmdir empty_directory` (remove an empty directory)
  - `ln -s /path/to/file link_name` (create a symbolic link)
- **Explication**: Les répertoires aident à structurer les fichiers, et les liens symboliques créent des raccourcis vers des fichiers ou des répertoires.

## 5. Afficher et Manipuler le Contenu des Fichiers
- **Définition**: Des commandes comme `cat`, `more`, `less`, `head` et `tail` permettent aux utilisateurs d'afficher et de manipuler le contenu des fichiers.
- **Exemple**:
  - `cat file.txt` (display entire file content)
  - `head file.txt` (show the first 10 lines of a file)
  - `tail file.txt` (show the last 10 lines of a file)
- **Explication**: Ces commandes sont essentielles pour inspecter et naviguer rapidement dans les fichiers sans ouvrir d'éditeur.

## 6. Introduction aux Caractères Génériques et à la Globbing de Fichiers
- **Définition**: Les caractères génériques permettent aux utilisateurs de faire correspondre des motifs dans les noms de fichiers pour le traitement par lots.
- **Exemple**:
  - `ls *.txt` (list all `.txt` files in the current directory)
  - `rm *.log` (remove all `.log` files)
- **Explication**: Les caractères génériques augmentent la flexibilité lorsque vous travaillez avec plusieurs fichiers à la fois, ce qui permet d'économiser du temps et des efforts.

## 7. Opérations de Base sur les Fichiers
- **Définition**: Linux fournit plusieurs commandes pour gérer les fichiers, telles que la copie, le déplacement, la suppression et la création de fichiers.
- **Exemple**:
  - `cp file1.txt file2.txt` (copy file1.txt to file2.txt)
  - `mv file1.txt /path/to/new/location` (move file1.txt to a new directory)
  - `rm file.txt` (delete file.txt)
  - `touch newfile.txt` (create an empty file)
- **Explication**: Ces opérations de base sur les fichiers sont le fondement de la gestion des fichiers sous Linux.

## 8. Redirection et Tubes
- **Définition**: La redirection et les tubes permettent aux utilisateurs de contrôler le flux d'entrée et de sortie entre les commandes.
- **Exemple**:
  - `ls > file_list.txt` (redirect output of `ls` to a file)
  - `cat file.txt | grep "pattern"` (search for a pattern in the file using pipe)
- **Explication**: La redirection (`>`, `<`) et les tubes (`|`) permettent des combinaisons puissantes de commandes pour le traitement avancé des données.

## 9. Comprendre les Variables d'Environnement
- **Définition**: Les variables d'environnement stockent des informations système et des paramètres de configuration.
- **Exemple**:
  - `echo $PATH` (display the system's PATH variable)
  - `export MY_VAR="value"` (set a custom environment variable)
- **Explication**: Ces variables sont cruciales pour la configuration du système et influencent la manière dont les applications et les scripts s'exécutent.

## 10. Édition de Texte de Base avec Nano et Vim
- **Définition**: Nano et Vim sont des éditeurs de texte disponibles dans le terminal pour créer et modifier des fichiers.
- **Exemple**:
  - `nano file.txt` (open file in Nano editor)
  - `vim file.txt` (open file in Vim editor)
- **Explication**: Nano est convivial pour les débutants, tandis que Vim est un éditeur plus avancé avec des fonctionnalités puissantes pour une édition efficace.

## Conclusion

### Points Clés à Retenir :
1. La ligne de commande Linux est un outil puissant pour gérer le système et automatiser les tâches.
2. La navigation et la manipulation de fichiers sont des compétences essentielles dans l'environnement Linux.
3. La compréhension des permissions et de la propriété des fichiers est cruciale pour la sécurité du système.
4. La maîtrise de la redirection, des tubes et des variables d'environnement peut rationaliser les flux de travail.
5. La familiarité avec les éditeurs de texte comme Nano et Vim est essentielle pour une édition de fichiers efficace.

### Exercice Pratique :
1. Utilisez les commandes `cd`, `ls` et `pwd` pour naviguer dans différents répertoires de votre système.
2. Créez un répertoire, définissez ses permissions et créez un fichier à l'intérieur à l'aide de `mkdir`, `chmod` et `touch`.
3. Ouvrez un fichier à l'aide de `nano` ou `vim`, modifiez-le, enregistrez-le et fermez l'éditeur.
4. Expérimentez avec la redirection de fichiers en enregistrant la sortie d'une commande comme `ls` dans un fichier.
