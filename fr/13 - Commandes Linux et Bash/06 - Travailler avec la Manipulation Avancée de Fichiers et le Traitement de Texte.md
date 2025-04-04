
# Travailler avec la Manipulation Avancée de Fichiers et le Traitement de Texte

Ce cours couvre les techniques avancées de manipulation de fichiers, de traitement de texte et d'automatisation des flux de données sous Linux. La maîtrise de ces compétences vous permettra de gérer efficacement des opérations de fichiers complexes, d'extraire et de manipuler des données, et d'automatiser la génération de rapports.

## Table des Matières
1. [Maîtriser les Permissions et la Propriété des Fichiers](#maitriser-les-permissions-et-la-propriete-des-fichiers)
2. [Compression et Archivage de Fichiers](#compression-et-archivage-de-fichiers)
3. [Recherche Avancée de Texte avec grep et awk](#recherche-avancee-de-texte-avec-grep-et-awk)
4. [Analyse de Fichiers et Génération de Rapports avec awk](#analyse-de-fichiers-et-generation-de-rapports-avec-awk)
5. [Traitement de Texte avec sed](#traitement-de-texte-avec-sed)
6. [Travailler avec JSON et XML dans les Scripts Bash](#travailler-avec-json-et-xml-dans-les-scripts-bash)
7. [Les Expressions Régulières en Détail](#les-expressions-regulieres-en-detail)
8. [Travailler avec de Grands Fichiers et des Flux](#travailler-avec-de-grands-fichiers-et-des-flux)
9. [Tri et Filtrage de Données](#tri-et-filtrage-de-donnees)
10. [Analyse des Fichiers CSV et des Fichiers Journaux avec Bash](#analyse-des-fichiers-csv-et-des-fichiers-journaux-avec-bash)

## 1. Maîtriser les Permissions et la Propriété des Fichiers
- **Définition**: Les permissions de fichiers Linux définissent qui peut lire, écrire ou exécuter des fichiers. La propriété contrôle qui peut modifier les permissions.
- **Exemple**:
  - **Change Permissions**:
    ```bash
    chmod 755 filename
    ```
  - **Change Ownership**:
    ```bash
    chown user:group filename
    ```
  - **Set ACL**:
    ```bash
    setfacl -m u:user:rw filename
    ```
- **Explication**: `chmod` modifie les permissions, `chown` change la propriété du fichier et `setfacl` gère les listes de contrôle d'accès pour des permissions plus granulaires.

## 2. Compression et Archivage de Fichiers
- **Définition**: La compression de fichiers réduit la taille de stockage, et l'archivage regroupe plusieurs fichiers en un seul paquet pour une gestion plus facile.
- **Exemple**:
  - **Create a tar Archive**:
    ```bash
    tar -cvf archive.tar file1 file2
    ```
  - **Compress with gzip**:
    ```bash
    gzip file
    ```
  - **Extract a zip file**:
    ```bash
    unzip archive.zip
    ```
- **Explication**: `tar` est utilisé pour créer des archives, `gzip` compresse les fichiers et `unzip` extrait les fichiers zip compressés.

## 3. Recherche Avancée de Texte avec grep et awk
- **Définition**: `grep` est utilisé pour rechercher des motifs de texte, tandis que `awk` permet un traitement de texte et une correspondance de motifs plus complexes.
- **Exemple**:
  - **Search with grep**:
    ```bash
    grep 'pattern' filename
    ```
  - **Advanced Search with awk**:
    ```bash
    awk '/pattern/ {print $1}' filename
    ```
- **Explication**: `grep` recherche des motifs simples, et `awk` peut effectuer une extraction et une manipulation de données avancées basées sur des motifs.

## 4. Analyse de Fichiers et Génération de Rapports avec awk
- **Définition**: `awk` est un outil puissant pour l'analyse et le traitement de fichiers texte, particulièrement utile pour la génération de rapports.
- **Exemple**:
  - **Print Specific Columns**:
    ```bash
    awk '{print $1, $3}' file.txt
    ```
  - **Sum Values in Column**:
    ```bash
    awk '{sum+=$2} END {print sum}' file.txt
    ```
- **Explication**: `awk` divise l'entrée en champs et effectue des actions sur ceux-ci, ce qui le rend idéal pour la génération et l'analyse de rapports.

## 5. Traitement de Texte avec sed
- **Définition**: `sed` est un éditeur de flux pour transformer le texte dans un pipeline ou un fichier, utile pour la substitution, la suppression et l'insertion de texte.
- **Exemple**:
  - **Substitute Text**:
    ```bash
    sed 's/old/new/g' file.txt
    ```
  - **Delete Line**:
    ```bash
    sed '3d' file.txt
    ```
- **Explication**: `sed` effectue des transformations de texte telles que des substitutions et des suppressions basées sur des motifs.

## 6. Travailler avec JSON et XML dans les Scripts Bash
- **Définition**: L'analyse et la manipulation de données structurées comme JSON et XML sont courantes dans le traitement de données et l'intégration de services web.
- **Exemple**:
  - **Parse JSON with jq**:
    ```bash
    jq '.key' file.json
    ```
  - **Parse XML with xmllint**:
    ```bash
    xmllint --xpath "//tag" file.xml
    ```
- **Explication**: `jq` et `xmllint` sont des outils spécialisés pour l'analyse et l'interrogation des données JSON et XML respectivement.

## 7. Les Expressions Régulières en Détail
- **Définition**: Les expressions régulières (regex) sont des motifs utilisés pour faire correspondre et manipuler des chaînes de caractères en fonction de règles spécifiques.
- **Exemple**:
  - **Simple regex with grep**:
    ```bash
    grep '^abc' file.txt
    ```
  - **Advanced regex with awk**:
    ```bash
    awk '/^[0-9]{3}-[0-9]{2}-[0-9]{4}/' file.txt
    ```
- **Explication**: Les expressions régulières sont puissantes pour la correspondance de motifs, et des outils comme `grep` et `awk` les utilisent pour la recherche et le traitement de texte.

## 8. Travailler avec de Grands Fichiers et des Flux
- **Définition**: Les grands fichiers peuvent être difficiles à manipuler en mémoire, c'est pourquoi les outils Linux offrent des moyens de traiter les fichiers ligne par ligne ou par blocs.
- **Exemple**:
  - **Process Large Files with awk**:
    ```bash
    awk '{print $1}' largefile.txt
    ```
  - **Stream Output with less**:
    ```bash
    cat largefile.txt | less
    ```
- **Explication**: `awk` traite efficacement les grands fichiers, et `less` permet de visualiser de grands fichiers de manière interactive sans les charger complètement en mémoire.

## 9. Tri et Filtrage de Données
- **Définition**: Le tri et le filtrage des données sont essentiels pour organiser et analyser de grands ensembles de données.
- **Exemple**:
  - **Sort Data**:
    ```bash
    sort file.txt
    ```
  - **Remove Duplicates**:
    ```bash
    uniq file.txt
    ```
  - **Cut Columns from Data**:
    ```bash
    cut -d',' -f1 file.csv
    ```
- **Explication**: `sort` organise les données, `uniq` supprime les lignes en double et `cut` extrait des colonnes spécifiques des fichiers.

## 10. Analyse des Fichiers CSV et des Fichiers Journaux avec Bash
- **Définition**: L'analyse des fichiers CSV et des fichiers journaux est essentielle pour extraire des informations significatives à partir de données structurées.
- **Exemple**:
  - **Parse CSV**:
    ```bash
    awk -F',' '{print $1, $2}' file.csv
    ```
  - **Extract Logs for Errors**:
    ```bash
    grep 'ERROR' /var/log/syslog
    ```
- **Explication**: `awk` est utilisé pour analyser les fichiers CSV en spécifiant un délimiteur, et `grep` aide à filtrer les journaux pour des motifs spécifiques comme les erreurs.

## Conclusion

### Points Clés à Retenir :
1. La maîtrise des permissions et de la propriété des fichiers est essentielle pour la gestion de la sécurité et du contrôle d'accès.
2. Des outils comme `tar`, `gzip` et `zip` sont essentiels pour la compression et l'archivage des fichiers, tandis que `unzip` les extrait.
3. Le traitement de texte avancé avec `grep`, `awk` et `sed` permet une manipulation et une extraction efficaces des données des fichiers.
4. Les expressions régulières sont un outil essentiel pour la correspondance de motifs et la manipulation de chaînes de caractères.
5. Des outils comme `jq` et `xmllint` aident à analyser et à manipuler les formats de données structurées comme JSON et XML.

### Exercice Pratique :
1. Écrivez un script qui analyse un fichier CSV, calcule le total d'une colonne spécifique et affiche le résultat.
2. Utilisez `awk` pour générer un rapport résumant le nombre d'occurrences de chaque mot dans un fichier journal.
3. Compressez un répertoire dans une archive `.tar.gz` et extrayez-le vers un emplacement différent.
4. Créez une commande `sed` pour rechercher et remplacer toutes les occurrences de "foo" par "bar" dans un fichier texte.
5. Écrivez un script bash qui traite un grand fichier journal et extrait toutes les adresses IP uniques.
