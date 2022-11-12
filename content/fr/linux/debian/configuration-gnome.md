---
title: Configuration Gnome
weight: 3
---

# Configuration Gnome

## Packets additionels nécessaires

``` bash
sudo apt install steam krita git homebank keepassxc vlc neofetch ntfs-3g exfat-fuse exfat-utils eject zip gnome-tweak-tool nautilus-admin
```

## Suppressions packets inutiles

``` bash
sudo apt purge gnome-contacts totem malcontent
sudo apt autoremove
```

## Gnome Tweak Tool

Modifier les paramètres suivant dans Gnome Tweak Tool (Ajustements)

* Barre de titre des fenêtres > Cocher "Maximiser" et "Minimiser"
* Barre supérieure > décocher "Jour de semaine"
* Barre supérieure > décocher "Coin actif pour la vue d'ensemble des activités"


## Terminal

Modification du thème utilisé dans le Terminal

* Préférences > Sans nom > Couleur >  Décocher "Utiliser les couleurs du thème système" > Solarizé sombre


## Dash To Panel

``` bash
sudo apt install gnome-shell-extension-dash-to-panel
```

### Configuration Dash To Panel

A REVOIR

``` bash
gsettings set org.gnome.shell.extensions.dash-to-panel panel-positions '{"0":"LEFT"}'
gsettings set org.gnome.shell.extensions.dash-to-panel dot-position 'RIGHT'
gsettings set org.gnome.shell.extensions.dash-to-panel panel-size 30


gsettings set org.gnome.shell.extensions.dash-to-panel dot-color-dominant true
gsettings set org.gnome.shell.extensions.dash-to-panel dot-size 2
gsettings set org.gnome.shell.extensions.dash-to-panel dot-style-focused 'DASHES'
gsettings set org.gnome.shell.extensions.dash-to-panel dot-style-unfocused 'DASHES'
gsettings set org.gnome.shell.extensions.dash-to-panel trans-use-custom-bg true
gsettings set org.gnome.shell.extensions.dash-to-panel trans-bg-color '#000000'
gsettings set org.gnome.shell.extensions.dash-to-panel trans-use-custom-opacity true
gsettings set org.gnome.shell.extensions.dash-to-panel trans-panel-opacity 0.4
gsettings set org.gnome.shell.extensions.dash-to-panel trans-use-dynamic-opacity true
gsettings set org.gnome.shell.extensions.dash-to-panel trans-dynamic-anim-target 1.0
gsettings set org.gnome.shell.extensions.dash-to-panel trans-dynamic-behavior 'ALL_WINDOWS'
gsettings set org.gnome.shell.extensions.dash-to-panel window-preview-show-title false

gsettings set org.gnome.shell.extensions.dash-to-panel window-preview-size 120
gsettings set org.gnome.shell.extensions.dash-to-panel peek-mode false



gsettings set org.gnome.shell.extensions.dash-to-panel panel-element-positions '{"0":[{"element":"activitiesButton","visible":false,"position":"stackedTL"},{"element":"leftBox","visible":false,"position":"stackedTL"},{"element":"showAppsButton","visible":true,"position":"stackedTL"},{"element":"taskbar","visible":true,"position":"stackedTL"},{"element":"rightBox","visible":false,"position":"stackedBR"},{"element":"centerBox","visible":false,"position":"stackedBR"},{"element":"systemMenu","visible":false,"position":"stackedBR"},{"element":"dateMenu","visible":false,"position":"stackedBR"},{"element":"desktopButton","visible":false,"position":"stackedBR"}]}'
```

org.gnome.shell.extensions.dash-to-panel panel-size 26
org.gnome.shell.extensions.dash-to-panel appicon-padding 2
org.gnome.shell.extensions.dash-to-panel appicon-margin 6
org.gnome.shell.extensions.dash-to-panel dot-size 2
org.gnome.shell.extensions.dash-to-panel dot-color-dominant true
org.gnome.shell.extensions.dash-to-panel dot-position 'BOTTOM'
org.gnome.shell.extensions.dash-to-panel dot-style-focused 'DASHES'
org.gnome.shell.extensions.dash-to-panel dot-style-unfocused 'DASHES'



## Nautilus

Personnaliser Nautilus

