# Excel

## Créer tableau à partir de plusieurs colonnes adjacentes

``` excel
=A1#:E1#
```

## Créer tableau à partir de plusieurs colonnes non adjacentes

``` excel
=CHOOSE({1\2\3}; A1#; C1#; E1#)
```

## Créer un tableau constant de plusieurs lignes

``` excel
={1;2;3}
```

## Créer un tableau constant de plusieurs colonnes

``` excel
={1\2\3}
```

## Créer un tableau constant de plusieurs lignes et colonnes

``` excel
={"Colonne1.Ligne1"\"Colonne2.Ligne1";"Colonne1.Ligne2"\"Colonne2.Ligne2"}
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

## Inverser l'ordre d'un vecteur

``` excel
=LET(
vector;{10;20;30;40;50};
reverseVector;INDEX(vector;SEQUENCE(ROWS(vector);;ROWS(vector);-1));
reverseVector
)
```

## Multiplier un tableau x.y par un vecteur 1.x donne un vecteur 1.y

Exemple :
    Pour un vecteur de valeurs `values` et pour un 2 vecteurs de critères (valeurs min `minCriterias` et valeurs max `maxCriterias`), retourner respectivement le numéro du premier critère trouvé et le numéro du deuxième critère trouvé pour chaque valeur

``` excel
=LET(
values;{150;250;350;450;550;650};
minCriterias;{100;300;100;500};
maxCriterias;{200;400;600;600};

criteriasCount;ROWS(minCriterias);
reverseSequenceCriterias;SEQUENCE(criteriasCount;;criteriasCount;-1);
reverseMinCriterias;INDEX(minCriterias;reverseSequenceCriterias);
reverseMaxCriterias;INDEX(maxCriterias;reverseSequenceCriterias);
transposeReverseMinCriterias;TRANSPOSE(reverseMinCriterias);
transposeReverseMaxCriterias;TRANSPOSE(reverseMaxCriterias);
reverseCriteriasPerValue;(values>=transposeReverseMinCriterias)*(values<=transposeReverseMaxCriterias);
reverseBinaryCriteriasPerValue;MMULT(reverseCriteriasPerValue;2^(SEQUENCE(criteriasCount)-1));
reverseFirstBinaryCriteriaPerValue;reverseBinaryCriteriasPerValue;
reverseFirstCriteriaPerValue;FLOOR.MATH(LOG(reverseFirstBinaryCriteriaPerValue;2));
firstCriteriaPerValue;IFERROR(criteriasCount-reverseFirstCriteriaPerValue;0);
reverseSecondBinaryCriteriaPerValue;reverseFirstBinaryCriteriaPerValue-(2^reverseFirstCriteriaPerValue);
reverseSecondCriteriaPerValue;FLOOR.MATH(LOG(reverseSecondBinaryCriteriaPerValue;2));
secondCriteriaPerValue;IFERROR(criteriasCount-reverseSecondCriteriaPerValue;0);
CHOOSE({1\2};firstCriteriaPerValue;secondCriteriaPerValue)
)

```

``` excel
=LET(
values;{150;250;350;450;550;650};
minCriterias;{100;300;100;500};
maxCriterias;{200;400;600;600};

criteriasCount;ROWS(minCriterias);
sequenceCriterias;SEQUENCE(criteriasCount);
foundCriteriasPerValueFn;LAMBDA(foundCriteriaIndex;BYROW(values;LAMBDA(value;IFERROR(INDEX(FILTER(sequenceCriterias;(value>=minCriterias)*(value<=maxCriterias);0);foundCriteriaIndex);0))));
firstCriteriaPerValue;foundCriteriasPerValueFn(1);
secondCriteriaPerValue;foundCriteriasPerValueFn(2);
CHOOSE({1\2};firstCriteriaPerValue;secondCriteriaPerValue)
)
```

## Convertir un nombre décimal en binaire

``` excel
=BASE(nombre;2)
```

## Concaténer 1 titre avec 1 dynamic array

``` excel
=LET(
rowCount;ROWS(AM11:AM13);
sequenceTitleAndRow;SEQUENCE(rowCount+1;;0);
IF(sequenceTitleAndRow=0;"Titre";INDEX(AM11:AM13;sequenceTitleAndRow))
)
```

``` excel
=IFERROR(INDEX(AM11:AM13;SEQUENCE(ROWS(AM11:AM13)+1));"Titre")
```


## Comment exécuter une macro qui affiche le temps de calcul d'un WorkBook

Sub Performance()

    Time1 = Timer
    
    Columns("A:A").Select
    Selection.Insert Shift:=xlToRight, CopyOrigin:=xlFormatFromLeftOrAbove
    
    Columns("A:A").Select
    Selection.Delete
    
    Time2 = Timer
    CalculationTime = Time2 - Time1
    
    MsgBox "Temps d'exécution : " & (CalculationTime * 1000) & " ms."

End Sub
