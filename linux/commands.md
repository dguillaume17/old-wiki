# Linux | Commandes

## Textes

### `cat`

Imprimer le fichier d'un fichier texte

Paramètres :

* `-n` | `--number` = afficher le numéro de lignes
* `-b` | `--number-nonblank` = afficher le numéro des lignes non vides

### `echo`

Imprimer le contenu passé en paramètre

### `printf`

Formatter plusieurs variables concaténée et écrire le résultat dans la sortie standard

Paramètres :

* `\n` = Retour à la ligne
* `%[<n>|-<n>]s` = Ecrire une chaîne de caractères...
  * Si `<n>` : ...sur `n` position(s) et cadrer à droite
  * Si `<-n>` : ...sur `n` position(s) et cadrer à gauche
* `%[+][<n>|-<n>]d` = Ecrire un nombre entier...
  * Si `<n>` : ...sur `n` position(s) et cadrer à droite
  * Si `<-n>` : ...sur `n` position(s) et cadrer à gauche
  * Si `<+>` : ...avec le signe
* `%[+][<n.d>|-<n.d>]f` = Ecrire un nombre flotant...
  * Si `<n.d>` : ...sur `n` position(s) au total dont `d` décimales et cadrer à droite
  * Si `<-n.d>` : ...sur `n` position(s) au total dont `d` décimales et cadrer à gauche
  * Si `<+>` : ...avec le signe

Exemples :

```bash
article="Livres"
quantite=3
prix=3.5
printf "%-20s***%03d***%+10.2f\n" $article $quantite $prix
```

```bash
liste=(livre 10 3.5 cd 5 10.65 dvd 7 19.70 bd 80 5.25)
printf "%-20s***%03d***%+10.2f\n" ${liste[*]}
```

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

### `nano`

Editeur de texte simple

Raccourcis :

* `^<t>` = `CTRL` + la touche du clavier `<t>`

### `read`

Lire dans l'entrée standard et affecter le contenu dans la variable passée en paramètre

Paramètres :

* `-p<t>` = imprimer le texte `<t>` avant de lire l'entrée standard

Exemple :

```bash
read -p"Quel est votre nom? " nom && echo $nom
```

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

### `vim`

Editeur de texte avancé

Aide :

* `vimtutor` : démarrer un tuto en anglais
* `vimtutor fr` : démarrer un tuto en français

Raccourcis :

* Mode `Normal`
  * Activer dans ce mode : `echap`
  * Action
    * `k`/ (`j` | `enter`) : Se déplacer en haut / en bas
    * `h`/ `l` : Se déplacer à gauche / à droite
    * `x` : Effacer le caractère qui se trouve sous le curseur
    * `w` / `b` (word / back) : se déplacer de mot en mot vers la droite / vers la gauche en plaçant sur curseur sur la première lettre du mot de destination
    * `e` (end) : Se déplacer de mot en mot vers la droite en plaçant sur curseur sur la dernière lettre du mot de destination
    * `$` : Sse déplacer à la fin de la ligne
    * `t<l>` / `T<l>` : Se déplacer jusqu'à la prochaine lettre `<l>` trouvée vers la droite / vers la gauche et positionner le curseur 1 caractère avant / après
    * `u` (undo) / `CTRL + R` : revenir en arrière (équivalent du CTRL Z) / revenir
     en avant (équivalent du CTRL Y)
    * `gg` / `GG` (goto) : Se déplacer au début du fichier / à la fin du fichier
    * `yy` : Copier la ligne sur laquelle se trouve le curseur
    * `dd` (duplicate) : Copier et supprimer la ligne sur laquelle se trouve le curseur
    * `p` (paste) : Coller à la ligne qui suit celle sur laquelle se trouve le curseur
  * Action en chaîne
    * `<n><a>` = répéter `n` fois l'action `<a>` (ex: `2w`)
    * `d[<n>]<a>` = supprimer le contendu à partir du curseur jusque l'endroit désigné par l'action `[<n>]<a>` (`<n> = 1` par défaut)
  * Commandes
    * `:q + enter` (quit) : quitter (ne fonctionne pas si fichier modifié)
    * `:q! + enter` (quit!) : quitter sans sauvegarder
    * `:w + enter` (write) : enregistrer
    * `:wq + enter` (write & quit) : enregistrer et quitter
    * `CTRL + G` : afficher en bas de l'écran la position du curseur dans le fichier
    * `CTRL + A` / `CTRL + X` : positionner le curseur sur le prochain nombre trouvé et l'incrémenter / le décrémenter
    * `set nu + enter` (number) : afficher le numéro des lignes
    * `:<n> + enter` : se déplacer à la ligne `<n>`
  * Recherches
    * `/<word>` = lancer la rechercher avec le mot `<word>` et se positionner sur la première occurrence trouvée
    * `n` / `N` (next) : se positionner sur l'occurrence suivante / précédente quand la recherche est lancée
  * Macros
    * `q<m>` = démarrer l'enregistrement de la macro numéro `<m>`
    * `q` = stoper l'enregistrement de la macro
    * `[<c>]@<m>` = exécuter la macro numéro `<m>` et répéter l'opération `<c>` fois (1 fois si `<c>` pas renseigné)
    * `:reg` = afficher tout ce qui se trouve dans le registre (en y incluant la liste des macros déjà enregistrées)
  * Remplacement
    * `:s/<r>/<t>/g` (substitute ) = remplacer la regex `<r>` par le texte `<t>` (pour la ligne dans laquelle se trouve le curseur)
    * `:%s/<r>/<t>/g[c]` (substitute ) = remplacer la regex `<r>` par le texte `<t>` (dans tout le fichier) et demande une confirmation pour chaque occurrence si la lettre `[c]` est spécifiée
    * `:<l1>,<l2>s/<r>/<t>/g[c]` (substitute ) = remplacer la regex `<r>` par le texte `<t>` (pour le texte situé entre les lignes `<l1>` et `<l2>`) et demande une confirmation pour chaque occurrence si la lettre `[c]` est spécifiée

