## Introduction

Le déterminant est une valeur très utile en algèbre linéaire. Il est calculé à partir des éléments diagonaux d'une matrice carrée. Pour une matrice 2x2, il s'agit simplement de la soustraction du produit de l'élément supérieur gauche et inférieur droit du produit des deux autres.

En d'autres termes, pour une matrice ```[[a,b], [c,d]]```, le déterminant est calculé comme "ad-bc". Les matrices carrées plus grandes sont considérées comme une combinaison de matrices 2x2.

La fonction ```numpy.linalg.det()``` calcule le déterminant de la matrice d'entrée.

```python
import numpy as np
a = np.array([[1,2], [3,4]]) 
print np.linalg.det(a)
```

Il produira le résultat suivant -

```python
-2.0
```

### Exemple

```python
import numpy as np 

b = np.array([[6,1,1], [4, -2, 5], [2,8,7]]) 
print b 
print np.linalg.det(b) 
print 6*(-2*7 - 5*8) - 1*(4*7 - 5*2) + 1*(4*8 - -2*2)
```

Il produira le résultat suivant -

```python
[
    [ 6 1 1]
    [ 4 -2 5]
    [ 2 8 7]
]

-306.0

-306
```