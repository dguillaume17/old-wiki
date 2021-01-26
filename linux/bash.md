# Linux | Bash

## Première ligne (shebang)

Définir que le script doit s'exécuter avec sh ou un shell compatible

```bash
#!/bin/sh
```

### Paramètres

Syntaxe :

```bash
$[n]
```

Paramètres :
>[n] = numéro du paramètre

Exemple

```bash
echo $1
echo $2
```

### Variables

#### Affectation

Syntaxe :

```bash
[variable]=[valeur]
```

Paramètres :
>[variable] = nom de la variable
[valeur] = valeur à affecter

Exemple

```bash
toto="toto"
tata=1
tutu=false
```

#### Utilisation
### Conditions

#### IF

Syntaxe :

```bash
if [ [condition] ]
then
    [...]
fi
```

Exemple

```bash
nom="Bruno"
if [ $nom = "Bruno" ]
then
    echo "Salut Bruno"
fi

condition=true
if [ "$condition" = true ]
then
    echo "Condition vraie"
fi
```

#### ELSE

Syntaxe :

```bash
if [ [condition] ]
then
    [...]
else
    [...]
fi
```

#### ELSE IF

Syntaxe :

```bash
if [ [condition1] ]
then
    [...]
elif [ [condition2] ]
    [...]
else
    [...]
fi
```

