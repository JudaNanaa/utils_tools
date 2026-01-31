# Mon goinfre perso

Espace temporaire très gros (RAM + swap) → disparaît au redémarrage de la machine.

## Étapes (à faire une seule fois)

```bash
# 1. Créer le dossier
sudo mkdir -p /goinfre/$USER

# 2. Donner les droits
sudo chown -R $USER:$USER /goinfre/$USER

# 3. Créer le raccourci dans ton home (le plus pratique)
ln -s /goinfre/$USER ~/goinfre
```


## Option : tout effacer automatiquement à chaque reboot
```Bash
# Ouvre ton crontab
crontab -e
```

Ajoute cette ligne :

```bash
@reboot rm -rf /goinfre/$USER/*
```

(Sauvegarde : Ctrl+O → Entrée → Ctrl+X si tu es sur nano)
