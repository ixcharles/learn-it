
# Maîtriser l'Administration et l'Optimisation des Systèmes Linux

Ce cours couvre les compétences essentielles pour l'administration avancée des systèmes Linux, y compris le réglage des performances, les services système, la gestion des disques, le contrôle des ressources, la haute disponibilité et la mise à l'échelle avec la virtualisation et l'automatisation.

## Table des Matières
1. [Comprendre et Configurer les Services Système](#comprendre-et-configurer-les-services-systeme)
2. [Réglage des Performances pour le CPU, la Mémoire et le Disque](#reglage-des-performances-pour-le-cpu-la-memoire-et-le-disque)
3. [Gestion des Systèmes de Fichiers et des Disques](#gestion-des-systemes-de-fichiers-et-des-disques)
4. [Journalisation Système et Rotation des Logs](#journalisation-systeme-et-rotation-des-logs)
5. [Configuration et Compilation du Noyau](#configuration-et-compilation-du-noyau)
6. [Gestion et Contrôle des Ressources](#gestion-et-controle-des-ressources)
7. [Haute Disponibilité et Équilibrage de Charge sous Linux](#haute-disponibilite-et-equilibrage-de-charge-sous-linux)
8. [Stratégies de Sauvegarde et Planification de la Reprise Après Sinistre](#strategies-de-sauvegarde-et-planification-de-la-reprise-apres-sinistre)
9. [Mise à l'Échelle et Virtualisation](#mise-a-lechelle-et-virtualisation)
10. [Intégration et Déploiement Continus sous Linux](#integration-et-deploiement-continus-sous-linux)

## 1. Comprendre et Configurer les Services Système
- **Définition**: `systemd` gère les services, les processus de démarrage et les états du système dans les distributions Linux modernes.
- **Exemple**:
  - Activer et démarrer un service :
    ```bash
    sudo systemctl enable nginx
    sudo systemctl start nginx
    ```
- **Explication**: `systemctl` contrôle les services système, assurant un démarrage automatique et un fonctionnement correct.

## 2. Réglage des Performances pour le CPU, la Mémoire et le Disque
- **Définition**: L'optimisation de la planification du CPU, de la gestion de la mémoire et des E/S disque améliore les performances du système.
- **Exemple**:
  - Ajuster le gouverneur CPU pour la performance :
    ```bash
    echo "performance" | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    ```
- **Explication**: Ceci force le CPU à fonctionner à sa vitesse maximale pour des performances améliorées.

## 3. Gestion des Systèmes de Fichiers et des Disques
- **Définition**: Gérer le stockage efficacement à l'aide de RAID, LVM et de différents systèmes de fichiers optimise les performances et la fiabilité des disques.
- **Exemple**:
  - Créer et monter une partition LVM :
    ```bash
    sudo pvcreate /dev/sdb
    sudo vgcreate my_vg /dev/sdb
    sudo lvcreate -L 10G -n my_lv my_vg
    sudo mkfs.ext4 /dev/my_vg/my_lv
    ```
- **Explication**: Logical Volume Management (LVM) permet une allocation et un redimensionnement flexibles des disques.

## 4. Journalisation Système et Rotation des Logs
- **Définition**: Les outils de gestion des logs (`journald`, `logrotate`) aident à surveiller l'activité du système et à empêcher une croissance excessive des fichiers de logs.
- **Exemple**:
  - Afficher les logs récents :
    ```bash
    journalctl -xe
    ```
  - Configurer la rotation des logs :
    ```bash
    sudo nano /etc/logrotate.d/nginx
    ```
- **Explication**: `journalctl` affiche les logs du système, tandis que `logrotate` empêche les logs de consommer trop d'espace.

## 5. Configuration et Compilation du Noyau
- **Définition**: La personnalisation du noyau Linux permet des améliorations de performances et des optimisations matérielles.
- **Exemple**:
  - Télécharger, configurer et compiler un nouveau noyau :
    ```bash
    wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.5.tar.xz
    tar -xf linux-6.5.tar.xz
    cd linux-6.5
    make menuconfig
    make -j$(nproc)
    sudo make modules_install && sudo make install
    ```
- **Explication**: Ce processus compile un noyau personnalisé pour un contrôle amélioré sur les performances et les fonctionnalités du système.

## 6. Gestion et Contrôle des Ressources
- **Définition**: `cgroups` et `systemd` permettent un contrôle précis du CPU, de la mémoire et des E/S disque par processus.
- **Exemple**:
  - Limiter l'utilisation du CPU d'un processus :
    ```bash
    sudo cgcreate -g cpu:/limited
    echo 50000 | sudo tee /sys/fs/cgroup/cpu/limited/cpu.cfs_quota_us
    sudo cgexec -g cpu:limited /usr/bin/my_program
    ```
- **Explication**: `cgroups` peut restreindre l'utilisation du CPU, de la mémoire et des E/S pour éviter la surcharge du système.

## 7. Haute Disponibilité et Équilibrage de Charge sous Linux
- **Définition**: Des techniques telles que le clustering et l'équilibrage de charge améliorent la disponibilité et distribuent efficacement les charges de travail.
- **Exemple**:
  - Configurer HAProxy comme équilibreur de charge :
    ```bash
    sudo apt install haproxy
    sudo nano /etc/haproxy/haproxy.cfg
    ```
- **Explication**: HAProxy distribue uniformément le trafic sur plusieurs serveurs pour une disponibilité améliorée.

## 8. Stratégies de Sauvegarde et Planification de la Reprise Après Sinistre
- **Définition**: La mise en œuvre de sauvegardes régulières et d'une reprise après sinistre assure une perte de données minimale.
- **Exemple**:
  - Automatiser les sauvegardes incrémentielles :
    ```bash
    rsync -av --delete /home /backup/home
    ```
- **Explication**: `rsync` sauvegarde efficacement les fichiers tout en conservant les permissions et les horodatages.

## 9. Mise à l'Échelle et Virtualisation
- **Définition**: La virtualisation et la conteneurisation (Docker, LXC, KVM) permettent une utilisation efficace des ressources et une mise à l'échelle.
- **Exemple**:
  - Lancer un conteneur Docker :
    ```bash
    docker run -d --name webserver -p 80:80 nginx
    ```
- **Explication**: Les conteneurs permettent un déploiement léger et rapide des applications.

## 10. Intégration et Déploiement Continus sous Linux
- **Définition**: Les pipelines CI/CD automatisent les tests et le déploiement de logiciels.
- **Exemple**:
  - Automatiser le déploiement avec GitHub Actions :
    ```yaml
    name: Deploy
    on: push
    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2
          - run: ./deploy.sh
    ```
- **Explication**: Ceci assure des déploiements fluides et automatisés à chaque modification de code.

## Conclusion

### Points Clés à Retenir :
1. `systemd` simplifie la gestion des services, améliorant le démarrage et la fiabilité.
2. Le réglage des performances optimise les performances du CPU, de la mémoire et du disque.
3. `LVM` et RAID offrent une gestion du stockage flexible.
4. La rotation des logs empêche une utilisation excessive du disque et aide à maintenir les performances du système.
5. `cgroups` et les outils de haute disponibilité assurent un contrôle efficace des ressources.
6. La virtualisation et CI/CD rationalisent la mise à l'échelle et le déploiement.

### Exercice Pratique :
1. Configurez un service système à l'aide de `systemctl` et assurez-vous qu'il démarre au démarrage.
2. Optimisez les performances du CPU et de la mémoire à l'aide des paramètres `sysctl`.
3. Configurez et montez un volume de stockage basé sur LVM.
4. Mettez en œuvre la rotation des logs pour un service spécifique.
5. Déployez une application web simple à l'aide de Docker et automatisez son déploiement avec un pipeline CI/CD.
