# Linux

## Bash

### Première ligne (shebang)

Définir que le script doit s'exécuter avec sh ou un shell compatible

```bash
#!/bin/sh
```

### Répertoire en cours

>.

Exemple

```bash
`chmod 777 .`
```

### Condition

>if

Exemple (plusieurs lignes)

```bash
nom="Bruno"

if [ $nom = "Bruno" ]
then
    echo "Salut Bruno !"
fi
```

Exemple (une ligne)

```bash
nom="Bruno"; if [ $nom = "Bruno" ]; then echo "Salut Bruno"; fi
```

### Statut de la dernière commande

>$?

Exemple

```bash
mkdir test
echo $?
```

## Commandes

### pwd
>Lister le répertoire en cours

### ls
>Lister les répertoires

`ls -l`

### chmod
>Modifier les droits d'un répertoire

Ajouter le droit "full" sur le répertoire en cours
`chmod 777 .`

### ps
Lister tous les process

`ps -ax`