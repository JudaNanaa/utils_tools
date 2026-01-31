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