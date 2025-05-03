<!-- Banner -->
<p align="center">
  # 🚀 Born2beroot
</p>

## 📝 Présentation rapide
Ce projet m’a permis de découvrir l’administration système sur Debian, en créant une VM sécurisée et minimaliste, sans interface graphique.

## 🖥️ Installation et partitionnement
J’ai installé Debian stable sur une machine virtuelle VirtualBox. J’ai configuré le partitionnement avec :
- Une partition `/boot` non chiffrée (~500 Mo)
- Le reste du disque chiffré via LVM, réparti en `/`, `swap` et `/home`

## 🔒 Sécurité et services
- J’ai activé et vérifié AppArmor pour renforcer la sécurité.
- J’ai configuré le service SSH pour n’écouter que sur le port 4242, en interdisant la connexion directe de root.
- J’ai mis en place le pare-feu UFW pour n’autoriser que le port 4242 au démarrage.

## 👤 Utilisateurs et politique de mot de passe
- J’ai créé un utilisateur personnel (en plus de root), membre des groupes `user42` et `sudo`.
- J’ai appliqué une politique de mot de passe forte : expiration à 30 jours, complexité, avertissement, etc.

## 🛡️ Sudo
- J’ai restreint sudo à 3 essais, ajouté un message personnalisé en cas d’échec, activé la journalisation des commandes dans `/var/log/sudo/`, forcé le mode TTY et limité les chemins autorisés.

## 📊 Monitoring
- J’ai développé un script `monitoring.sh` en bash, qui affiche toutes les 10 minutes les informations système clés sur tous les terminaux (via cron et wall).

📄 Les détails de mon script sont disponibles ici : [monitoring.sh](https://docs.google.com/document/d/1RxfQ3NQr1N-lqCcB0ruKLArxJWuvVgdGuBpF44vLVy4/edit?usp=sharing)


## 🧰 Quelques commandes utiles
- `lsblk` : voir le partitionnement
- `sudo aa-status` : vérifier AppArmor
- `ss -tnulp | grep 4242` : vérifier SSH
- `sudo ufw status` : vérifier le pare-feu
- `chage -l <user>` : vérifier la politique de mot de passe
- `sudo -l` ou consulter `/var/log/sudo/` : vérifier sudo

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

---
<p align="center">
  <img src="https://img.shields.io/badge/42-Network-blue?style=flat-square&logo=42&logoColor=white" alt="42"/>
  <img src="https://img.shields.io/badge/Linux-000000?style=flat-square&logo=linux&logoColor=white" alt="Linux"/>
  <img src="https://img.shields.io/badge/Virtualization-20C997?style=flat-square&logo=proxmox&logoColor=white" alt="Virtualization"/>
</p>
