## Introduction

Cette fonction permute la dimension du tableau donné. Elle retourne une vue lorsque cela est possible. La fonction prend les paramètres suivants.

```python
numpy.transpose(arr, axes)
```

Où,

**Paramètre et description**

- **arr** - Le tableau à transposer
- **axes** - Liste d'ints, correspondant aux dimensions. Par défaut, les dimensions sont inversées

### Exemple

```python
import numpy as np 
a = np.arange(12).reshape(3,4) 

print 'The original array is:' 
print a  
print '\n' 

print 'The transposed array is:' 
print np.transpose(a)
```

Sa sortie serait la suivante -

```python
The original array is:
[
    [ 0 1 2 3]
    [ 4 5 6 7]
    [ 8 9 10 11]
]

The transposed array is:
[
    [ 0 4 8]
    [ 1 5 9]
    [ 2 6 10]
    [ 3 7 11]
]
```