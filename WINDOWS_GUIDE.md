# WiFi Cracker - Windows Guide 🪟

## Installation sur Windows

### Prérequis
- **Windows 10/11**
- **Python 3.8+** (https://www.python.org/downloads/)
- **Accès Administrateur**

### Étape 1: Installer Python

1. Télécharger Python depuis https://www.python.org/downloads/
2. **IMPORTANT**: Cocher "Add Python to PATH"
3. Cliquer sur "Install Now"

### Étape 2: Cloner le dépôt

```bash
git clone https://github.com/Luludodo54/wifi-cracker.git
cd wifi-cracker
```

### Étape 3: Installer les dépendances

```bash
pip install -r requirements.txt
```

### Étape 4: Télécharger une Wordlist

**Option A: rockyou.txt (recommandé)**
```bash
# Télécharger depuis le site officiel
# https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
# Et placer dans le dossier du projet
```

**Option B: Créer votre propre wordlist**
```
Créer un fichier `passwords.txt` avec un mot de passe par ligne:
password123
12345678
monwifi123
etc...
```

## Utilisation

### 1. Ouvrir PowerShell en tant qu'ADMINISTRATEUR

- Clic droit sur le menu Démarrer
- Cliquer sur "Windows PowerShell (Admin)" ou "Terminal (Admin)"

### 2. Aller dans le dossier du projet

```powershell
cd C:\Users\YourName\wifi-cracker
```

### 3. Lancer le script

```powershell
python wifi_cracker_windows.py "VotreSSID" rockyou.txt
```

### Exemples concrets

```powershell
# Exemple 1: WiFi personnel
python wifi_cracker_windows.py "Orange-1234" rockyou.txt

# Exemple 2: Avec wordlist personnalisée
python wifi_cracker_windows.py "MonReseau" passwords.txt

# Exemple 3: Mode verbeux (debug)
python wifi_cracker_windows.py "MyWiFi" wordlist.txt -v
```

## Résultat

Si le mot de passe est trouvé, vous verrez:

```
[+] ✅ PASSWORD TROUVÉ!
[+] SSID: VotreSSID
[+] Password: monmotdepasse123
[+] Temps écoulé: 45.23 secondes
[+] Mots de passe testés: 1523
```

Le résultat est également sauvegardé dans `wifi_cracked.json`

## 📥 Wordlists Recommandées

### 1. rockyou.txt (140 MB)
- La plus populaire et efficace
- Télécharger: https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt

### 2. fasttrack.txt
- Version rapide mais moins complète
- Idéale pour les premiers tests

### 3. Créer votre propre
```bash
# Combiner plusieurs wordlists
type rockyou.txt passwords.txt > combined.txt
```

## ⚠️ Avertissements Importants

- ✅ Exécutez **EN TANT QU'ADMINISTRATEUR**
- ✅ Testez **UNIQUEMENT** sur des réseaux dont vous avez la permission
- ✅ Le crack non autorisé est **ILLÉGAL**
- ✅ Gardez les mots de passe trouvés **CONFIDENTIELS**

## Troubleshooting

### Erreur: "python: command not found"

**Solution**: Python n'est pas dans le PATH
1. Désinstaller Python
2. Réinstaller en cochant "Add Python to PATH"
3. Redémarrer l'ordinateur

### Erreur: "Access Denied"

**Solution**: Lancer en tant qu'ADMINISTRATEUR
- Clic droit sur PowerShell/CMD
- "Exécuter en tant qu'administrateur"

### Erreur: "File not found: rockyou.txt"

**Solution**: Télécharger la wordlist
```bash
# Windows: Utiliser le navigateur ou:
Invoke-WebRequest -Uri "https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt" -OutFile "rockyou.txt"
```

### Le crack est très lent

**Solutions**:
1. Utiliser une wordlist plus petite
2. Vérifier que le SSID est correct
3. S'assurer que vous êtes à proximité du routeur

### Mot de passe non trouvé

- Le mot de passe n'est pas dans la wordlist
- Le SSID est mal épelé
- Essayez une autre wordlist

## Performance

| Wordlist | Taille | Temps Approx |
|----------|--------|-------------|
| fasttrack.txt | 1.5 MB | < 1 min |
| rockyou.txt | 140 MB | 5-30 min |
| Custom (100) | - | < 10 sec |

## ℹ️ Note Technique

Le script Windows utilise:
- **netsh** (outil Windows natif)
- **WPA2/WPA3 profiles** (WiFi standard)
- **Dictionary attack** (force brute avec wordlist)

C'est moins rapide que la version Linux mais fonctionne nativement sur Windows.

## 🔗 Ressources

- Microsoft netsh docs: https://docs.microsoft.com/en-us/windows-server/networking/technologies/netsh/netsh
- WiFi Security: https://owasp.org/www-community/attacks/Brute_force_attack
- Wordlists: https://github.com/brannondorsey/naive-hashcat

---

**Bon crack! 🔓 Mais utilisez-le légalement! ⚖️**
