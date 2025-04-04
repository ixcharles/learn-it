
# Dépannage et Récupération sous Linux

Ce cours couvre les techniques essentielles pour diagnostiquer, récupérer et dépanner les systèmes Linux. Apprenez à résoudre les échecs de démarrage, à récupérer les fichiers perdus, à réparer les systèmes de fichiers corrompus et à restaurer efficacement la fonctionnalité du système.

## Table des Matières
1. [Concepts de Base de la Récupération Système](#concepts-de-base-de-la-recuperation-systeme)
2. [Récupérer un Système de Fichiers Corrompu](#recuperer-un-systeme-de-fichiers-corrompu)
3. [Récupérer des Fichiers et des Répertoires Perdus](#recuperer-des-fichiers-et-des-repertoires-perdus)
4. [Résoudre les Problèmes de Gestion des Paquets](#resoudre-les-problemes-de-gestion-des-paquets)
5. [Résoudre les Problèmes de Démarrage](#resoudre-les-problemes-de-demarrage)
6. [Panique du Noyau et Dépannage du Démarrage](#panique-du-noyau-et-depannage-du-demarrage)
7. [Dépannage Réseau Avancé](#depannage-reseau-avance)
8. [Résoudre les Goulots d'Étranglement des Performances](#resoudre-les-goulots-detranglement-des-performances)
9. [Analyser les Vidages de Noyau et Déboguer les Applications](#analyser-les-vidages-de-noyau-et-deboguer-les-applications)
10. [Récupération Complète du Système et Stratégies de Sauvegarde](#recuperation-complete-du-systeme-et-strategies-de-sauvegarde)

## 1. Concepts de Base de la Récupération Système
- **Définition**: La récupération du système implique l'utilisation d'outils tels que les CD Live ou les modes de secours pour restaurer un système Linux endommagé ou incapable de démarrer.
- **Exemple**:
  - Boot into rescue mode:
    ```bash
    sudo systemctl rescue
    ```
- **Explication**: Le mode de secours permet d'accéder au système lorsque le démarrage normal échoue, ce qui permet le dépannage et la récupération.

## 2. Récupérer un Système de Fichiers Corrompu
- **Définition**: La corruption du système de fichiers peut survenir en raison de pannes de courant ou de problèmes matériels, nécessitant des outils comme `fsck`.
- **Exemple**:
  - Check and repair filesystem:
    ```bash
    sudo fsck -y /dev/sda1
    ```
- **Explication**: `fsck` analyse et corrige les erreurs sur un système de fichiers, évitant la perte de données.

## 3. Récupérer des Fichiers et des Répertoires Perdus
- **Définition**: Des outils comme `extundelete` et `TestDisk` aident à restaurer les fichiers supprimés accidentellement.
- **Exemple**:
  - Recover a deleted file from an ext4 partition:
    ```bash
    sudo extundelete /dev/sda1 --restore-all
    ```
- **Explication**: `extundelete` analyse un disque à la recherche de fichiers récemment supprimés et tente de les récupérer.

## 4. Résoudre les Problèmes de Gestion des Paquets
- **Définition**: Des installations de paquets corrompues ou cassées peuvent entraîner une instabilité du système et nécessitent une intervention manuelle.
- **Exemple**:
  - Fix broken packages in Debian-based systems:
    ```bash
    sudo dpkg --configure -a
    ```
- **Explication**: Cette commande tente de reconfigurer les paquets cassés, assurant ainsi le bon fonctionnement du système.

## 5. Résoudre les Problèmes de Démarrage
- **Définition**: Les problèmes avec le chargeur de démarrage (GRUB, LILO) peuvent empêcher Linux de démarrer.
- **Exemple**:
  - Reinstall GRUB:
    ```bash
    sudo grub-install /dev/sda
    sudo update-grub
    ```
- **Explication**: Ceci restaure le chargeur de démarrage GRUB, corrigeant les problèmes de démarrage causés par des erreurs de configuration ou une corruption.

## 6. Panique du Noyau et Dépannage du Démarrage
- **Définition**: Les paniques du noyau indiquent des défaillances système graves, souvent liées au matériel, aux pilotes ou aux configurations du noyau.
- **Exemple**:
  - View the last kernel panic logs:
    ```bash
    journalctl -k -b -1
    ```
- **Explication**: Les journaux du noyau aident à identifier la cause des plantages et à déterminer les actions correctives.

## 7. Dépannage Réseau Avancé
- **Définition**: Le diagnostic des problèmes de réseau implique la vérification des pare-feu, du DNS, du routage et de la connectivité.
- **Exemple**:
  - Check network interface details:
    ```bash
    ip a
    ```
- **Explication**: Cette commande liste les interfaces réseau et leur état, aidant à diagnostiquer les problèmes de connectivité.

## 8. Résoudre les Goulots d'Étranglement des Performances
- **Définition**: Une utilisation élevée des ressources peut ralentir un système, nécessitant une surveillance et une optimisation.
- **Exemple**:
  - Check CPU and memory usage:
    ```bash
    top
    ```
- **Explication**: `top` fournit une surveillance des processus en temps réel pour identifier les applications gourmandes en ressources.

## 9. Analyser les Vidages de Noyau et Déboguer les Applications
- **Définition**: Les vidages de noyau stockent l'état d'un programme au moment d'un plantage, ce qui facilite le débogage.
- **Exemple**:
  - Analyze a core dump using `gdb`:
    ```bash
    gdb /path/to/executable core
    ```
- **Explication**: `gdb` aide à déboguer les plantages d'applications en analysant la mémoire et les erreurs d'exécution.

## 10. Récupération Complète du Système et Stratégies de Sauvegarde
- **Définition**: Une stratégie de sauvegarde robuste garantit que les données peuvent être restaurées en cas de défaillance.
- **Exemple**:
  - Create a full system backup with `tar`:
    ```bash
    tar -cvpzf /backup/system.tar.gz --exclude=/backup /
    ```
- **Explication**: Cette commande crée une archive compressée de l'ensemble du système, à l'exclusion du répertoire de sauvegarde lui-même.

## Conclusion

### Points Clés à Retenir :
1. Les CD Live et les modes de secours permettent la récupération des systèmes incapables de démarrer.
2. Les vérifications du système de fichiers (`fsck`) et les outils de récupération (`extundelete`, `TestDisk`) aident à restaurer les données perdues ou corrompues.
3. La résolution des problèmes de gestion des paquets peut restaurer la fonctionnalité du système.
4. Le dépannage des problèmes de chargeur de démarrage est essentiel pour résoudre les échecs de démarrage.
5. Les vidages de noyau et les outils de débogage aident à analyser les plantages du système et des applications.

### Exercice Pratique :
1. Simulez un système de fichiers corrompu et tentez une récupération à l'aide de `fsck`.
2. Supprimez un fichier de test et utilisez `extundelete` ou `TestDisk` pour le restaurer.
3. Cassez et réparez GRUB en le réinstallant manuellement.
4. Utilisez `top` et `iotop` pour analyser les performances du système et identifier les goulots d'étranglement.
5. Générez un vidage de noyau et analysez-le à l'aide de `gdb`.
