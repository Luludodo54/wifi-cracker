# Guide d'Installation Détaillé

## Linux (Recommandé)

### Debian/Ubuntu
```bash
# Mise à jour du système
sudo apt-get update && sudo apt-get upgrade -y

# Installation d'aircrack-ng
sudo apt-get install -y aircrack-ng python3-pip

# Clonage du dépôt
git clone https://github.com/Luludodo54/wifi-cracker.git
cd wifi-cracker

# Installation des dépendances Python
pip3 install -r requirements.txt
```

### Arch Linux
```bash
sudo pacman -S aircrack-ng python-pip
git clone https://github.com/Luludodo54/wifi-cracker.git
cd wifi-cracker
pip install -r requirements.txt
```

### Fedora/RHEL
```bash
sudo dnf install aircrack-ng python3-pip
git clone https://github.com/Luludodo54/wifi-cracker.git
cd wifi-cracker
pip3 install -r requirements.txt
```

## macOS

### Via Homebrew
```bash
# Installer Homebrew si pas déjà installé
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Installation d'aircrack-ng
brew install aircrack-ng

# Clonage et setup
git clone https://github.com/Luludodo54/wifi-cracker.git
cd wifi-cracker
pip3 install -r requirements.txt
```

## Kali Linux (Pré-installé)

Aircrack-ng est déjà installé sur Kali Linux:
```bash
git clone https://github.com/Luludodo54/wifi-cracker.git
cd wifi-cracker
pip3 install -r requirements.txt
```

## Vérification de l'Installation

```bash
# Vérifier Python
python3 --version

# Vérifier aircrack-ng
sudo aircrack-ng --version

# Vérifier les dépendances Python
pip3 list | grep -E "paramiko|pycryptodome|scapy"
```

## Préparation de votre Interface WiFi

### Vérifier votre interface WiFi
```bash
# Affiche tous les appareils réseau
ifconfig
# ou
ip link show

# Cherchez: wlan0, wlan1, en0, etc.
```

### Activer le mode monitor manuellement
```bash
# Arrêter Network Manager
sudo systemctl stop NetworkManager

# Activer le mode monitor
sudo airmon-ng start wlan0

# Vérifier
sudo airmon-ng
```

## Prêt à utiliser !

```bash
sudo python3 wifi_cracker.py wlan0mon "VotreSSID" rockyou.txt
```

## Troubleshooting

### Problème: "aircrack-ng: command not found"
```bash
# Réinstaller
sudo apt-get install --reinstall aircrack-ng
```

### Problème: "Permission denied"
```bash
# Utiliser sudo
sudo python3 wifi_cracker.py ...
```

### Problème: Interface not found
```bash
# Vérifier les interfaces
iwconfig
# ou
nmcli device
```

## Support

Pour l'aide, créez une issue sur GitHub: 
https://github.com/Luludodo54/wifi-cracker/issues
