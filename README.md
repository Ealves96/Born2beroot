<!-- Banner -->
<p align="center">
  <img src="https://img.shields.io/badge/Born2beRoot-42-blueviolet?style=for-the-badge&logo=linux" alt="Born2beRoot"/>
</p>

# 🚀 Born2beroot

## 📝 Introduction
Born2beroot est un projet d’initiation à l’administration système et à la virtualisation, proposé par l’école 42. L’objectif est de créer une machine virtuelle Debian, sécurisée et configurée selon des règles strictes, sans interface graphique, en utilisant VirtualBox (ou UTM).

## 🛠️ Outils utilisés
<p>
  <img src="https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white" alt="VirtualBox"/>
  <img src="https://img.shields.io/badge/Debian-A81D33?style=for-the-badge&logo=debian&logoColor=white" alt="Debian"/>
  <img src="https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white" alt="Bash"/>
  <img src="https://img.shields.io/badge/UFW-222222?style=for-the-badge&logo=ubuntu&logoColor=white" alt="UFW"/>
  <img src="https://img.shields.io/badge/AppArmor-5E5E5E?style=for-the-badge&logo=linux&logoColor=white" alt="AppArmor"/>
  <img src="https://img.shields.io/badge/Cron-6A5ACD?style=for-the-badge&logo=linux&logoColor=white" alt="Cron"/>
  <img src="https://img.shields.io/badge/SSH-2C2C2C?style=for-the-badge&logo=openssh&logoColor=white" alt="SSH"/>
</p>

## 📦 Prérequis
- VirtualBox (ou UTM si VirtualBox ne fonctionne pas)
- Image ISO de Debian (version stable, pas de testing/unstable)
- Connaissances de base en ligne de commande Linux

## 🖥️ Installation et partitionnement
1. **Créer une machine virtuelle** sous VirtualBox avec Debian stable (64 bits).
2. **Partitionnement** : Créez au moins 2 partitions chiffrées avec LVM. Exemple :
   - `/boot` (non chiffré, ~500 Mo)
   - Partition principale chiffrée (LVM) :
     - `/` (ex : 2 Go)
     - `swap` (ex : 1 Go)
     - `/home` (ex : 3,8 Go)

## ⚙️ Configuration système
- **Hostname** : doit être votre login suivi de 42 (ex : wil42)
- **Pas d’interface graphique** : n’installez pas X.org ou équivalent
- **AppArmor** : doit rester actif sur Debian
- **Service SSH** : actif sur le port 4242 uniquement, connexion root interdite
- **Pare-feu UFW** : actif au démarrage, seul le port 4242 doit être ouvert

## 👤 Utilisateurs et groupes
- Un utilisateur avec votre login (en plus de root)
- Groupes : user42 et sudo
- Savoir créer un nouvel utilisateur et lui assigner un groupe

## 🔒 Politique de mot de passe fort
- Expiration : tous les 30 jours
- Délai minimum avant changement : 2 jours
- Avertissement d’expiration : 7 jours avant
- Complexité : 10 caractères min., 1 majuscule, 1 minuscule, 1 chiffre, max 3 caractères identiques consécutifs, ne doit pas contenir le nom de l’utilisateur
- Pour tous sauf root : au moins 7 caractères différents de l’ancien mot de passe
- Tous les mots de passe (root inclus) doivent être changés après configuration

## 🛡️ Configuration stricte de sudo
- 3 essais maximum pour l’authentification
- Message personnalisé en cas d’échec
- Archivage des commandes (inputs/outputs) dans `/var/log/sudo/`
- Mode TTY activé
- Restriction des paths utilisables par sudo :
  `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`

## 📊 Script de monitoring
- Script `monitoring.sh` en bash
- Exécuté toutes les 10 minutes (via cron), écrit sur tous les terminaux (utiliser `wall`)
- Affiche :
  - Architecture et version du kernel
  - Nombre de CPU physiques et virtuels
  - RAM disponible et taux d’utilisation
  - Disque disponible et taux d’utilisation
  - Charge CPU
  - Date/heure du dernier boot
  - LVM actif ou non
  - Nombre de connexions actives
  - Nombre d’utilisateurs connectés
  - Adresse IPv4 et MAC
  - Nombre de commandes sudo exécutées

## 🧰 Exemples de commandes utiles
- Vérifier les partitions : `lsblk`
- Vérifier AppArmor : `sudo aa-status`
- Vérifier le port SSH : `ss -tnulp | grep 4242`
- Vérifier le pare-feu : `sudo ufw status`
- Vérifier la politique de mot de passe : `chage -l <user>`
- Vérifier sudo : `sudo -l`, consulter `/var/log/sudo/`

## 🎓 Conseils pour la soutenance
- Savoir expliquer chaque choix de configuration
- Savoir créer/modifier des utilisateurs et groupes
- Savoir modifier le hostname
- Savoir interrompre le script de monitoring via cron

## 📤 Rendu
- Uniquement le fichier `signature.txt` à la racine du dépôt (voir sujet pour la génération)

## 👨‍💻 Auteur
[Votre nom]

## 📄 Documentation du script de monitoring
Pour plus de détails sur le script `monitoring.sh`, consultez le document suivant :  
[Documentation détaillée du script sur Google Drive](https://drive.google.com/ton-lien-ici)

---
<p align="center">
  <img src="https://img.shields.io/badge/42-Network-blue?style=flat-square&logo=42&logoColor=white" alt="42"/>
  <img src="https://img.shields.io/badge/Linux-000000?style=flat-square&logo=linux&logoColor=white" alt="Linux"/>
  <img src="https://img.shields.io/badge/Virtualization-20C997?style=flat-square&logo=proxmox&logoColor=white" alt="Virtualization"/>
</p>
