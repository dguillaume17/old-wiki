# Linux | Droits

Syntaxe :

```bash
[type][groupe1][groupe2][groupe3]
```

Paramètres :

>[type] = type du fichier (1 caractère)
>>"-" : fichier classique
d : répertoire
l : lien symbolique
c : périphérique de type caractère
b : périphérique de type bloc
p : pipe
s : socket
>
>[groupe1] = droits du propriétaire (3 caractères)
[groupe2] = droits du groupe (3 caractères)
[groupe3] = droits pour tout le monde (3 caractères)
>>r : lecture
w : écriture
x : exécution

Exemple :

```bash
drwxr-xr-x
```
