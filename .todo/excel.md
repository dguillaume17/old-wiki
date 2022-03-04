# Excel

## Créer tableau à partir de plusieurs colonnes adjacentes

``` excel
=A1#:E1#
```

## Créer tableau à partir de plusieurs colonnes non adjacentes

``` excel
=CHOOSE({1\2\3}; A1#; C1#; E1#)
```

## Créer un tableau constant de plusieurs colonnes

``` excel
={1\2\3}
```

## Créer un tableau constant de plusieurs lignes

``` excel
={1;2;3}
```

## Retourner la colonne `n` d'un tableau

``` excel
=INDEX(A1#:E1#;;n)
```

## Convertir un tableau de number en un tableau de boolean

``` excel
=A1:A10>0
```

## Convertir un tableau de boolean en un tableau de number

``` excel
=--A1:A10
```

## Convertir un tableau en séquence

``` excel
SEQUENCE(ROWS(array))
```

## Créer un tableau de x.y rempli avec la valeur 1

``` excel
=RANDARRAY(x;y;1;1)
```

## Multiplier un tableau x.y par un vecteur 1.x donne un vecteur 1.y

Exemple :

- convertir chaque valeur d'un vecteur (données) en TRUE si celle-ci est contenue au moins une fois dans les valeurs d'un autre vecteur (critères)
- convertir en FALSE dans le cas contraire

``` excel
=LET(
données;{50;100;150;200;200;300};
criteres;{100;200;250};
matrice;données=TRANSPOSE(criteres);
vecteur;criteres/criteres;
MMULT(--matrice;--vecteur)>0
)
```
