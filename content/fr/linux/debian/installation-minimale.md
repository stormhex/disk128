---
title: Installation minimale
weight: 1
---

# Installation minimale

Installer une version minimale de Debian avec le desktop Gnome ou XFCE

## Partitions

| Partition | Type   | Taille   |
|-----------|:------:|---------:|
| 1         |  EFI   |  256Mb   |
| 2         |  SWAP  |  16384   |
| 3         |  EXT4  |  Reste   |

## Logiciels

Cocher seulement

``` text
Utilitaires usuels du système
```

## Packets indispensables

Après l'installation, redémarrer le système et se connecter en "root"

``` bash
su root
```

Installer les packets ci-dessous

``` bash
apt install sudo net-tools software-properties-common
```

Ajouter l'utilisateur créé pendant l'installation au groupe "sudo"

``` bash
adduser <username> sudo
```

Ajouter les depôts "non-free" et "contrib" et l'architecture i386

``` bash
add-apt-repository non-free
add-apt-repository contrib
dpkg --add-architecture i386
```

Mettre à jour le système

``` bash
apt update
apt upgrade
```

## Drivers NVIDIA

Installer Nvidia Detect pour savoir ce qu'il est recommandé d'installer

``` bash
apt install nvidia-detect
```

Lancer Nvidia Detect

``` bash
nvidia-detect
```

Installation du driver s'il est bien indiqué "It is recommanded to install the nvidia-driver package"

``` text
apt install nvidia-driver
```

Redémarrer le système

``` bash
reboot
```

## Environnement graphique de bureau

Les rubriques ci-dessous Gnome et XFCE permettent d'installer les environnements de bureau avec le minimum de packets

{{< color-block style="warning" >}}
Poursuivre avec l'installation de Gnome OU Xfce
{{< /color-block >}}

### Gnome

``` bash
apt install xfonts-base xserver-xorg gnome-core
```

### XFCE

``` bash
apt install xfce4 xfce4-terminal mousepad
```

## Redémarrer le système

``` bash
reboot
```

## Ajouter rescuezilla au boot

``` bash
sudo apt install grml-rescueboot
``` 

Télécharer la dernière version de rescuezilla sur https://rescuezilla.com/

Renommer le fichier avec le nom "rescuezilla.iso" et le déplacer dans "/boot/grml/"

``` bash
sudo mv /home/axel/Téléchargements/rescuezilla.iso /boot/grml/
```

Mettre à jour Grub

``` bash
suod update-grub
```