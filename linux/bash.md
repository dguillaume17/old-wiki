# Linux | Bash

### Première ligne (shebang)

Définir que le script doit s'exécuter avec sh ou un shell compatible

```bash
#!/bin/sh
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