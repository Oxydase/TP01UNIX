# TP 01 MILTON FIGUEIREDO

## 1.1 Installation Machine Virtuelle

L'installation de la VM Debian a été assez compliqué sur mon pc portable tout d'abord dû au fait que mon processeur n'était pas assez puissant ce qui à fait que j'ai dû récuperer un autre mini-iso puis les étapes de l'installation en mode expert étaient très lente à charger et ayant recommencé plusieurs fois j'ai finalement décidé d'utiliser la machine préinstallé sur le pc de l'université.

## 2.1 Configuration SSH

A l'aide de la commande `apt update` je récupère une mise à jour de la liste des paquets disponibles dans les dépots configurés et j'ai donc pu installer SSH avec la commande `apt install ssh`.

Il a ensuite fallu ajouter au fichier sshd config la ligne de commande `PermitRootLogin yes` pour permettre les connexion root distantes avec un mot de passe

## 2.2 Connexion

Pour se connecter il a fallu utiliser depuis un terminal sur notre machine personnelle la ligne de commande suivante : `ssh username@serveur` puis entrer le mot de passe

## 2.3 Nombre de paquets
```
root@serveur-correction:~# dpkg -l | wc -l
331
```
## 2.4 Space usage 
```
root@serveur-correction:~# df -h
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
udev               4,9G       0  4,9G   0% /dev
tmpfs              995M    572K  994M   1% /run
/dev/sda1          9,1G    1,6G  7,0G  19% /
tmpfs              4,9G       0  4,9G   0% /dev/shm
tmpfs              5,0M       0  5,0M   0% /run/lock
/dev/sda3          921M     31M  827M   4% /var/log
/dev/sda2          3,6G     40K  3,4G   1% /tmp
tmpfs              995M       0  995M   0% /run/user/0
```

## 2.5

**Locales**
```
root@serveur-correction:~# echo $LANG
fr_FR.UTF-8
```

**Nom machine**
```
root@serveur-correction:~# hostname
serveur-correction
```

**Domaine**
```
root@serveur-correction:~# man hostname
root@serveur-correction:~# domainname
(none)
```

**Verification emplacement dépots**
```
root@serveur-correction:~# cat /etc/apt/sources.list | grep -v -E '^#|^$'
deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware
```

**Passwd/shadow**
```
root@serveur-correction:~# cat /etc/apt/sources.list | grep -v -E '^#|^$'
deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware
```

**Compte utilisateur**
```
root@serveur-correction:~# cat /etc/passwd | grep -vE 'nologin|sync'
root:x:0:0:root:/root:/bin/bash
```

**fdisk -f**
```
Disque /dev/sda : 20 GiB, 21474836480 octets, 41943040 secteurs
Modèle de disque : HARDDISK        
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : gpt
Identifiant de disque : 3ED2EBFD-8995-4690-8EEF-8C65108F2339

Périphérique    Début      Fin Secteurs Taille Type
/dev/sda1        2048 19531775 19529728   9,3G Système de fichiers Linux
/dev/sda2    19531776 27344895  7813120   3,7G Système de fichiers Linux
/dev/sda3    27344896 29298687  1953792   954M Système de fichiers Linux
/dev/sda4    29298688 41940991 12642304     6G Partition d'échange Linux
```

**fdisk -x**
```
Disque /dev/sda : 20 GiB, 21474836480 octets, 41943040 secteurs
Modèle de disque : HARDDISK        
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : gpt
Identifiant de disque : 3ED2EBFD-8995-4690-8EEF-8C65108F2339

Périphérique    Début      Fin Secteurs Taille Type
/dev/sda1        2048 19531775 19529728   9,3G Système de fichiers Linux
/dev/sda2    19531776 27344895  7813120   3,7G Système de fichiers Linux
/dev/sda3    27344896 29298687  1953792   954M Système de fichiers Linux
/dev/sda4    29298688 41940991 12642304     6G Partition d'échange Linux
```

**Expliquer le retour de la commande df -h** 
C'est l'historique de stockage

## 3.1 installation automatique

Preseed sert à configurer des réponses aux questions posées lors de l'installation de debian afin d'automatiser celle-ci et de même avoir accès à des paramètres supplémentaires pas disponibles de base.