* Mode `Insertion`
  * Activer dans ce mode `Insertion` : `i`
    * `CTRL + N` : ouvrir l'auto-complétion (basé) sur les mots qui existent dans le fichier)

### `wc`

Compter le nombre de lignes, de mots et de caractères d'un fichier

Paramètres :

* `-l` | `--lines` : nombre le lignes
* `-w` | `--words` : nombre de mots
* `-c` | `--chars` : nombre de caractères

## Permissions

### `chmod`

Modifier les droits d'un répertoire

Paramètres :

* Général
  * `-R` : affecte les droits de manière récursive sur le répertoire, sur ses fichiers, ses sous-répertoires, etc.)
  * `777`: activer les droits max
* Utilisateur associé
  * `u+<d>` : activer les droits `<d>` pour l'utilisateur associé
  * `u-<d>` : désactiver les droits `<d>` pour l'utilisateur associé
  * `u+<d1>-<d2>` : activer les droits `<d1>` et désactiver les droits `<d2>` pour l'utilisateur associé
* Group associé
  * `g+<d>` : activer les droits `<d>` pour le groupe associé
  * `g-<d>` : désactiver les droits `<d>` pour le groupe associé
  * `g+<d1>-<d2>` : activer les droits `<d1>` et désactiver les droits `<d2>` pour le groupe associé
* Les autres
  * `o+<d>` : activer les droits `<d>` pour les autres
  * `o-<d>` : désactiver les droits `<d>` pour les autres
  * `o+<d1>-<d2>` : activer les droits `<d1>` et désactiver les droits `<d2>` pour les autres
* Tout le monde
  * `a+<d>` : activer les droits `<d>` pour tout le monde
  * `a-<d>` : désactiver les droits `<d>` pour tout le monde
  * `a+<d1>-<d2>` : activer les droits `<d1>` et désactiver les droits `<d2>` pour tout le monde

Exemples :

