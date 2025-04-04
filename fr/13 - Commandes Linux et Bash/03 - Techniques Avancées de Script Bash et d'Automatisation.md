
# Techniques Avancées de Script Bash et d'Automatisation

Ce cours approfondit les techniques avancées de script Bash et les pratiques d'automatisation, vous aidant à écrire des scripts plus puissants, efficaces et maintenables. Vous explorerez les fonctions, la manipulation de données, le débogage, la planification de tâches et plus encore pour gérer des tâches d'automatisation complexes.

## Table des Matières
1. [Fonctions Avancées dans les Scripts Bash](#fonctions-avancees-dans-les-scripts-bash)
2. [Tableaux et Tableaux Associatifs](#tableaux-et-tableaux-associatifs)
3. [Manipulation de Chaînes de Caractères dans Bash](#manipulation-de-chaines-de-caracteres-dans-bash)
4. [Gestion des Erreurs et Débogage des Scripts Bash](#gestion-des-erreurs-et-debogage-des-scripts-bash)
5. [Travailler avec les Fichiers et les Répertoires de Manière Programmatique](#travailler-avec-les-fichiers-et-les-repertoires-de-maniere-programmatique)
6. [Planification des Tâches avec Cron et At](#planification-des-taches-avec-cron-et-at)
7. [Automatisation des Tâches d'Administration Système](#automatisation-des-taches-dadministration-systeme)
8. [Utilisation des Expressions Régulières dans Bash](#utilisation-des-expressions-regulieres-dans-bash)
9. [Utilisation de sed pour l'Édition de Flux](#utilisation-de-sed-pour-ledition-de-flux)
10. [Travailler avec des Programmes Externes et des Appels Système](#travailler-avec-des-programmes-externes-et-des-appels-systeme)

## 1. Fonctions Avancées dans les Scripts Bash
- **Définition**: Les fonctions dans Bash peuvent être utilisées pour encapsuler du code, rendant les scripts plus modulaires et réutilisables.
- **Exemple**:
  ```bash
  my_function() {
    echo "Hello, $1"
    return 0
  }
  my_function "World"
  ```
- **Explication**: Les fonctions permettent le passage de paramètres, rendant vos scripts plus propres et mieux organisés.

## 2. Tableaux et Tableaux Associatifs
- **Définition**: Les tableaux dans Bash permettent de stocker plusieurs valeurs dans une seule variable. Les tableaux associatifs utilisent des paires clé-valeur.
- **Exemple**:
  - **Indexed Array**:
    ```bash
    fruits=("Apple" "Banana" "Cherry")
    echo ${fruits[1]}  # Output: Banana
    ```
  - **Associative Array**:
    ```bash
    declare -A colors
    colors[apple]="red"
    colors[banana]="yellow"
    echo ${colors[banana]}  # Output: yellow
    ```
- **Explication**: Les tableaux indexés utilisent des index numériques, tandis que les tableaux associatifs utilisent des clés nommées.

## 3. Manipulation de Chaînes de Caractères dans Bash
- **Définition**: Bash fournit de puissantes fonctionnalités de manipulation de chaînes de caractères telles que l'extraction de sous-chaînes, le calcul de la longueur et le remplacement.
- **Exemple**:
  - **Substring**:
    ```bash
    text="Hello World"
    echo ${text:6:5}  # Output: World
    ```
  - **Length**:
    ```bash
    echo ${#text}  # Output: 11
    ```
  - **Replace**:
    ```bash
    text="Hello World"
    echo ${text/World/Bash}  # Output: Hello Bash
    ```
- **Explication**: Les opérations sur les chaînes de caractères dans Bash offrent une flexibilité pour le traitement de texte dans les scripts.

## 4. Gestion des Erreurs et Débogage des Scripts Bash
- **Définition**: Une gestion des erreurs et un débogage appropriés sont cruciaux pour la construction de scripts fiables.
- **Exemple**:
  - **Error Handling**:
    ```bash
    command_that_might_fail || echo "Command failed"
    ```
  - **Debugging**:
    ```bash
    set -x  # Enable debugging
    set +x  # Disable debugging
    ```
- **Explication**: `set -x` active le débogage, et `||` garantit que les messages d'erreur sont affichés lorsqu'une commande échoue.

## 5. Travailler avec les Fichiers et les Répertoires de Manière Programmatique
- **Définition**: L'automatisation de la gestion des fichiers et des répertoires via des scripts permet des opérations sur le système de fichiers dynamiques et flexibles.
- **Exemple**:
  - **Create File**:
    ```bash
    touch newfile.txt
    ```
  - **Create Directory**:
    ```bash
    mkdir -p /path/to/directory
    ```
  - **Check File Existence**:
    ```bash
    if [ -f "file.txt" ]; then
      echo "File exists"
    fi
    ```
- **Explication**: Bash fournit des commandes intégrées pour manipuler les fichiers et les répertoires de manière programmatique.

## 6. Planification des Tâches avec Cron et At
- **Définition**: Cron et At permettent de planifier l'exécution automatique de scripts ou de commandes à des moments spécifiés.
- **Exemple**:
  - **Cron** (run every day at 2 AM):
    ```bash
    0 2 * * * /path/to/script.sh
    ```
  - **At** (run once at a specific time):
    ```bash
    echo "/path/to/script.sh" | at 2:00 AM
    ```
- **Explication**: Cron est destiné aux tâches récurrentes, tandis qu'At est utilisé pour une exécution unique.

## 7. Automatisation des Tâches d'Administration Système
- **Définition**: Les scripts Bash sont souvent utilisés pour automatiser les tâches d'administration système de routine telles que les sauvegardes, la gestion des utilisateurs et la surveillance du système.
- **Exemple**:
  - **Backup Script**:
    ```bash
    tar -czf backup.tar.gz /home/user/
    ```
  - **User Management**:
    ```bash
    useradd newuser
    echo "newuser:password" | chpasswd
    ```
- **Explication**: L'automatisation améliore l'efficacité et réduit les erreurs humaines dans l'administration système.

## 8. Utilisation des Expressions Régulières dans Bash
- **Définition**: Les expressions régulières (regex) permettent une correspondance de motifs et une recherche de texte avancées.
- **Exemple**:
  - **grep with regex**:
    ```bash
    echo "apple banana cherry" | grep -o '\b\w*an\w*\b'  # Output: banana
    ```
  - **awk with regex**:
    ```bash
    echo "apple 10" | awk '/apple/ {print $2}'
    ```
- **Explication**: Les expressions régulières sont puissantes pour la correspondance, la recherche et le remplacement de texte dans les scripts.

## 9. Utilisation de sed pour l'Édition de Flux
- **Définition**: `sed` est un éditeur de flux utilisé pour transformer le texte dans des fichiers ou des flux d'entrée.
- **Exemple**:
  - **Replace Text**:
    ```bash
    sed 's/old/new/g' file.txt
    ```
  - **Delete Lines**:
    ```bash
    sed '/pattern/d' file.txt
    ```
- **Explication**: `sed` permet l'édition sur place, la substitution et la suppression de texte dans les fichiers.

## 10. Travailler avec des Programmes Externes et des Appels Système
- **Définition**: Les scripts Bash peuvent invoquer des programmes externes et effectuer des appels système pour interagir avec le système d'exploitation sous-jacent.
- **Exemple**:
  - **Using `curl`**:
    ```bash
    curl -O https://example.com/file.txt
    ```
  - **Using `system` for system calls**:
    ```bash
    system("ls /home/user")
    ```
- **Explication**: Bash peut interagir avec le système et des programmes externes pour étendre la fonctionnalité des scripts.

## Conclusion

### Points Clés à Retenir :
1. Les fonctions, les tableaux et la manipulation de chaînes de caractères améliorent l'efficacité et la lisibilité de vos scripts.
2. Une gestion des erreurs et un débogage appropriés sont essentiels pour la construction de scripts Bash robustes.
3. L'automatisation des tâches avec Cron et At permet de gagner du temps et garantit que les tâches sont exécutées selon le calendrier.
4. L'utilisation d'outils tels que `grep`, `sed` et `awk` permet un traitement et une manipulation de texte avancés.
5. Les scripts Bash peuvent gérer les fichiers, les répertoires et les tâches système de manière programmatique, augmentant ainsi la productivité.

### Exercice Pratique :
1. Écrivez un script qui sauvegarde un répertoire spécifique tous les jours à l'aide de Cron.
2. Créez un script qui automatise la création d'utilisateurs en acceptant un nom d'utilisateur et un mot de passe comme arguments.
3. Écrivez un script pour rechercher des fichiers contenant un motif spécifique à l'aide de `grep` et utilisez `sed` pour remplacer un terme dans ces fichiers.
4. Créez une fonction pour vérifier si un fichier existe et, sinon, créez-le avec un contenu d'exemple à l'aide de `echo`.