``` bash
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'
gsettings set org.gnome.nautilus.preferences show-hidden-files true
gsettings set org.gnome.nautilus.list-view default-zoom-level 'small'
gsettings set org.gnome.nautilus.window-state maximized  true
gsettings set org.gtk.Settings.FileChooser sort-directories-first true
```


## Thème et personnalisation

### Thème Fluent

``` bash
git clone https://github.com/vinceliuice/Fluent-gtk-theme
cd Fluent-gtk-theme/
./install.sh -s compact --tweaks solid --tweaks square --tweaks noborder
```

### Icônes Papirus

``` bash
sudo apt install papirus-icon-theme
```

### Polices

``` bash
wget https://fonts.google.com/download?family=Roboto
sudo unzip Roboto.zip -d /usr/share/fonts/Roboto
wget https://fonts.google.com/download?family=Open%20Sans
sudo unzip Open_Sans.zip -d /usr/share/fonts/Open_Sans
wget https://fonts.google.com/download?family=Fira%20Sans
sudo unzip Fira_Sans.zip -d /usr/share/fonts/Fira_Sans
```


## Extensions

### Extensions natives

Installer les dépendances

``` bash
sudo apt install lm-sensors
```

Installer les extensions

``` bash
sudo apt install gnome-shell-extension-freon gnome-shell-extension-caffeine gnome-shell-extension-top-icons-plus gnome-shell-extension-volume-mixer
```

Additionel si besoin

``` bash
sudo apt install gnome-shell-extension-hide-activities gnome-shell-extension-pixelsaver gnome-shell-extension-autohidetopbar
```

### CPU Power

Installer les dépendances

``` bash
sudo apt install make gettext
```

Installer l'extension

``` bash
git clone https://github.com/martin31821/cpupower.git
cd cpupower
sudo make install PREFIX=/home/axel/.local
```

### Clipboard Indicator

``` bash
wget https://github.com/Tudmotu/gnome-shell-extension-clipboard-indicator/archive/refs/tags/v37.zip
sudo unzip v37.zip -d ~/.local/share/gnome-shell/extensions/
sudo mv ~/.local/share/gnome-shell/extensions/gnome-shell-extension-clipboard-indicator-37 ~/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com
```


## Raccourcis

### Accès au Raspberry

Le raccourci suivant permet de se connecter au Raspberry en SSH en faisant un clic gauche sur l'icône du terminal

``` bash
sudo gedit /usr/share/applications/org.gnome.Terminal.desktop
```

Ajouter "pi-ssh" dans la ligne "Actions" sous [Desktop Entry]

``` text
Actions=new-window;preferences;pi-ssh;
```

Ajouter aussi le texte suviant, adresse IP à définir

``` text
[Desktop Action pi-ssh]
Name=SSH on Raspberry Pi
Exec=gnome-terminal -e "ssh pi@ip_address"
```

### Presse papier pour mails

``` bash
sudo apt install xdotool xclip
```

Ajouter les raccourcis suivant dans

* Paramètres > Raccourcis clavier

| Nom          | Commande                                                                                                               | Raccourci     |
|--------------|------------------------------------------------------------------------------------------------------------------------|---------------|
| Mail_Gmail   | /bin/bash -c "sleep 0.2 && printf 'mail_address@gmail.com' \| xclip -selection clipboard && xdotool key Control_L+v"   | CTRL + &      |
| Mail_Orange  | /bin/bash -c "sleep 0.2 && printf 'mail_address@orange.fr' \| xclip -selection clipboard && xdotool key Control_L+v"   | CTRL + eacute |
| Mail_Hotmail | /bin/bash -c "sleep 0.2 && printf 'mail_address@hotmail.com' \| xclip -selection clipboard && xdotool key Control_L+v" | CTRL + "      |


Pour ajouter un raccourci pour fermer un processus bloqué

| Nom   | Commande   | Raccourci           |
|-------|:----------:|--------------------:|
| xkill | xkill      | CTRL + ALT + Espace |


## Optimiser SWAP

Pour vérifier la valeur du paramètre actuel

``` bash
cat /proc/sys/vm/swappiness
```

Editer le fichier

``` bash
sudo nano /etc/sysctl.conf
```

Ajouter à la fin du fichier

``` text
vm.swappiness = 10
```