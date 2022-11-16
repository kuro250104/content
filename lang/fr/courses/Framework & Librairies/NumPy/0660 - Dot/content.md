## Introduction

Cette fonction renvoie le produit scalaire de deux tableaux. Pour les vecteurs 2-D, c'est l'équivalent d'une multiplication de matrice. Pour les tableaux 1-D, c'est le produit interne des vecteurs. Pour les tableaux à N dimensions, il s'agit du produit de la somme du dernier axe de a et de l'avant-dernier axe de b.

```python
import numpy.matlib 
import numpy as np 

a = np.array([[1,2],[3,4]]) 
b = np.array([[11,12],[13,14]]) 
np.dot(a,b)
```

Il produira le résultat suivant -

```python
[
    [37  40] 
    [85  92]
]
```

Notez que le produit scalaire est calculé comme -

```python
[[1*11+2*13, 1*12+2*14],[3*11+4*13, 3*12+4*14]]
```