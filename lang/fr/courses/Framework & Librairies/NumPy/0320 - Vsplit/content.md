## Introduction

numpy.vsplit est un cas particulier de la fonction split() où l'axe est 1, ce qui indique une division verticale quelle que soit la dimension du tableau d'entrée. L'exemple suivant le montre clairement.

### Exemple

```python
import numpy as np 
a = np.arange(16).reshape(4,4) 

print 'First array:' 
print a 
print '\n'

print 'Vertical splitting:' 
b = np.vsplit(a,2) 
print b
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

Vertical splitting:                                                           
[
    array(
        [
            [0, 1, 2, 3],                                                         
            [4, 5, 6, 7]
        ]
    ), array(
        [
            [ 8,  9, 10, 11],                               
            [12, 13, 14, 15]
        ]
    )
]
```