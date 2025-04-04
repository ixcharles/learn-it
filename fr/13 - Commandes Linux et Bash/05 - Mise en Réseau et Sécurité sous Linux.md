
# Mise en Réseau et Sécurité sous Linux

Ce cours se concentre sur les pratiques essentielles de mise en réseau et de sécurité sous Linux. Apprenez à configurer les réseaux, à sécuriser les communications, à dépanner les problèmes de réseau et à protéger votre système contre les menaces externes. Ces compétences sont fondamentales pour la gestion de systèmes Linux sécurisés et fiables.

## Table des Matières
1. [Concepts de Base de la Mise en Réseau et Configuration sous Linux](#concepts-de-base-de-la-mise-en-reseau-et-configuration-sous-linux)
2. [SSH et Connectivité à Distance](#ssh-et-connectivite-a-distance)
3. [Diagnostic et Dépannage Réseau](#diagnostic-et-depannage-reseau)
4. [Travailler avec iptables pour la Sécurité](#travailler-avec-iptables-pour-la-securite)
5. [Sécurisation des Serveurs Linux : Meilleures Pratiques](#securisation-des-serveurs-linux-meilleures-pratiques)
6. [Configuration et Gestion des Pare-feu](#configuration-et-gestion-des-pare-feu)
7. [Mise en Place de VPN et de Tunnels Sécurisés](#mise-en-place-de-vpns-et-de-tunnels-securises)
8. [Sécurisation des Transferts de Fichiers](#securisation-des-transferts-de-fichiers)
9. [Outils Réseau Linux pour le Dépannage](#outils-reseau-linux-pour-le-depannage)
10. [Authentification des Utilisateurs et Gestion des Mots de Passe](#authentification-des-utilisateurs-et-gestion-des-mots-de-passe)

## 1. Concepts de Base de la Mise en Réseau et Configuration sous Linux
- **Définition**: La mise en réseau sous Linux implique la configuration des interfaces, de l'adressage IP et du routage pour permettre la communication entre les systèmes.
- **Exemple**:
  - **View Network Configuration**:
    ```bash
    ip a
    ```
  - **Set Static IP**:
    Modifiez `/etc/network/interfaces` ou utilisez `nmcli` pour les systèmes contrôlés par NetworkManager.
- **Explication**: La commande `ip` permet d'afficher les interfaces réseau et leurs paramètres. La configuration d'une IP statique se fait via les fichiers d'interface réseau.

## 2. SSH et Connectivité à Distance
- **Définition**: SSH permet une connexion à distance sécurisée aux systèmes, tandis que SCP et SFTP permettent des transferts de fichiers sécurisés.
- **Exemple**:
  - **SSH Login**:
    ```bash
    ssh username@hostname
    ```
  - **SCP (Secure Copy)**:
    ```bash
    scp localfile user@hostname:/remote/path
    ```
  - **SFTP**:
    ```bash
    sftp username@hostname
    ```
- **Explication**: SSH chiffre la connexion pour un accès à distance sécurisé, tandis que SCP et SFTP sont utilisés pour les transferts de fichiers sécurisés.

## 3. Diagnostic et Dépannage Réseau
- **Définition**: Les outils de dépannage réseau aident à identifier les problèmes de connectivité et à diagnostiquer les performances du réseau.
- **Exemple**:
  - **Ping**:
    ```bash
    ping google.com
    ```
  - **Traceroute**:
    ```bash
    traceroute google.com
    ```
  - **Netcat**:
    ```bash
    nc -v -z 192.168.1.1 1-1000
    ```
- **Explication**: `ping` vérifie la connectivité, `traceroute` trace le chemin réseau et `netcat` teste les ports pour la disponibilité des services.

## 4. Travailler avec iptables pour la Sécurité
- **Définition**: `iptables` est utilisé pour configurer, gérer et maintenir les règles de pare-feu pour la sécurisation des systèmes Linux.
- **Exemple**:
  - **List Current Rules**:
    ```bash
    sudo iptables -L
    ```
  - **Allow Incoming SSH**:
    ```bash
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    ```
  - **Block All Incoming Traffic Except SSH**:
    ```bash
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    sudo iptables -A INPUT -j DROP
    ```
- **Explication**: `iptables` peut être utilisé pour filtrer le trafic réseau en fonction des règles définies par l'administrateur système.

## 5. Sécurisation des Serveurs Linux : Meilleures Pratiques
- **Définition**: La sécurisation d'un serveur Linux implique le renforcement du système pour empêcher les accès et les attaques non autorisés.
- **Exemple**:
  - **Disable Root Login**:
    Modifiez `/etc/ssh/sshd_config` et définissez `PermitRootLogin no`.
  - **Install Fail2Ban**:
    ```bash
    sudo apt install fail2ban
    ```
- **Explication**: Les meilleures pratiques incluent la désactivation de la connexion root, l'utilisation de pare-feu et l'installation d'outils de prévention des intrusions comme Fail2Ban.

## 6. Configuration et Gestion des Pare-feu
- **Définition**: Linux offre des outils comme `ufw` et `firewall-cmd` pour la gestion des pare-feu.
- **Exemple**:
  - **Using UFW**:
    ```bash
    sudo ufw allow ssh
    sudo ufw enable
    ```
  - **Using firewall-cmd** (Firewalld):
    ```bash
    sudo firewall-cmd --zone=public --add-service=http --permanent
    sudo firewall-cmd --reload
    ```
- **Explication**: `ufw` et `firewall-cmd` fournissent des interfaces conviviales pour gérer les règles de pare-feu.

## 7. Mise en Place de VPN et de Tunnels Sécurisés
- **Définition**: Un VPN chiffre le trafic réseau, et les tunnels sécurisés offrent confidentialité et sécurité pour la communication à distance.
- **Exemple**:
  - **Set up OpenVPN**:
    ```bash
    sudo apt install openvpn
    sudo openvpn --config /path/to/config.ovpn
    ```
  - **SSH Tunnel**:
    ```bash
    ssh -L 8080:localhost:80 user@remote_host
    ```
- **Explication**: OpenVPN et les tunnels SSH créent des connexions sécurisées entre les clients et les serveurs, souvent utilisées pour le travail à distance ou pour contourner les restrictions géographiques.

## 8. Sécurisation des Transferts de Fichiers
- **Définition**: La sécurisation des transferts de fichiers garantit la confidentialité et l'intégrité lors de la transmission des données.
- **Exemple**:
  - **Using Rsync**:
    ```bash
    rsync -avz /local/dir user@hostname:/remote/dir
    ```
  - **Using SSH Keys**:
    Générez et copiez les clés SSH pour une connexion sans mot de passe :
    ```bash
    ssh-keygen
    ssh-copy-id user@hostname
    ```
  - **Encrypt Files with GPG**:
    ```bash
    gpg -c filename
    ```
- **Explication**: `rsync` est un outil puissant pour le transfert de fichiers, tandis que GPG fournit un chiffrement pour une sécurité accrue.

## 9. Outils Réseau Linux pour le Dépannage
- **Définition**: Des outils comme `tcpdump` et `Wireshark` sont utilisés pour capturer et analyser le trafic réseau, aidant ainsi à diagnostiquer les problèmes.
- **Exemple**:
  - **Using tcpdump**:
    ```bash
    sudo tcpdump -i eth0
    ```
  - **Using Wireshark**: Démarrez Wireshark et sélectionnez l'interface réseau pour capturer les paquets.
- **Explication**: Ces outils sont utilisés pour capturer, analyser et filtrer le trafic réseau, ce qui est crucial pour le dépannage des problèmes de réseau.

## 10. Authentification des Utilisateurs et Gestion des Mots de Passe
- **Définition**: Linux fournit des mécanismes pour gérer l'authentification des utilisateurs et les politiques de mots de passe afin de garantir un accès sécurisé.
- **Exemple**:
  - **Change Password**:
    ```bash
    passwd username
    ```
  - **Set Password Expiry**:
    ```bash
    chage -M 30 username
    ```
  - **Configure PAM (Pluggable Authentication Modules)**:
    Modifiez `/etc/pam.d/common-password` pour appliquer des politiques de mots de passe plus strictes.
- **Explication**: Des outils comme `passwd`, `chage` et PAM garantissent que les informations d'identification des utilisateurs sont gérées de manière sécurisée et que les politiques de mots de passe sont appliquées.

## Conclusion

### Points Clés à Retenir :
1. Les outils de mise en réseau tels que `ping`, `traceroute` et `netcat` aident à diagnostiquer et à dépanner les problèmes de connectivité.
2. SSH, SCP et SFTP offrent des capacités d'accès à distance et de transfert de fichiers sécurisées.
3. Les pare-feu et les VPN sont essentiels pour sécuriser les serveurs Linux et assurer une communication sûre.
4. La sécurisation des transferts de fichiers avec `rsync` et les outils de chiffrement comme GPG améliore la protection des données.
5. Une gestion efficace des utilisateurs et des politiques de mots de passe est vitale pour maintenir la sécurité du système.

### Exercice Pratique :
1. Configurez une connexion VPN sur un serveur Linux à l'aide d'OpenVPN et testez la connexion sécurisée.
2. Configurez `ufw` pour autoriser le trafic HTTP et SSH tout en refusant toutes les autres connexions entrantes.
3. Configurez une connexion SSH sécurisée basée sur des clés et désactivez l'authentification par mot de passe pour SSH.
4. Utilisez `tcpdump` pour capturer le trafic réseau et analysez les paquets à l'aide de Wireshark pour une interface réseau spécifique.
