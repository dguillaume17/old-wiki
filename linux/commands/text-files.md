# Fichiers textes

## `bc`

Effectuer un calcul arithmétique et imprimer le résultat dans la sortie standard

Exemples :

```bash
echo "35/7" | bc
> 5
```

```bash
echo "(1+2)*3" | bc
> 9
```

```bash
echo "scale=2;4/2.7" | bc
> 1.48
```

```bash
echo "obase=16; 255" | bc
> FF
```

```bash
echo "ibase=16; FF" | bc
> 255
```

```bash
echo  "a=23;b=2;a+b" | bc
> 25
```

```bash
a=$(echo "3+4" | bc)
echo $a
> 7
```

```bash
echo "for (i = 1; i <= 4; ++i) { i } " | bc
> 1
> 2
> 3
> 4
```

```bash
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
cat test1.txt
> hello
> world
```

```bash
cat test1.txt test2.txt
> hello
> world
> hello everybody
```

```bash
cat test1.txt test2.txt -n
> 1 hello
> 2 world
> 3 hello everybody
```

Paramètres :

* `-n` | `--number` : imprimer le numéro des lignes
* `-b` | `--number-nonblank` : imprimer le numéro des lignes non vides

### `echo`

Imprimer la chaîne de caractères passée en paramètre

Exemples :

```bash
echo "Hello World!"
> Hello World!
```

### `wc`

Compter le nombre de lignes, de mots et de caractères d'un fichier

Exemples :

```bash
wc test1.txt
> 74    88      364     test1.txt
```

* 74 = nombre de lignes
* 88 = nombre de mots
* 364 = nombre de caractères

```bash
wc test1.txt test2.txt
> 74    88      364     test1.txt
> 65    75      287     test2.txt
> 139   163     651     total
```

```bash
cat test1.txt | wc
> 74    88      364
```

Paramètres :

```bash
wc test1.txt test2.txt -l
> 74    test1.txt
> 65    test2.txt
> 139   total
```

```bash
cat test1.txt | wc -l
> 74
```

* `-l` | `--lines` : nombre le lignes
* `-w` | `--words` : nombre de mots
* `-c` | `--chars` : nombre de caractères
