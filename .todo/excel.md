# Excel

## Créer tableau à partir de plusieurs colonnes adjacentes

``` excel
=A1#:E1#
```

## Créer tableau à partir de plusieurs colonnes non adjacentes

``` excel
=CHOOSE(TRANSPOSE({1;2;3}); A1#; C1#; E1#)
```

## Retourner la colonne `n` d'un tableau

``` excel
=INDEX(A1#:E1#;;n)
```

## Convertir un tableau de number en un tableau de boolean

``` excel
=ISNUMBER(A1:A10)
```

## Convertir un tableau de boolean en un tableau de number

``` excel
=--A1:A10
```
