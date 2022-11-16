## Introduction

La fonction ```numpy.matmul()``` retourne le produit matriciel de deux tableaux. Bien qu'elle retourne un produit normal pour les tableaux 2-D, si les dimensions de l'un des arguments sont >2, il est traité comme une pile de matrices résidant dans les deux derniers index et est diffusé en conséquence.

D'autre part, si l'un des arguments est un tableau 1-D, il est promu en matrice en ajoutant un 1 à sa dimension, qui est supprimé après la multiplication.

### Exemple

```python
# For 2-D array, it is matrix multiplication 
import numpy.matlib 
import numpy as np 

a = [[1,0],[0,1]] 
b = [[4,1],[2,2]] 
print np.matmul(a,b)
```

Il produira le résultat suivant -

```python
[
    [4  1] 
    [2  2]
]
```

### Example

```python
# 2-D mixed with 1-D 
import numpy.matlib 
import numpy as np 

a = [[1,0],[0,1]] 
b = [1,2] 
print np.matmul(a,b) 
print np.matmul(b,a)
```

Il produira le résultat suivant -

```python
[1  2] 
[1  2]
```

### Example

```python
# one array having dimensions > 2 
import numpy.matlib 
import numpy as np 

a = np.arange(8).reshape(2,2,2) 
b = np.arange(4).reshape(2,2) 
print np.matmul(a,b)
```

Il produira le résultat suivant -

```python
[
    [
        [2   3] 
        [6   11]
    ]
    [
        [10  19] 
        [14  27]
    ]
]
```