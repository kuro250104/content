## Introduction

La fonction numpy.hsplit est un cas particulier de la fonction split() où l'axe est 1, indiquant une division horizontale quelle que soit la dimension du tableau d'entrée.

### Exemple

```python
import numpy as np 
a = np.arange(16).reshape(4,4) 

print 'First array:' 
print a 
print '\n'  

print 'Horizontal splitting:' 
b = np.hsplit(a,2) 
print b 
print '\n'
```

Sa sortie serait la suivante -

```python
First array:
[
    [ 0 1 2 3]
    [ 4 5 6 7]
    [ 8 9 10 11]
    [12 13 14 15]
]

Horizontal splitting:                                                         
[
    array(
        [
            [ 0,  1],
            [ 4,  5],
            [ 8,  9],
            [12, 13]
        ]
    ), array(
        [
            [ 2,  3],
            [ 6,  7],
            [10, 11],
            [14, 15]
        ]
    )
]
```