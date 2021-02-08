# Linux | Bash

## Shebang

Définir que le script doit s'exécuter avec sh ou un shell compatible

```bash
#!/bin/sh
...
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

Exemples :

* Affectation

```bash
toto="toto"
tata=1
tutu=false
```

## Conditions

Exemples :

* `IF...` avec `string`

```bash
nom="Toto"

if [ $nom = "Toto" ]
then
    echo "Salut Toto"
fi
```

* `IF...` avec `bool`

```bash
condition=true
if [ "$condition" = true ]
then
    echo "Condition vraie"
fi
```

* `IF...ELSE...`

```bash
nom="Toto"
if [ $nom = "Toto" ]
then
    echo "Salut Toto"
else
    echo "Salut !"
fi
```

* `IF...ELSEIF...ELSE...`

```bash
nom="Toto"
if [ $nom = "Toto" ]
then
    echo "Salut Toto"
elif [ $nom = "Tata" ]
    echo "Salut Tata"
else
    echo "Salut !"
fi
```
