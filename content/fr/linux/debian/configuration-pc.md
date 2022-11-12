---
title: Configuration PC
weight: 6
---

# Configuration PC

## Processeur Intel

Si le processeur utilisé est un processeur Intel

``` bash
sudo apt install intel-microcode
```


## Configuration pour jouer

``` bash
sudo apt install gamemode mangohud goverlay
```


## Fixe MSI

Installer les packets suivants pour la gestion du réseau

``` bash
sudo apt install firmware-realtek
```

### Icône réseau avec point d'interrogation

``` bash
sudo nano /etc/NetworkManager/NetworkManager.conf
```

Remplacer 

``` text
[ifupdown] managed=false
```

Par

``` text
[ifupdown] managed=true
```


## Portable Lenovo Legion

### Wifi et réseau

Installer les packets suivants pour la gestion du Wifi et du réseau

``` bash
sudo apt install firmware-iwlwifi firmware-realtek
```

Installer le gestionnaire de connexion

``` bash
sudo apt install network-manager-gnome
```

Si problème point d'interrgoration sur la connectvité réseau

``` bash
sudo apt install network-manager
```


### Problème réglage luminosité avec les touches Fn

``` bash
sudo nano /etc/default/grub
```

Modifier la ligne suivante

``` text
GRUB_CMDLINE_LINUX_DEFAULT="quiet nvidia.NVreg_RegistryDwords=EnableBrightnessControl=1"
```

Mettre à jour grub

``` bash
sudo update-grub
```


## Portable HP 6450b

### Wifi

Installer les packets suivants pour la gestion du Wifi

``` bash
sudo apt install firmware-iwlwifi network-manager-gnome libgtk2.0-0
```

### Led

Créer le fichier suivant pour éviter que la Led Wifi ne clignote

``` bash
sudo nano /etc/modprobe.d/wlan.conf
```

Ajouter

``` text
options iwlwifi led_mode=1
```

### Raccourci gestion connexion

``` bash
sudo gedit nm-connection-editor.desktop 
```

``` text
ajouter à la fin du fichier :
NotShowIn=GNOME;
```


## Portable Toshiba

Installer les packets suivant

``` bash
sudo apt install firmware-iwlwifi firmware-misc-nonfree pulseaudio-module-bluetooth blueman bluez-firmware network-manager-gnome 
```