## Introduction

Cette fonction interchange les deux axes d'un tableau. Pour les versions de NumPy postérieures à 1.10, une vue du tableau échangé est retournée. La fonction prend les paramètres suivants.

```python
numpy.swapaxes(arr, axis1, axis2)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée dont les axes doivent être échangés
- **axis1** - Un int correspondant au premier axe
- **axis2** - Un int correspondant au deuxième axe

### Exemple

```python
# It creates a 3 dimensional ndarray 
import numpy as np 
a = np.arange(8).reshape(2,2,2) 

print 'The original array:' 
print a 
print '\n'  
# now swap numbers between axis 0 (along depth) and axis 2 (along width) 

print 'The array after applying the swapaxes function:' 
print np.swapaxes(a, 2, 0)
```

Sa sortie serait la suivante -

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

The array after applying the swapaxes function:
[
    [
        [0 4]
        [2 6]
    ]
    [
        [1 5]
        [3 7]
    ]
]
```