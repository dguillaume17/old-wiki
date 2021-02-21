# Linux | Bash

## Types

Un `shell` est un interprêteur de commandes.
Il en existe plusieurs types:

* `bash` : Bourne-Again Shell (`/bin/bash`)
* `zsh` : Z Shell (`/bin/zsh`)

Bash est le shell par défaut de GNU/Linux.
Zsh est le shell par défaut de MacOS.

## Shebang

Définir que le script doit s'exécuter avec sh ou un shell compatible

```bash
#!/bin/sh
...
```

## Bonnes pratiques

Exemple :

```bash
print_start_message() {
    echo "BEGIN"
}

print_end_message() {
    echo "END"
}

backup_files() {
    cp $file_to_backup $file_destination
}

main() {
    file_to_backup="test1.txt"
    file_destination="test1.txt"
    
    print_start_message
    backup_files
    print_end_message
}

main
```

## Paramètres

Exemple

* Commande

```bash
sh ./script.sh param1 param2
```

* Fichier `script.sh`

```bash
echo $1 #print "param1"
echo $2 #print "param2"
```

## Variables

Recommandation :

* Toujours concaténer les variables de cette manière afin d'éviter des erreurs de logiques : `"${variable1} ${variable2}"`

Exemples :

* Affectation

```bash
toto="toto"
tata=1
tutu=false
```

* Tableaux

```bash
liste=(1 ok true)
echo "${liste}" #imprimer le premier indice du tableau (=1)
echo "${liste[0]}" #imprimer le premier indice du tableau (=1)
echo "${liste[1]}" #imprimer le deuxième indice du tableau (=ok)
echo "${liste[*]}" #imprimer tout le tableau (=1 ok true)
```

## Conditions

Recommandation :

* Toujours utiliser des doubles `[[ ]]` afin d'éviter des erreurs de logiques

Exemples :

* `IF...` avec `string`

```bash
nom="Toto"

if [[ $nom = "Toto" ]] ; then
    echo "Salut Toto"
fi
```

* `IF...` avec `bool`

```bash
condition=true
if [[ "$condition" = true ]] ; then
    echo "Condition vraie"
fi
```

* `IF...ELSE...`

```bash
nom="Toto"
if [[ $nom = "Toto" ]] ; then
    echo "Salut Toto"
else
    echo "Salut !"
fi
```

* `IF...ELSEIF...ELSE...`

```bash
nom="Toto"
if [[ $nom = "Toto" ]] ; then
    echo "Salut Toto"
elif [[ $nom = "Tata" ]]
    echo "Salut Tata"
else
    echo "Salut !"
fi
```

* Tester si une variable est affectée

```bash
if [[ -n $variable ]] ; then
    echo "Variable non vide"
fi
```

* Tester si fichier existe

```bash
if [[ -f config.ini ]] ; then
   echo "config.ini existe"
fi
```

* Tester si une commnde retourne une erreur

```bash
if ! grep "OUI" config.ini ; then
    echo "Le fichier n'existe pas ou ne contient pas 'OUI'"
fi
```
