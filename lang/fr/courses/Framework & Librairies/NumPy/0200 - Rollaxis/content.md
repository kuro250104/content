## Introduction

Cette fonction fait reculer l'axe spécifié, jusqu'à ce qu'il se trouve dans une position spécifiée. La fonction prend trois paramètres.

```python
numpy.rollaxis(arr, axis, start)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée
- **axis** - Axe permettant de rouler vers l'arrière. La position des autres axes ne change pas les uns par rapport aux autres.
- **start** - Zéro par défaut conduisant au rouleau complet. Roule jusqu'à ce qu'il atteigne la position spécifiée

## Exemple

```python
# It creates 3 dimensional ndarray 
import numpy as np 
a = np.arange(8).reshape(2,2,2) 

print 'The original array:' 
print a 
print '\n'
# to roll axis-2 to axis-0 (along width to along depth) 

print 'After applying rollaxis function:' 
print np.rollaxis(a,2)  
# to roll axis 0 to 1 (along width to height) 
print '\n' 

print 'After applying rollaxis function:' 
print np.rollaxis(a,2,1)
```

Sa sortie est la suivante -

```python
The original array:
[
    [
        [0 1]
        [2 3]
    ]
    [
        [4 5]
        [6 7]
    ]
]

After applying rollaxis function:
[
    [
        [0 2]
        [4 6]
    ]
    [
        [1 3]
        [5 7]
    ]
]

After applying rollaxis function:
[
    [
        [0 2]
        [1 3]
    ]
    [
        [4 6]
        [5 7]
    ]
]
```