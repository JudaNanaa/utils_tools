# My personal goinfre

Very large temporary storage (RAM + swap) → **cleared on machine reboot**

## Setup (one-time)

```bash
# 1. Create the directory
sudo mkdir -p /goinfre/$USER

# 2. Set permissions

sudo chown -R $USER:$USER /goinfre/$USER

# 3. Create a shortcut in your home (recommended)
ln -s /goinfre/$USER ~/goinfre
```

## Optional: automatically wipe everything on reboot
```Bash
# Open your crontab
crontab -e
```

Add this line:

```bash
@reboot rm -rf /goinfre/$USER/*
```

(Save: Ctrl+O → Enter → Ctrl+X if you are using nano)

# Powerlevel10k – super beau prompt pour Zsh

Powerlevel10k est un thème très rapide et configurable pour Zsh  
→ icônes, git status, couleurs, wizard de configuration...

## Prérequis (déjà fait dans ton cas)

- zsh installé  
- Oh My Zsh installé
- Une police Nerd Font installée et sélectionnée dans ton terminal (ex: Hack Nerd Font, FiraCode Nerd Font, etc.)

## Installation (en 3 étapes)

```bash
# 1. Télécharger Powerlevel10k dans le dossier des thèmes Oh My Zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
    ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```

```bash
# 2. Activer le thème dans ~/.zshrc
# Ouvre le fichier (avec nano, vim, code, etc.)
nano ~/.zshrc
```

Change cette ligne :

```bash
ZSH_THEME="robbyrussell"     # ← ancienne valeur
```
en :

```Bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Puis sauvegarde (Ctrl+O → Enter → Ctrl+X avec nano)

```bash
# 3. Recharger zsh (ou ouvre un nouveau terminal)
source ~/.zshrc
```

À ce stade, le wizard de configuration Powerlevel10k devrait se lancer automatiquement.
Sinon, lance-le manuellement :

```bash
p10k configure
```

Suis les instructions à l’écran (il détecte et installe la police si nécessaire).

## Plugins recommandés (syntaxe + autosuggestions)

```bash
# Installer les deux plugins les plus populaires
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
	${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions \
	${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Puis édite à nouveau ```~/.zshrc``` :
```Bash
nano ~/.zshrc
```

Cherche la ligne qui commence par ```plugins=(``` et modifie-la pour inclure les nouveaux plugins :
```bash
plugins=( git zsh-syntax-highlighting zsh-autosuggestions )
```

Enregistre et recharge :
```bash
source ~/.zshrc
```

Ton terminal devrait maintenant être bien plus agréable.