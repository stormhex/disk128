---
title: Logiciels
weight: 5
---

# Logiciels

## Veracrypt

Installer la bibliothèque d'interface graphique utilisateur GTK

``` bash
sudo apt-get install libgtk2.0-0:i386
```

Aller sur le site de Veracrypt pour télécharger la dernière version

``` text
Aller sur "https://www.veracrypt.fr/en/Downloads.html"
Prendre le lien dans Linux > Generic Installers
```

Effectuer l'instllation

``` bash
cd /home/axel/Téléchargements
wget https://launchpad.net/veracrypt/trunk/1.24-update7/+download/veracrypt-1.24-Update7-setup.tar.bz2
tar xjf veracrypt-1.24-Update7-setup.tar.bz2
sudo ./veracrypt-1.24-Update7-setup-gui-x64
```

Editer le fichier du raccourci

``` bash
sudo gedit /usr/share/applications/veracrypt.desktop
```

Ajouter

``` text
Actions=mount;unmount

[Desktop Action mount]
Name=Mount CRYPTED
Exec=veracrypt /mnt/pi4/_CRYPTED /media/veracrypt1

[Desktop Action unmount]
Name=Unmount CRYPTED
Exec=veracrypt -d /media/veracrypt1
```

Ajouter en favoris le dossier monté dans Nautilus (CTRL + D) et le renommer en "CRYPTED" 

## VSCodium

Aller sur
https://github.com/VSCodium/vscodium/releases

Télécharer le fichier qui se termine par "amd64.deb"

lancer l'installation

``` bash
sudo apt install ./codium_*
```

## Ledger Live

Aller sur le lien https://www.ledger.com/ledger-live/download pour télécharger la dernière version de Linux

### Installation

Lien d'aide :

https://support.ledger.com/hc/fr-fr/articles/115005165269-R%C3%A9soudre-les-probl%C3%A8mes-de-connexion-USB-avec-Ledger-Live?support=true

Rendre executable le fichier AppImage

``` bash
chmod +x ledger-live-*.AppImage
```

Ajouter les règles pour autoriser l'accès USB au Ledger

``` bash
wget -q -O - https://raw.githubusercontent.com/LedgerHQ/udev-rules/master/add_udev_rules.sh | sudo bash
```

Créer un dossier "Applications" dans le Home de l'utilisateur

``` bash
mkdir /home/axel/Applications
```

Déplacer le fichier .AppImage dans le dossier "Applications"

``` bash
mv ledger-live-desktop-*.AppImage ~/Applications
```

Rendre le fichier executable

``` bash
chmod +x ~/Applications/ledger-live-desktop-*.AppImage 
```

### Créer un lien symbolique

``` bash
sudo ln -s ~/Applications/ledger-live-desktop-*.AppImage /usr/bin/ledger-live
```

Mettre à jour le lien symbolique après une mise à jour de Ledger

``` bash
sudo ln -sfn ~/Applications/ledger-live-desktop-*.AppImage /usr/bin/ledger-live
```

### Icône

Créer un fichier pour l'îcone

``` bash
sudo gedit /usr/share/applications/ledger-live.desktop
```

Ajouter

``` text
[Desktop Entry]
Name=Ledger Live
Exec=ledger-live
Type=Application
Icon=/usr/share/icons/Papirus/24x24/apps/appimagekit-ledger-live-desktop.svg
Terminal=false
Categories=GNOME;GTK;Office;Finance;
Actions=update-shortcut;

[Desktop Action update-shortcut]
Name=Update shortcut
Exec=gnome-terminal -e "sudo gedit /usr/share/applications/ledger-live.desktop"
```


## Canon MG3650

``` bash
sudo apt install system-config-printer cups-backend-bjnp libcupsimage2
```

Télécharger et installer le driver de l'imprimante

``` bash
wget https://gdlp01.c-wss.com/gds/2/0100006902/01/cnijfilter2-5.20-1-deb.tar.gz
tar -xvzf cnijfilter2-5.20-1-deb.tar.gz
cd cnijfilter2-5.20-1-deb.tar.gz
./install.sh
```


## Arduino

``` bash
sudo apt install arduino
```

### Problème d'icône basse résolution

Pour résoudre le problème d'icône basse résolution dans le dock, éditer le fichier suivant :

``` bash
sudo nano /usr/share/applications/arduino.desktop
```

Ajouter :

``` text
StartupWMClass=processing-app-Base
```


## Virtualbox

Aller sur "https://download.virtualbox.org/virtualbox/" pour récupérer les liens de téléchargement

Télécharger les fichiers

``` bash
cd ~/Téléchargements
wget https://download.virtualbox.org/virtualbox/6.1.26/virtualbox-6.1_6.1.26-145957~Debian~bullseye_amd64.deb
wget https://download.virtualbox.org/virtualbox/6.1.26/Oracle_VM_VirtualBox_Extension_Pack-6.1.26.vbox-extpack
```

Installer le packet et installer les dépendances

``` bash
sudo dpkg -i virtualbox-6.1_6.1.26-145957~Debian~bullseye_amd64.deb
sudo apt install -f
```

### Installer VirtualBox Extension Pack

Installation de VM VirtualBox Extension Pack

*Fichier > Paramètres > Extensions
*Ajouter le fichier téléchargé


### Résoudre le problème d'icône

Pour le problème d'icône quand une VM est lancée, éditer le fichier :

``` bash
sudo gedit /usr/share/applications/virtualbox.desktop
```

Ajouter et remplacer après "comment[sv]" :

``` text
StartupWMClass=VirtualBoxVM
Actions=Open;Start

[Desktop Action Open]
Exec=VirtualBox %U
Name=Open VirtualBox

[Desktop Action Start]
Exec=vboxmanage startvm "debian"
Name=Start Debian

[Desktop Action Stop]
Exec=vboxmanage controlvm "debian" acpipowerbutton
Name=Stop Debian
```