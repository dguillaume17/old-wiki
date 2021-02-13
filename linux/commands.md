# Linux | Commandes

## Textes

### `cat`

Imprimer le fichier d'un fichier texte

Paramètres :

* `-n` | `--number` = afficher le numéro de lignes
* `-b` | `--number-nonblank` = afficher le numéro des lignes non vides

### `echo`

Imprimer le contenu passé en paramètre

### `less`

Visualiser le contenu d'un fichier texte et naviguer

Raccourcis :

* Haut | Bas : (`up` | `down`) ou (`y` | `e`) ou (`k` | `j`)
* Début | Fin : `b` | `space`
* Quitter : `q`

Exemple :

```bash
less toto.txt
```

### `more`

Visualiser le contenu d'un fichier texte et descendre via "load more"

Raccourcis :

* Descendre : `enter`
* Quitter : `q`

### `head`

Imprimer les x premières lignes d'un fichier texte

Paramètres

* `-%count%` = nombre de lignes à afficher (10 par défaut)

### `sort`

Trier les lignes par ordre alphabétique

Paramètres :

* `-r` | `--reverse` = nombre de lignes à afficher (10 par défaut)

### `tail`

Imprimer les x dernières lignes d'un fichier texte

Paramètres :

* `-%count%` = nombre de lignes à afficher (10 par défaut)
* `-f` = afficher les dernières lignes en temps réel (utile pour suivre l'évolution des fichiers de log)

Raccourcis :

* Créer des lignes vides en mode follow (`-f`) : `enter`

### `uniq`

Gérer les lignes identiques consécutives

Paramètres :

* `-c` | `--count` : pour chaque ligne, compter le nombre d'occurrences
* `-i` | `--ignore-case` : ignorer la casse pour comparer les lignes
* `-u` | `--unique` : lister uniquement les lignes uniques
* `-d` | `--repeated` : lister uniquement les lignes dupliquées

### `wc`

Compter le nombre de lignes, de mots et de caractères d'un fichier

Paramètres :

* `-l` | `--lines` : nombre le lignes
* `-w` | `--words` : nombre de mots
* `-c` | `--chars` : nombre de caractères

## Permissions

### `chmod`

Modifier les droits d'un répertoire

Exemple :

```bash
chmod 777 .
```

### `chown`

[_TODO_]

## Processus

### `iotop`

Ouvrir un task manager

Raccourcis :

* Changer le tri (selon la colonne sélectionnée) : `left` ou `right`

### `glances`

Ouvrir un task manager

Raccourcis :

* Changer le tri (selon la colonne sélectionnée) : `left` ou `right`
* Afficher l'aide et les raccourcis in-app : `h`
* Quitter : `q`

Couleurs :

* Vert : OK
* Bleu : Mise en garde
* Violet : Attention
* Rouge : Critique

### `ps`

Lister tous les process

Paramètres :

* `-a` = lister les process pour tous les utilisateurs
* `-u` = afficher des colonnes supplémentaires et trier par nom d'utilisateur
* `-x` = lister en plus les process liés à des services
* `-f` = afficher l'arborescence

Exemple :

```bash
ps -aux
```

### `sleep`

Faire une pause (mesurée en secondes)

## Programmes

### `watch`

Exécute une commande à intervalle régulier et affiche le résultat dans la console

Syntaxe :

```bash
watch -n <seconds> '<command>'
```

Exemple :

```bash
watch -n 2 'ps aux'
```

### `which`

Vérifier si un programme est bien installé et imprimer son répertoire d'installation

Syntaxe :

```bash
which <program-name>
```

## Recherches

### awk

#### Mode `print`

Imprimer une colonne d'un fichier à séparateurs

Paramètres :

* `-F%sep%` = définir le caractère à utiliser comme séparateur
* `$%num%`= numéro de la colonne à imprimer

Exemple:

```bash
less /etc/passwd | awk -F: '{print $1}'
```

### `grep`

Imprimer les lignes correspondant à un motif donné

Paramètres :

* `-c` = compter le nombre d'occurrences
* `-v` | `--invert-match` = ne pas interpréter le motif
* `-G` = interpréter   le   motif   comme  une  expression  rationnelle  simple (comportement par défaut)
* `-E` = interpréter  le  motif  comme  une  expression  rationnelle étendue
* `-P` = interpréter le motif comme une expression rationnelle Perl
* `-i` = ignorer la casse
* `-n` = afficher les numéros des lignes
* `-<number>` = afficher les x lignes qui précèdent et succèdent le résultat
* `-r <folder-path>` = recherche dans tous les fichier du répertoire et de ses sous-répertoires (pas possible en mode `pipe`)

Exemples :

* mode `pipe`

```bash
ps aux | grep -v "bash"
```

* recherche

```bash
grep "log" -c -r /var/www/api
```

### `sed`

#### Mode substitution

Remplacer une chaîne dans un fichier texte

Syntaxe :

```bash
sed -i 's/<regex>/<new_text>/<regex_flag>' file.txt
```

Paramètre :

* `-i` = sauvegarder le résultat dans le fichier d'origine

Exemple:

```bash
sed -i 's/original/new/g' file.txt
```

## Remote

### `scp`

Copier un fichier d'un serveur ssh vers un autre

Exemple :

* D'un serveur vers le poste local

```bash
scp gder@192.168.0.70:/home/gder/temp/test.txt /home/toto/temp/test2.txt
```

* Du poste local vers un serveur

```bash
scp /home/toto/temp/test.txt gder@192.168.0.70:/home/gder/temp/test2.txt
```

* D'un serveur vers un autre serveur

```bash
scp toto@192.168.0.60:/home/toto/temp/test.txt gder@192.168.0.70:/home/gder/temp/test2.txt
```

### `screen`

Permt d'ouvrir plusieurs terminaux dans une même console, de passer de l'un à l'autre et de les récupérer plus tard

Remarques :

* `session` = terminal dans une console
* si `echo $TERM` imprime `screen`, alors on est attaché à une session

#### Lister les sessions en cours

Syntaxe :

```bash
screen -ls
```

#### Créer une session

Syntaxe :

```bash
screen -S <session-name>
```

#### Attacher une session

Syntaxe :

```bash
screen -r <session-name>
```

#### Détacher une session

Syntaxe :

```bash
screen -d [<session-name>]
```

Remarque :

* si `<session-name>` est vide, on prend la session en cours

#### Supprimer une session

Syntaxe :

```bash
screen -r <session-name>
exit
```

### `ssh`

Se connecter sur un serveur ssh

Exemple :

```bash
ssh gder@192.168.0.70
```

## Systèmes de fichier

### `df`

Lister les partitions et les espaces disques

Paramètres :

* `-h` = afficher les tailles en notation ingénieur

### `du`

Imprimer la taille des répertoires

Paramètres :

* `-h` = afficher la taille en notation ingénieur
* `-d<niveau>` = profondeur maximum

#### Imprimer la taille d'un répertoire

Syntaxte :

```bash
du -c <folder-path>
```

#### Imprimer la taille des sous-répertoires contenus dans un dossier

Syntaxte :

```bash
du <folder-path>
```

#### Imprimer la taille des sous-répertoires et des fichiers contenus dans un dossier

```bash
du <folder-path> -a
```

### find

Recherche de fichiers ou de répertoires

Paramètres :

* `-maxdepth <depth>` = profondeur max des sous répertoires
* `-type d` = uniquement les répertoires
* `-type f` = uniquement les fichiers

### `ls`

Lister le contenu d'un ou plusieurs répertoires

Paramètres :

* `-l` = mode liste
* `-a` = voir les contenus cachés
* `-F` = voir un astérix après le nom de chaque fichier exécutable
* `-h` | `--human-readable` = afficher les tailles en notation ingénieur (uniquement en mode liste)
* `-d` | `--directory` = imprimer les informations du répertoire passé en paramètre

Alias :

* `l` = `ls`
* `ll` = `ls -laF`

Exemple :

* Imprimer les infos des répertoires `/var` et `/mount`

```bash
ls -ld /var /mnt
```

* Lister les répertoires de `/var`

```bash
ls -ld /var/*/
ls -l /var | grep "^d"
```

### `lsof`

Lister les fichiers ouverts et les fichiers supprimés

Paramètres :

* `-t` = lister uniquement les PID
* `<folder-path>` = limiter au répertoire spécifié et à ses sous-répertoires
* `+D <folder-path>` = limiter au répertoire spécifié (sans ses sous-répertoires)
* `-u <user-name>` = limiter la liste pour l'utilisateur spécifié
* `-u ^<user-name>` = limiter la liste pour tous sauf l'utilisateur spécifié
* `-p <pid>` = limiter la liste pour le PID spécifié
* `-i` = limiter uniquement les connexions réseaux
* `-i <port-numer>` = limiter uniquement les connexions réseaux sur le port spécifié

Remarque :

* chaque paramètre est une condition séparée par un `OU`

### `mkdir`

Créer un répertoire

Paramètres :

* `-p` | `--parents` = ne pas retourner d'erreur si le répertoire existe déjà et créer les sous-répertoires parents si besoins

### `pwd`

Imprimer le chemin du répertoire en cours

### `rm`

Supprimer des fichiers ou des répertoires

Paramètres :

* `-f` | `--force` = ne pas retourner d'erreur si le fichier ou le répertoire n'existe pas
* `-r` | `--recursive` = supprimer un répertoire et son contenu
* `-d` | `--dir` = supprimer un répertoire vide

## Réseau

### `tcpdump`

Capturer le traffic réseau

#### Lister les interfaces sur lesquelles capturer

Syntaxe :

```bash
tcpdump -D
```

#### Capturer sur une interface

Syntaxe :

```bash
tcpdump -i <interface>
```

Paramètres :

* `-c<count>` = se limiter à `<count>` paquet(s)
* `-n` = désactiver la résolution de noms
* `-nn` = désactiver la résolution de noms et de ports
* `host <host-name>` = se limiter à un hôte
* `port <port-number>` = se limiter à un numéro de port
* `tcp | udp | icmp` = filter les paquets TCP ou UDP ou ICMP

## Utilisateurs

### `addgroup`

Créer un groupe d'utilisateurs (Cfr. fichier `/etc/group`)

Exemple :

```bash
sudo addgroup easi
```

### `adduser`

#### Mode création

Créer un utilisateur (Cfr. fichier `/etc/passwd`)

Exemple :

```bash
sudo adduser toto
```

### Mode affectation groupe

Ajouter un groupe à un utilisateur

Exemple :

```bash
sudo adduser toto easi
```

### `delgroup`

Supprimer un groupe et supprimer toutes ses dépendances

### `deluser`

Supprimer un utilisateur

Paramètres :

* `--remove-home` = Supprimer l'utilisateur et son répertoire `/home`
* `--force`= Supprimer l'utilisateur même s'il est connecté

### `passwd`

Changer le mot de passer d'un utilisateur

Paramètres :

* `<user_name>` = nom de l'utilisateur pour lequel modifier le mot de passe  
  * utilisateur en cours si vide
  * aucune password policy si exécuté en root
* `-e` = forcer le changement de mot de passe à la prochaine connexion (`<user_name>` et `sudo` sont obligatoires)

Exemples :

* Changer le mot de passe de l'utilisateur en cours (sans password policy)

```bash
sudo passwd
```

* Changer le mot de passe de toto (avec password policy)

```bash
passwd toto
```

* Forcer le changement de mot de passe à la prochaine connexion de toto

```bash
passwd -e toto
```

### `usermod`

Modifier un utilisateur

Paramètre :

* `-G` = supprimer tous les groupes d'un utilisateur et définir celui ou ceux passé(s) en paramètre (séparés par `,`)

Exemple :

* Définir un groupe

```bash
sudo usermod toto -G easi,house
```
