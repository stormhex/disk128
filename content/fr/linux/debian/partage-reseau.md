---
title: Partage réseau
weight: 2
toc: false
---

{{< breadcrumbs >}}

# Partage réseau

## Packets nécessaires

``` bash
sudo apt install nfs-common autofs
```

## Configuration AutoFS

AutoFS permet de monter automatiquement les partages NFS

Créer les dossiers nécessaires, changer les noms de dossier si besoin

``` bash
sudo mkdir /mnt/pi4
```

Editer le fichier

``` bash
sudo nano /etc/auto.master
```

Ajouter à la fin du fichier

``` bash
/-	/etc/auto.misc
```

Editer le fichier suivant

``` bash
sudo nano /etc/auto.misc
```

Ajouter à la fin du fichier la ligne suivante, adresse IP et chemin du partage à adapter

``` bash
/mnt/pi4    -fstype=nfs4,rw  192.168.1.5:/mnt/ssd/
```

Relancer le service

``` bash
sudo service autofs restart
```