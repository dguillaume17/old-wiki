# Linux | Commandes

## Tips

### Répertoire en cours

```bash
.
```

Exemple:

```bash
chmod 777 .
```

### Statut de la dernière commande

```bash
$?
```

Exemple:

```bash
mkdir test
echo $?
```

### Programmes

### pwd

Imprimer le chemin du répertoire en cours

### ls

Lister le contenu d'un répertoire

Paramètres :
>-l = mode liste
>-a = voir les contenus cachés
>-F = voir un astérix après le nom de chaque fichier exécutable

Exemple :

```bash
ls -la
```

Alias :
>l = ls
>ll = ls -laF

### less

Visualiser le contenu d'un fichier texte

Exemple :

```bash
less toto.txt
```

Raccourcis :
>Flèches du haut = Enter = e = j bouger d'une ligne vers le haut
>Flèches du bas = y = k = bouger d'une ligne vers le bas
>b = bouger d'une page vers le haut
>Espace = bouger d'une page vers le bas
>q = quitter

### chmod

Modifier les droits d'un répertoire

Ajouter le droit "full" sur le répertoire en cours

```bash
chmod 777 .
```

### chown

### ps

Lister tous les process

```bash
ps -ax
```

### awk

Imprimer une colonne d'un fichier à séparateurs

```bash
awk -F[séparateur]: '{print $[colonne]}' [fichier]
```

Avec:
>[séparateur] = Séparateur
>[colonne] = Numéro de la colonne
>[fichier] = Nom du fichier

Exemple:

```bash
less /etc/passwd | awk -F: '{print $1}'
```
