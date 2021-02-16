# Linux | Arborescence

* `/` :
    Ce répertoire est le dossier "racine" qui contient tous les répertoires principaux du système.
* `/bin` (Binaries)
    Ce répertoire contient les exécutables essentiels au système.
    Ces exécutables sont utilisables par tous les utilisateurs.
    (ex: `ls`, `pwd`, `cp`)
* `/sbin` (Super Binaries)
    Ce répertoire contient les exécutables systèmes.
    Ces exécutables sont utilisables par l'utilisateur `root` uniquement.
    Ex: `cfdisk`, `fsck`, `halt`, `init`, `iptable`
* `/boot`
    Ce répertoire contient les fichiers permettant à Linux de démarrer.
* `/dev` (Device)
    Ce répertoire contient les fichiers spéciaux représentant les point d'entrées de tous les périphériques
    (ex: disques durs, écrans, partitions, consoles TTY, webcam)
* `/etc` (Editing Text Config)
    Ce répertoire contient les fichiers textes nécessaires à la configuration du système et des services.
    (ex: `XXX.conf`, `passwd`, `inittab`, `fstab`)
* `/home`
    Ce répertoire est le dossier personnel des utilisateurs.
* `/lib` (Librairies)
    Ce répertoire contient les bibliothèques partagées essentielles au système lors du démarrage.
* `/lib64` = `lib` en 64bits
* `/mnt` (Mount)
    Ce répertoire contient les ressources qui sont montées de manière temporaire.
* `/media`
    Ce répertoire contient les ressources qui sont montées de manière définitive.
* `/opt` (Optional)
    Ce répertoire contient les programmes installés hors des dépôts de la distribution.
    Ces programmes sont généralement propriétaires.
    Ex: Spotify, TeamSpeak, Skype, AnyDesk
* `/proc` (Process)
    Ce répertoire est un dossier virtuel qui ne prend aucune place et qui contient des informations sur le noyau et les processus en cours.
* `/root`
    Ce répertoire est le dossier personnel de l'utilisateur `root`.
    Il est séparé du répertoire `/home` pour être certain qu'il soit bien monté et accessible par l'utilisateur `root` au démarrage du système. En effet, le répertoire `/home` se trouve généralement sur une partition à part et peut ne pas être monté en cas de problème.
* `/run` (Runtime)
    Ce répertoire contient des informations relatives au système concernant les utilisateurs et les services en cours d'exécution
* `/srv` (Service)
    Ce répertoire contient des données pour divers services (ex: stockage des documents de comptes FTP, ou pages de sites web)
    Il n'est pas disponible sur toutes les distributions
* `/sys` (System)
    Ce répertoire est un dossier virtuel qui ne prend aucune place et qui contient des informations entre le système et ses composants matériels
* `/tmp` (Temporary) => Répertoire fichier temporaires
    Ce répertoire est un dossier temporaire qui est vidé à chaque démarrage.
* `/usr` (Unix System Resources)
* `/usr/bin`
    Ce répertoire contient les programmes installés pour tous les utilisateurs.
    Ex: Firefox, LibreOffice
* `/usr/sbin`
    Ce répertoire contient les programmes installés pour l'utilisateur `root` uniquement.
* `/usr/lib`
    Ce répertoire contient les librairies des programmes installés.
* `/usr/src`
    Ce répertoire contient les codes sources des programmes installés manuellement.
* `/usr/local` (TOCHECK)
    Ce répertoire contient les programmes installés manuellement en compilant leurs codes sources.
* `/usr/share` (TOCHECK)
    Ce répertoire contient les éléments partagés indépendants de l'architecture
    Ex: documentations, icones, fonds d'écran configs qui sont indépendant d'une architecure
* `/var` (Variable)
    Ce répertoire contient les données variables.
* `/var/log`
    Ce répertoire contient les logs (avec un sous répertoire par service).
    Ex: `/var/log/message`
* `/var/lib`
    Ce répertoire contient les données variables liées aux programmes.
    Ex: les fichiers de base de données de `MySQL`
* `/var/www`
    Ce répertoire contient les fichiers qui sont hébergés par les serveurs web.
