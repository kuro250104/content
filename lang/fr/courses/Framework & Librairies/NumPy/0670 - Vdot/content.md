## Introduction

Cette fonction renvoie le produit scalaire de deux vecteurs. Si le premier argument est complexe, alors son conjugué est utilisé pour le calcul. Si l'argument id est un tableau multidimensionnel, il est aplati.

### Exemple

```python
import numpy as np 
a = np.array([[1,2],[3,4]]) 
b = np.array([[11,12],[13,14]]) 
print np.vdot(a,b)
```

Il produira le résultat suivant -

```python
130
```

__Remarque__ − 1*11 + 2*12 + 3*13 + 4*14 = 130