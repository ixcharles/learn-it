
# Administration Système Linux via la Ligne de Commande

Ce cours couvre les tâches essentielles d'administration système Linux via la ligne de commande, vous permettant de gérer les utilisateurs, les processus, le stockage, la mise en réseau et plus encore. En maîtrisant ces commandes, vous serez en mesure d'effectuer efficacement la maintenance et le dépannage courants du système.

## Table des Matières
1. [Gestion des Utilisateurs et des Groupes](#gestion-des-utilisateurs-et-des-groupes)
2. [Processus Système et Gestion des Processus](#processus-systeme-et-gestion-des-processus)
3. [Surveillance de la Mémoire et des Ressources](#surveillance-de-la-memoire-et-des-ressources)
4. [Fichiers Journaux Système et Surveillance](#fichiers-journaux-systeme-et-surveillance)
5. [Gestion des Disques et du Système de Fichiers](#gestion-des-disques-et-du-systeme-de-fichiers)
6. [Gestion des Paquets et Installation de Logiciels](#gestion-des-paquets-et-installation-de-logiciels)
7. [Commandes et Outils de Mise en Réseau](#commandes-et-outils-de-mise-en-reseau)
8. [Gestion des Règles de Pare-feu avec iptables](#gestion-des-regles-de-pare-feu-avec-iptables)
9. [Arrêt, Redémarrage et Gestion de l'Alimentation du Système](#arret-redemarrage-et-gestion-de-lalimentation-du-systeme)
10. [Travailler avec les Services Systemd et les Fichiers d'Unité](#travailler-avec-les-services-systemd-et-les-fichiers-dunite)

## 1. Gestion des Utilisateurs et des Groupes
- **Définition**: Linux fournit des commandes pour gérer les utilisateurs et les groupes, permettant la configuration du contrôle d'accès et des permissions.
- **Exemple**:
  - **Create User**:
    ```bash
    useradd newuser
    passwd newuser
    ```
  - **Create Group**:
    ```bash
    groupadd newgroup
    ```
- **Explication**: `useradd` crée un nouvel utilisateur, `passwd` définit le mot de passe et `groupadd` crée un nouveau groupe.

## 2. Processus Système et Gestion des Processus
- **Définition**: Les processus représentent les programmes en cours d'exécution, et Linux fournit des outils pour gérer leur état, leur priorité et leur terminaison.
- **Exemple**:
  - **View Processes**:
    ```bash
    ps aux
    ```
  - **Kill Process**:
    ```bash
    kill -9 PID
    ```
  - **Set Process Priority**:
    ```bash
    nice -n 10 command
    ```
- **Explication**: `ps` affiche les processus, `kill` termine les processus par leur PID et `nice` ajuste la priorité des processus.

## 3. Surveillance de la Mémoire et des Ressources
- **Définition**: La surveillance de la mémoire et des ressources système est cruciale pour diagnostiquer les problèmes de performance.
- **Exemple**:
  - **Free Memory**:
    ```bash
    free -h
    ```
  - **Disk Usage**:
    ```bash
    df -h
    ```
  - **Disk Space Usage**:
    ```bash
    du -sh /path/to/dir
    ```
- **Explication**: `free` affiche l'utilisation de la mémoire, `df` affiche l'utilisation de l'espace disque et `du` affiche l'utilisation du disque d'un répertoire spécifique.

## 4. Fichiers Journaux Système et Surveillance
- **Définition**: Les journaux système enregistrent un historique des événements et des erreurs, utiles pour le débogage et les vérifications de l'état du système.
- **Exemple**:
  - **View System Logs**:
    ```bash
    tail -f /var/log/syslog
    ```
  - **Journal Logs**:
    ```bash
    journalctl
    ```
- **Explication**: `tail -f` affiche les journaux les plus récents, et `journalctl` est utilisé pour accéder aux journaux gérés par `systemd`.

## 5. Gestion des Disques et du Système de Fichiers
- **Définition**: La gestion des disques et du système de fichiers implique le partitionnement, le formatage et le montage des périphériques de stockage.
- **Exemple**:
  - **Create Partition**:
    ```bash
    fdisk /dev/sda
    ```
  - **Format Disk**:
    ```bash
    mkfs.ext4 /dev/sdb1
    ```
  - **Mount Disk**:
    ```bash
    mount /dev/sdb1 /mnt
    ```
- **Explication**: `fdisk` partitionne un disque, `mkfs` le formate et `mount` attache le système de fichiers à un répertoire.

## 6. Gestion des Paquets et Installation de Logiciels
- **Définition**: Les distributions Linux gèrent les paquets logiciels à l'aide de gestionnaires de paquets comme `apt` (basé sur Debian) et `yum` (basé sur RHEL).
- **Exemple**:
  - **Install Package** (APT):
    ```bash
    sudo apt update
    sudo apt install package_name
    ```
  - **Install Package** (YUM):
    ```bash
    sudo yum install package_name
    ```
  - **Remove Package**:
    ```bash
    sudo apt remove package_name
    ```
- **Explication**: `apt` et `yum` permettent d'installer et de supprimer des paquets logiciels sur différentes distributions.

## 7. Commandes et Outils de Mise en Réseau
- **Définition**: Les commandes de mise en réseau aident à configurer les interfaces réseau, à vérifier la connectivité et à dépanner.
- **Exemple**:
  - **View Network Configuration**:
    ```bash
    ifconfig
    ```
  - **Check Network Status**:
    ```bash
    ip a
    ```
  - **Ping Host**:
    ```bash
    ping google.com
    ```
  - **Download File**:
    ```bash
    wget https://example.com/file
    ```
- **Explication**: `ifconfig` affiche les interfaces réseau, `ping` vérifie la connectivité et `wget` télécharge des fichiers depuis le web.

## 8. Gestion des Règles de Pare-feu avec iptables
- **Définition**: `iptables` est utilisé pour configurer et gérer les règles de pare-feu afin de sécuriser le système contre le trafic indésirable.
- **Exemple**:
  - **List Rules**:
    ```bash
    sudo iptables -L
    ```
  - **Allow Incoming SSH**:
    ```bash
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    ```
- **Explication**: `iptables` aide à configurer les règles de pare-feu pour la sécurité du réseau. Utilisez `-A` pour ajouter des règles et `-L` pour les lister.

## 9. Arrêt, Redémarrage et Gestion de l'Alimentation du Système
- **Définition**: Linux fournit des commandes pour arrêter, redémarrer et gérer les paramètres d'alimentation en toute sécurité.
- **Exemple**:
  - **Shutdown**:
    ```bash
    sudo shutdown now
    ```
  - **Reboot**:
    ```bash
    sudo reboot
    ```
  - **Power Off**:
    ```bash
    sudo poweroff
    ```
- **Explication**: `shutdown`, `reboot` et `poweroff` gèrent l'alimentation du système et les transitions d'état.

## 10. Travailler avec les Services Systemd et les Fichiers d'Unité
- **Définition**: `systemd` est le gestionnaire de services par défaut sur de nombreuses distributions Linux, utilisé pour gérer les services et les fichiers d'unité systemd.
- **Exemple**:
  - **Start Service**:
    ```bash
    sudo systemctl start service_name
    ```
  - **Enable Service**:
    ```bash
    sudo systemctl enable service_name
    ```
  - **Check Service Status**:
    ```bash
    sudo systemctl status service_name
    ```
- **Explication**: `systemctl` est l'outil en ligne de commande utilisé pour interagir avec les services `systemd`.

## Conclusion

### Points Clés à Retenir :
1. La gestion des utilisateurs et des groupes assure un contrôle d'accès et une sécurité appropriés.
2. La compréhension des outils de gestion et de surveillance des processus est vitale pour le dépannage des performances du système.
3. Les outils de gestion des disques et du système de fichiers permettent une organisation et une maintenance efficaces du stockage.
4. La gestion des paquets aide à automatiser l'installation, la mise à jour et la suppression de logiciels sous Linux.
5. Les outils réseau et la configuration du pare-feu garantissent une communication sécurisée et fiable entre les systèmes.

### Exercice Pratique :
1. Écrivez un script qui ajoute un nouvel utilisateur, crée un groupe et affecte l'utilisateur au groupe.
2. Utilisez `top` ou `htop` pour surveiller les ressources système, puis terminez un processus gourmand en ressources.
3. Configurez une tâche cron qui vérifie automatiquement l'utilisation du disque et envoie un e-mail si l'utilisation dépasse un certain seuil.
4. Créez une règle de pare-feu à l'aide de `iptables` qui bloque tout le trafic entrant à l'exception de SSH.
