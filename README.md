# Enric's Fedora Silverblue Image

## Create a rootful Fedora 42 container

```bash
distrobox assemble create --replace --file  opt/distrobox/fedora-distrobox-42.ini
```

To enter, run:

```bash
distrobox enter --root fedora-distrobox-42
```

## Problems and solutions

### VSCODE : The password you use to log in to your computer no longer matches that of your login keyring

1. Remove the following file

```bash
rm ~/.local/share/keyrings/*.keyring
```

2. Next time you will be required to set a new password.

