## Introduction

Cette fonction renvoie le produit interne des vecteurs pour les tableaux 1-D. Pour les dimensions supérieures, elle renvoie le produit de la somme sur les derniers axes.

### Exemple

```python
import numpy as np 
print np.inner(np.array([1,2,3]),np.array([0,1,0])) 
# Equates to 1*0+2*1+3*0
```

Il produira le résultat suivant -

```python
2
```

### Exemple

```python
# Multi-dimensional array example 
import numpy as np 
a = np.array([[1,2], [3,4]]) 

print 'Array a:' 
print a 
b = np.array([[11, 12], [13, 14]]) 

print 'Array b:' 
print b 

print 'Inner product:' 
print np.inner(a,b)
```

Il produira le résultat suivant -

```python
Array a:
[
    [1 2]
    [3 4]
]

Array b:
[
    [11 12]
    [13 14]
]

Inner product:
[
    [35 41]
    [81 95]
]
```

Dans le cas ci-dessus, le produit interne est calculé comme -

```python
1*11+2*12, 1*13+2*14 
3*11+4*12, 3*13+4*14
```