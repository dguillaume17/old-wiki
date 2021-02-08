# Linux | Commandes

## Fichiers textes

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

Paramètres

* `-%count%` = nombre de lignes à afficher (10 par défaut)
* `-f` = afficher les dernières lignes en temps réel (utile pour suivre l'évolution des fichiers de log)

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
