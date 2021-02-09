# Linux | Commandes

## Textes

### `less`

Visualiser le contenu d'un fichier texte

Raccourcis :

* Haut | Bas : (`up` | `down`) ou (`y` | `e`) ou (`k` | `j`)
* Début | Fin : `b` | `space`
* Quitter : `q`

Exemple :

```bash
less toto.txt
```

### `head`

Imprimer les x premières lignes d'un fichier texte

Paramètres

* `-%count%` = nombre de lignes à afficher (10 par défaut)

### `tail`

Imprimer les x dernières lignes d'un fichier texte

Paramètres :

* `-%count%` = nombre de lignes à afficher (10 par défaut)
* `-f` = afficher les dernières lignes en temps réel (utile pour suivre l'évolution des fichiers de log)

Raccourcis :

* Créer des lignes vides en mode follow (`-f`) : `enter`

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

### `ps`

Lister tous les process

Paramètres :

* `-a` = lister les process pour tous les utilisateurs
* `-u` = afficher des colonnes supplémentaires et trier par nom d'utilisateur
* `-x` = lister en plus les process liés à des services

Exemple:

```bash
ps -aux
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

### `sed`

#### Mode substitution

Remplacer une chaîne dans un fichier texte

Syntaxe :

```bash
sed -i 's/<regular_expression>/<new_text>/<regex_flag>' file.txt
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

### `ls`

Lister le contenu d'un répertoire

Paramètres :

* `-l` = mode liste
* `-a` = voir les contenus cachés
* `-F` = voir un astérix après le nom de chaque fichier exécutable

Alias :

* `l` = `ls`
* `ll` = `ls -laF`

Exemple :

```bash
ls -la
```

### `pwd`

Imprimer le chemin du répertoire en cours

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
