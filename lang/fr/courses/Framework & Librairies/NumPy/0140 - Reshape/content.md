## Introduction

Cette fonction donne une nouvelle forme à un tableau sans modifier les données. Elle accepte les paramètres suivants

```python
numpy.reshape(arr, newshape, order')
```

Où,

**Paramètre et description**

- **arr** - Un tableau à remodeler	
- **newshape** - int ou tuple de int. La nouvelle forme doit être compatible avec la forme original
- **order** - C" pour le style C, "F" pour le style Fortran, "A" signifie un ordre de type Fortran si un tableau est stocké dans une mémoire contiguë de type Fortran, de type C autrement.

### Exemple

```python
import numpy as np
a = np.arange(8)
print 'The original array:'
print a
print '\n'

b = a.reshape(4,2)
print 'The modified array:'
print b
```

Sa sortie serait la suivante -

```python
The original array:
[0 1 2 3 4 5 6 7]

The modified array:
[
    [0 1]
    [2 3]
    [4 5]
    [6 7]
]
```