# Fichiers textes

## `bc`

Effectuer un calcul arithmétique et imprimer le résultat dans la sortie standard

```bash
echo "35/7" | bc
> 5

echo "(1+2)*3" | bc
> 9

echo "scale=2;4/2.7" | bc
> 1.48

echo "obase=16; 255" | bc
> FF

echo "ibase=16; FF" | bc
> 255

echo  "a=23;b=2;a+b" | bc
> 25

a=$(echo "3+4" | bc)
echo $a
> 7

echo "for (i = 1; i <= 4; ++i) { i } " | bc
> 1
> 2
> 3
> 4

calc="for (i = 1; i <= 4; ++i) { i }"
for i in $(echo ${calc} | bc)
do
echo "Ordinateur ${i}";
done
> Ordinateur 1
> Ordinateur 2
> Ordinateur 3
> Ordinateur 4

```

## `cat`

Concaténer un ou plusieurs fichiers et imprimer le résultat dans la sortie standard

```bash
cat -n fichier

cat -n fichier1 fichier2
```

Paramètres :

* `-n` | `--number` : imprimer le numéro des lignes
* `-b` | `--number-nonblank` : imprimer le numéro des lignes non vides

### `echo`

Imprimer la chaîne de caractères passée en paramètre

```bash
echo "Hello World!"
```