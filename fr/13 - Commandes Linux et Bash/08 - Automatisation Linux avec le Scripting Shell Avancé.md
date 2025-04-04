
# Automatisation Linux avec le Scripting Shell Avancé

Ce cours se concentre sur l'automatisation de tâches complexes à l'aide de techniques avancées de scripting shell. Apprenez à rationaliser la configuration des serveurs, la surveillance du système, les sauvegardes et plus encore à l'aide de scripts Bash, et intégrez-les à d'autres outils pour une efficacité maximale.

## Table des Matières
1. [Introduction à l'Automatisation par Script Shell](#introduction-a-lautomatisation-par-script-shell)
2. [Écrire des Scripts Modulaires et Réutilisables](#ecrire-des-scripts-modulaires-et-reutilisables)
3. [Automatisation de la Configuration et de l'Installation des Serveurs](#automatisation-de-la-configuration-et-de-linstallation-des-serveurs)
4. [Gestion des Sauvegardes de Fichiers et de Répertoires dans les Scripts](#gestion-des-sauvegardes-de-fichiers-et-de-repertoires-dans-les-scripts)
5. [Intégration de Bash avec d'Autres Langages de Scripting](#integration-de-bash-avec-dautres-langages-de-scripting)
6. [Création et Utilisation de Bibliothèques Bash](#creation-et-utilisation-de-bibliotheques-bash)
7. [Utilisation de Crontab pour l'Automatisation Planifiée](#utilisation-de-crontab-pour-lautomatisation-planifiee)
8. [Automatisation des Sauvegardes et de la Maintenance des Bases de Données](#automatisation-des-sauvegardes-et-de-la-maintenance-des-bases-de-donnees)
9. [Écrire des Scripts Complexes pour la Surveillance Système et les Alertes](#ecrire-des-scripts-complexes-pour-la-surveillance-systeme-et-les-alertes)
10. [Intégration du Contrôle de Version dans les Scripts Bash](#integration-du-controle-de-version-dans-les-scripts-bash)

## 1. Introduction à l'Automatisation par Script Shell
- **Définition**: Le scripting shell permet l'automatisation de tâches répétitives, ce qui améliore l'efficacité et la fiabilité de l'administration système.
- **Exemple**:
  - **Basic Script Example**:
    ```bash
    #!/bin/bash
    echo "Automating tasks with Bash scripts!"
    ```
- **Explication**: Le scripting shell peut automatiser des tâches telles que la manipulation de fichiers, la surveillance du système et la gestion des services en exécutant automatiquement des commandes.

## 2. Écrire des Scripts Modulaires et Réutilisables
- **Définition**: Les scripts modulaires sont divisés en fonctions réutilisables, ce qui les rend plus faciles à maintenir et à faire évoluer.
- **Exemple**:
  - **Function Example**:
    ```bash
    function backup() {
      cp $1 $2
      echo "Backup of $1 completed to $2"
    }
    backup /home/user/data /backup
    ```
- **Explication**: En définissant des fonctions réutilisables comme `backup()`, les scripts deviennent plus faciles à gérer et à étendre.

## 3. Automatisation de la Configuration et de l'Installation des Serveurs
- **Définition**: Les scripts d'automatisation peuvent rationaliser la configuration des serveurs, assurant la cohérence et réduisant les risques d'erreurs manuelles.
- **Exemple**:
  - **Automate Package Installation**:
    ```bash
    #!/bin/bash
    apt update && apt install -y nginx vim
    systemctl start nginx
    ```
- **Explication**: Ce script installe les paquets nécessaires et démarre un service automatiquement lors du provisionnement du serveur.

## 4. Gestion des Sauvegardes de Fichiers et de Répertoires dans les Scripts
- **Définition**: Les scripts de sauvegarde aident à automatiser le processus de création de sauvegardes de fichiers et de répertoires, assurant la sécurité des données.
- **Exemple**:
  - **Simple Backup Script**:
    ```bash
    #!/bin/bash
    tar -czf /backup/$(date +\%F).tar.gz /home/user/data
    ```
- **Explication**: Le script crée une sauvegarde horodatée du répertoire `/home/user/data` en utilisant `tar` pour la compression.

## 5. Intégration de Bash avec d'Autres Langages de Scripting (Python, Perl)
- **Définition**: L'intégration de Bash avec des langages comme Python ou Perl vous permet de tirer parti des forces des deux : Bash pour les tâches système et Python/Perl pour une logique plus complexe.
- **Exemple**:
  - **Call Python Script from Bash**:
    ```bash
    #!/bin/bash
    python3 myscript.py
    ```
  - **Call Bash from Python**:
    ```python
    import subprocess
    subprocess.run(["bash", "myscript.sh"])
    ```
- **Explication**: Bash peut invoquer des scripts Python ou Perl pour effectuer des opérations avancées qui ne sont pas réalisables en pur scripting shell.

## 6. Création et Utilisation de Bibliothèques Bash
- **Définition**: Les bibliothèques Bash consistent en une collection de fonctions et d'utilitaires qui peuvent être réutilisés dans différents scripts.
- **Exemple**:
  - **Create Library File (`lib.sh`)**:
    ```bash
    #!/bin/bash
    function print_date() {
      echo "Today's date: $(date)"
    }
    ```
  - **Include Library in Script**:
    ```bash
    #!/bin/bash
    source lib.sh
    print_date
    ```
- **Explication**: Les bibliothèques permettent la réutilisation du code et la modularité. La commande `source` est utilisée pour inclure des scripts externes.

## 7. Utilisation de Crontab pour l'Automatisation Planifiée
- **Définition**: `cron` est utilisé pour planifier l'exécution automatique de tâches à des intervalles spécifiés, ce qui est essentiel pour la maintenance et la surveillance régulières.
- **Exemple**:
  - **Schedule Backup with Crontab**:
    ```bash
    crontab -e
    # Add the following line to run a backup script every day at 2 AM
    0 2 * * * /home/user/backup.sh
    ```
- **Explication**: Ceci configure une tâche planifiée pour exécuter automatiquement le script de sauvegarde tous les jours à 2 heures du matin.

## 8. Automatisation des Sauvegardes et de la Maintenance des Bases de Données
- **Définition**: L'automatisation des sauvegardes de bases de données garantit que les données sont sauvegardées régulièrement sans intervention humaine.
- **Exemple**:
  - **Automate MySQL Backup**:
    ```bash
    #!/bin/bash
    mysqldump -u user -p password dbname > /backup/dbname_$(date +\%F).sql
    ```
- **Explication**: Ce script sauvegarde la base de données MySQL dans un fichier `.sql`, avec la date ajoutée au nom de fichier pour l'unicité.

## 9. Écrire des Scripts Complexes pour la Surveillance Système et les Alertes
- **Définition**: Des scripts complexes peuvent surveiller la santé du système (CPU, mémoire, disque, etc.) et envoyer des alertes en fonction de conditions.
- **Exemple**:
  - **Monitor Disk Usage**:
    ```bash
    #!/bin/bash
    disk_usage=$(df / | grep / | awk '{ print $5 }' | sed 's/%//g')
    if [ $disk_usage -gt 90 ]; then
      echo "Warning: Disk usage is above 90%" | mail -s "Disk Alert" admin@example.com
    fi
    ```
- **Explication**: Ce script vérifie l'utilisation du disque et envoie une alerte par e-mail si elle dépasse 90 %.

## 10. Intégration du Contrôle de Version dans les Scripts Bash (Git)
- **Définition**: L'intégration de Git avec les scripts Bash permet de maintenir le contrôle de version pour les scripts d'automatisation, facilitant les restaurations et la collaboration.
- **Exemple**:
  - **Add and Commit Changes to Git**:
    ```bash
    git add myscript.sh
    git commit -m "Updated backup script"
    git push origin main
    ```
- **Explication**: En utilisant Git, vous pouvez suivre les modifications apportées à vos scripts, collaborer avec d'autres et vous assurer que l'historique des versions est conservé.

## Conclusion

### Points Clés à Retenir :
1. Les scripts shell peuvent automatiser les tâches répétitives, ce qui permet de gagner du temps et de réduire les erreurs humaines.
2. L'écriture de scripts modulaires améliore la maintenabilité et l'évolutivité du code.
3. Des outils comme `cron` peuvent planifier des tâches pour une exécution régulière, automatisant ainsi la maintenance du système.
4. L'intégration de Bash avec d'autres langages de script comme Python ou Perl étend vos capacités d'automatisation.
5. Le contrôle de version, via Git, aide à suivre les modifications apportées aux scripts d'automatisation et à collaborer efficacement.

### Exercice Pratique :
1. Écrivez un script pour automatiser l'installation d'un paquet logiciel et de ses dépendances.
2. Créez un script de sauvegarde qui s'exécute quotidiennement à une heure précise et stocke les sauvegardes avec des noms de fichiers horodatés.
3. Automatisez la surveillance de la santé du système (CPU, mémoire, disque) et envoyez des alertes par e-mail en cas de conditions anormales.
4. Développez un script Bash qui s'intègre à un script Python pour des tâches de traitement de données avancées.
5. Contrôlez les versions de vos scripts d'automatisation en les poussant vers un dépôt Git et en gérant les mises à jour des scripts.
