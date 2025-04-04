
# Commandes Bash Intermédiaires et Concepts de Script

Ce cours explore les commandes Bash intermédiaires et les concepts de script, élargissant vos connaissances pour écrire des scripts shell plus complexes et efficaces. La maîtrise de ces concepts permettra l'automatisation, la logique conditionnelle et la gestion efficace des processus au sein des scripts Bash.

## Table des Matières
1. [Comprendre le Scripting Shell Bash](#comprendre-le-scripting-shell-bash)
2. [Variables et Types de Données dans Bash](#variables-et-types-de-donnees-dans-bash)
3. [Conditionnelles (if, elif, else)](#conditionnelles-if-elif-else)
4. [Boucles (for, while, until)](#boucles-for-while-until)
5. [Fonctions et Arguments dans les Scripts Bash](#fonctions-et-arguments-dans-les-scripts-bash)
6. [Gestion des Entrées et Sorties dans les Scripts](#gestion-des-entrees-et-sorties-dans-les-scripts)
7. [Opérateurs de Test de Fichiers](#operateurs-de-test-de-fichiers)
8. [Redirection de la Sortie et des Erreurs](#redirection-de-la-sortie-et-des-erreurs)
9. [Création et Utilisation d'Alias Bash Personnalisés](#creation-et-utilisation-dalias-bash-personnalises)
10. [Contrôle des Jobs et Processus en Arrière-Plan](#controle-des-jobs-et-processus-en-arriere-plan)

## 1. Comprendre le Scripting Shell Bash
- **Définition**: Le scripting Bash est une manière d'automatiser des tâches en écrivant une série de commandes dans un fichier texte que le shell peut exécuter.
- **Exemple**: A basic script to print "Hello, World":
  ```bash
  #!/bin/bash
  echo "Hello, World"
  ```
- **Explication**: La première ligne `#!/bin/bash` spécifie l'interpréteur, et le script exécute la commande `echo` pour afficher du texte.

## 2. Variables et Types de Données dans Bash
- **Définition**: Bash permet l'utilisation de variables pour stocker des données, et bien que Bash ne soit pas typé, les variables peuvent contenir des chaînes de caractères, des entiers ou des tableaux.
- **Exemple**:
  ```bash
  name="Alice"
  age=25
  echo "Name: $name, Age: $age"
  ```
- **Explication**: Les variables sont créées sans déclaration de type et référencées à l'aide de `$`.

## 3. Conditionnelles (if, elif, else)
- **Définition**: Les conditionnelles permettent une logique de branchement basée sur des tests booléens.
- **Exemple**:
  ```bash
  if [ $age -ge 18 ]; then
    echo "Adult"
  else
    echo "Minor"
  fi
  ```
- **Explication**: L'instruction `if` vérifie les conditions ; `-ge` est utilisé pour vérifier si l'âge est supérieur ou égal à 18.

## 4. Boucles (for, while, until)
- **Définition**: Les boucles permettent de répéter des tâches plusieurs fois.
- **Exemple**:
  - **For loop**:
    ```bash
    for i in {1..5}; do
      echo "Number $i"
    done
    ```
  - **While loop**:
    ```bash
    count=1
    while [ $count -le 5 ]; do
      echo "Count $count"
      ((count++))
    done
    ```
- **Explication**: La boucle `for` itère sur une plage, et la boucle `while` s'exécute tant qu'une condition est vraie.

## 5. Fonctions et Arguments dans les Scripts Bash
- **Définition**: Les fonctions permettent une écriture de scripts modulaire et la réutilisation de code.
- **Exemple**:
  ```bash
  greet() {
    echo "Hello, $1!"
  }
  greet Alice
  ```
- **Explication**: `$1` fait référence au premier argument passé à la fonction.

## 6. Gestion des Entrées et Sorties dans les Scripts
- **Définition**: Bash fournit des mécanismes pour interagir avec l'utilisateur et gérer la sortie.
- **Exemple**:
  - **Input**:
    ```bash
    read -p "Enter your name: " name
    echo "Hello, $name"
    ```
  - **Output**:
    ```bash
    printf "Hello, %s!\n" "$name"
    ```
- **Explication**: `read` prend l'entrée de l'utilisateur, et `echo` ou `printf` affichent les données.

## 7. Opérateurs de Test de Fichiers
- **Définition**: Les opérateurs de test de fichiers vérifient les attributs des fichiers ou des répertoires.
- **Exemple**:
  ```bash
  if [ -f "file.txt" ]; then
    echo "File exists"
  fi
  ```
- **Explication**: Le `-f` vérifie si le fichier existe et est un fichier régulier. D'autres opérateurs incluent `-d`, `-r`, `-w` et `-x` pour vérifier l'existence du répertoire, la lisibilité, l'écrivabilité et l'exécutabilité.

## 8. Redirection de la Sortie et des Erreurs
- **Définition**: La sortie et les erreurs peuvent être redirigées vers des fichiers ou d'autres commandes.
- **Exemple**:
  - Redirect standard output:
    ```bash
    ls > files.txt
    ```
  - Redirect standard error:
    ```bash
    ls non_existent_file 2> error.log
    ```
  - Redirect both output and error:
    ```bash
    ls > output.txt 2>&1
    ```
- **Explication**: `>` redirige la sortie, et `2>&1` redirige les erreurs vers le même emplacement.

## 9. Création et Utilisation d'Alias Bash Personnalisés
- **Définition**: Les alias permettent de créer des commandes abrégées pour simplifier les commandes fréquemment utilisées.
- **Exemple**:
  ```bash
  alias ll='ls -l'
  alias gs='git status'
  ```
- **Explication**: Les alias sont définis à l'aide de `alias` et peuvent être ajoutés à `.bashrc` pour les rendre persistants.

## 10. Contrôle des Jobs et Processus en Arrière-Plan
- **Définition**: Le contrôle des jobs permet de gérer les processus en arrière-plan et de contrôler les tâches.
- **Exemple**:
  - Run a command in the background:
    ```bash
    long_running_process &
    ```
  - Bring a background job to the foreground:
    ```bash
    fg %1
    ```
  - Check jobs:
    ```bash
    jobs
    ```
- **Explication**: Le symbole `&` exécute les commandes en arrière-plan, tandis que `fg` ramène les jobs au premier plan.

## Conclusion

### Points Clés à Retenir :
1. Le scripting Bash permet d'automatiser les tâches et de créer des flux de travail complexes.
2. Les variables et les fonctions sont essentielles pour écrire des scripts modulaires et réutilisables.
3. La compréhension des conditionnelles et des boucles est essentielle pour la logique de branchement et d'itération.
4. Les opérateurs de test de fichiers et la redirection de la sortie améliorent la gestion des fichiers et la gestion des erreurs.
5. Le contrôle des jobs aide à gérer efficacement les processus et les tâches en arrière-plan.

### Exercice Pratique :
1. Écrivez un script qui invite l'utilisateur à entrer son âge et affiche s'il est adulte ou mineur en utilisant des conditionnelles.
2. Créez un script qui accepte un nom de fichier comme argument et vérifie s'il existe à l'aide des opérateurs de test de fichiers.
3. Écrivez un script qui parcourt une liste d'éléments et les affiche un par un à l'aide d'une boucle `for`.
4. Utilisez la redirection pour capturer la sortie de `ls` et tous les messages d'erreur dans des fichiers séparés.