```bash
chmod 777 .
chmod +w test.txt 
chmod u+w test.txt
chmod u+w,g+w test.txt
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

### `alias`

TODO

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

### `ln`

Créer des raccourcis entre les fichiers et les répertoires.

#### Lien physique

Permet de créer un fichier / répertoire (=raccourci) qui pointera vers un fichier / répertoire d'origine (=source).

Le raccourci aura le même numéro d'inode que la source.

Il faut supprimer le raccourci et la source pour que le contenu soit réellement supprimé.

Si on supprime uniquement la source, le contenu existe toujours et est accessible via le raccourci.

Attention que la commande `ls` ne distingue pas un fichier / répertoire classique d'un lien physique. Pour voir le lien physique, il faut se référer au numéro d'inode.

Syntaxe :

* `ln <src> <link>` : créer le lien physique `<link>` qui pointe vers la source `<src>`

#### Lien symbolique

Permet de créer un fichier / répertoire (=raccourci) qui pointera vers un fichier / répertoire d'origine (=source).

Le raccourci aura un numéro d'inode différence de la source.

Il faut supprimer uniquement la source pour que le contenu soit réellement supprimé.

Si on supprime uniquement la source, le contenu n'existe plus et n'est donc plus accessible via le raccourci. Le raccourci est alors imprimé en rouge par la commande `ls` pour signaler qu'il est corrompu.

Syntaxe :

* `ln -s <src> <link>` : créer le lien symbolique `<link>` qui pointe vers la source `<src>`

### `ls`

Lister le contenu d'un ou plusieurs répertoires

Paramètres :

* `-l` = mode liste
* `-a` | `--all` = voir tous les fichiers
* `-A` | `--almost-all` = voir tous les fichiers (sauf `.` et `..`)
* `-F` = voir un astérix après le nom de chaque fichier exécutable
* `-h` | `--human-readable` = afficher les tailles en notation ingénieur
* `-r` | `--reverse` = inverser l'ordre d'affichage
* `-R` | `--recursive` = mode récursif dans les répertoires et sous-répertoires
(uniquement en mode liste)
* `-d` | `--directory` = imprimer les informations du répertoire passé en paramètre
* `--full-time` = afficher les dates et heures au format ISO complet
* `--time=atime` / `--time=ctime` = afficher les `atime` / `ctime` (`mtime` est affiché par défaut)
* `--sort=none` / `--sort=size` / `--sort=time` / `--sort=extension` = sans tri / avec tri par taille / avec tri par date et heure / avec tri par extension
* `-i` | `--inode` = afficher le numéro d'inode (id unique pour chaque fichier / répertoire)

Résultat :

* Mode liste
  * les droits d'accès sont affichés dans la colonne 1 en utilisant 10 symboles
    * Symbole 1
      * `-` : fichier classique
      * `d` : répertoire
      * `l` : lien symbolique
      * `c` : périphérique de type caractère
      * `b` : périphérique de type bloc
      * `p` : pipe
      * `s` : socket
    * Symboles 2 & 5 & 8 : droits de lectures respectivement pour l'utilisateur associé, pour le groupe associé et pour les autres
      * `-` : droit de lecture désactivé
      * `r` : droit de lecture activé
    * Symboles 3 & 6 & 9 : droits d'écriture respectivement pour l'utilisateur associé, pour le groupe associé et pour les autres
      * `-` : droit d'écriture désactivé
      * `w` : droit d'écriture activé
    * Symboles 4 & 7 & 10 : droits d'exécution respectivement pour l'utilisateur associé, pour le groupe associé et pour les autres
      * `-` : droit d'exécution désactivé
      * `x` : droit d'exécution activé
  * l'avant dernière colonne affiche le propriétaire et le groupe
  * le `mtime` est affiché par défaut dans les dernières colonnes

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

### `stat`

Imprimer les statistiques d'un fichier / dossier

Paaramètres :

* `-c %a` : imprimer uniquement les droits d'accès en numérique
* `-c %A` : imprimer uniquement les droits d'accès en alphanumérique
* `-c %s` : imprimer uniquement la taille en octets
* `-c %U` : imprimer le nom du propriétaire
* `-c %w` / `-c %W`  : imprimer le `btime` au format ISO / en secondes depuis l'époque Unix
* `-c %x` / `-c %X` : imprimer le `atime` au format ISO / en secondes depuis l'époque Unix
* `-c %y` / `-c %Y` : imprimer le `mtime` au format ISO / en secondes depuis l'époque Unix
* `-c %z` / `-c %Z` : imprimer le `ctime` au format ISO / en secondes depuis l'époque Unix

Résultat :

* Mode par défaut
  * Ligne 1 : nom du fichier / dossier
  * ligne 2 : Tailles dans les différents formats
  * Ligne `Access` 1 : droits d'accès
  * Ligne `Access` 2 : `atime`
  * Ligne `Modify` : `mtime`
  * Ligne `Change` : `ctime`

### `touch`

Créer un nouveau fichier texte ou mettre à jour la date et heure de modification d'un fichier texte existant

Paramètres :

* `-a` : changer la date et heure d'accès du fichier
* `-m` : changer la date et heure de modification du fichier
* `-t<dh>` : changer la date et heure de modification du fichier avec celle spécifiée `<dh>` (au format `YYYYMMDDhhmm.ss`)

Exemples :

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
