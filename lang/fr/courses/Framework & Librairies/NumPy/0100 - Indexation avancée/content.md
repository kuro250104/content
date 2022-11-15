## Introduction

Il est possible d'effectuer une sélection dans ndarray qui est une séquence non-tuple, un objet ndarray de type entier ou booléen, ou un tuple dont au moins un élément est un objet séquence. L'indexation avancée renvoie toujours une copie des données. En revanche, le découpage en tranches ne présente qu'une vue.

Il existe deux types d'indexation avancée - Entier et Booléen.

## Indexation des nombres entiers

Ce mécanisme permet de sélectionner n'importe quel élément arbitraire d'un tableau en fonction de son index à N dimensions. Chaque tableau d'entiers représente le nombre d'index dans cette dimension. Lorsque l'index est constitué d'autant de tableaux d'entiers que de dimensions du tableau cible, cela devient simple.

Dans l'exemple suivant, un élément de la colonne spécifiée de chaque ligne de l'objet ndarray est sélectionné. Par conséquent, l'indice de ligne contient tous les numéros de ligne, et l'indice de colonne spécifie l'élément à sélectionner.

### Exemple 1

```python
import numpy as np 

x = np.array([[1, 2], [3, 4], [5, 6]]) 
y = x[[0,1,2], [0,1,0]] 
print y
```

Sa sortie serait la suivante -

```python
[1  4  5]
```

La sélection comprend des éléments à (0,0), (1,1) et (2,0) du premier tableau.

Dans l'exemple suivant, les éléments placés aux coins d'un tableau 4X3 sont sélectionnés. Les indices de ligne de la sélection sont ```[0, 0]``` et ```[3,3]``` tandis que les indices de colonne sont ```[0,2]``` et ```[0,2]```.

### Exemple 2

```python
import numpy as np 
x = np.array([[ 0,  1,  2],[ 3,  4,  5],[ 6,  7,  8],[ 9, 10, 11]]) 

print 'Our array is:' 
print x 
print '\n' 

rows = np.array([[0,0],[3,3]])
cols = np.array([[0,2],[0,2]]) 
y = x[rows,cols] 

print 'The corner elements of this array are:' 
print y
```

La sortie de ce programme est la suivante -

```python
Our array is:                                                                 
[
    [ 0  1  2]                                                                   
    [ 3  4  5]                                                                   
    [ 6  7  8]                                                                   
    [ 9 10 11]
]

The corner elements of this array are:                                        
[
    [ 0  2]
    [ 9 11]
] 
```

La sélection résultante est un objet ndarray contenant des éléments de coin.

L'indexation avancée et de base peut être combinée en utilisant une tranche ( :) ou une ellipse (...) avec un tableau d'index. L'exemple suivant utilise la tranche pour la ligne et l'index avancé pour la colonne. Le résultat est le même lorsque la tranche est utilisée pour les deux. Mais l'index avancé résulte en une copie et peut avoir une disposition de mémoire différente.

### Exemple 3

```python
import numpy as np 
x = np.array([[ 0,  1,  2],[ 3,  4,  5],[ 6,  7,  8],[ 9, 10, 11]]) 

print 'Our array is:' 
print x 
print '\n'  

# slicing 
z = x[1:4,1:3] 

print 'After slicing, our array becomes:' 
print z 
print '\n'  

# using advanced index for column 
y = x[1:4,[1,2]] 

print 'Slicing using advanced index for column:' 
print y
```

La sortie de ce programme serait la suivante -

```python
Our array is:
[
    [ 0  1  2] 
    [ 3  4  5] 
    [ 6  7  8]
    [ 9 10 11]
]

After slicing, our array becomes:
[
    [ 4  5]
    [ 7  8]
    [10 11]
]

Slicing using advanced index for column:
[
    [ 4  5]
    [ 7  8]
    [10 11]
] 
```

## Indexation des tableaux booléens

Ce type d'indexation avancée est utilisé lorsque l'objet résultant est censé être le résultat d'opérations booléennes, telles que des opérateurs de comparaison.

### Exemple 1

Dans cet exemple, les éléments supérieurs à 5 sont renvoyés à la suite de l'indexation booléenne.

```python
import numpy as np 
x = np.array([[ 0,  1,  2],[ 3,  4,  5],[ 6,  7,  8],[ 9, 10, 11]]) 

print 'Our array is:' 
print x 
print '\n'  

# Now we will print the items greater than 5 
print 'The items greater than 5 are:' 
print x[x > 5]
```

La sortie de ce programme serait -

```python
Our array is: 
[
    [ 0  1  2] 
    [ 3  4  5] 
    [ 6  7  8] 
    [ 9 10 11]
] 

The items greater than 5 are:
[ 6  7  8  9 10 11] 
```

### Exemple 2

Dans cet exemple, les éléments NaN (Not a Number) sont omis en utilisant ~ (opérateur de complément).

```python
import numpy as np 
a = np.array([np.nan, 1,2,np.nan,3,4,5]) 
print a[~np.isnan(a)]
```

Sa sortie serait -

```python
[ 1.   2.   3.   4.   5.] 
```

### Exemple 3

L'exemple suivant montre comment filtrer les éléments non complexes d'un tableau.

```python
import numpy as np 
a = np.array([1, 2+6j, 5, 3.5+5j]) 
print a[np.iscomplex(a)]
```

Ici, la sortie est la suivante -

```python
[2.0+6.j  3.5+5.j]
```