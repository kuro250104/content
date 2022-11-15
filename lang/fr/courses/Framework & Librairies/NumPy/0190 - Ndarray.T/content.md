## Introduction

Cette fonction appartient à la classe ndarray. Elle se comporte de manière similaire à numpy.transpose.

### Exemple

```python
import numpy as np 
a = np.arange(12).reshape(3,4) 

print 'The original array is:' 
print a 
print '\n'  

print 'Array after applying the function:' 
print a.T
```

La sortie du programme ci-dessus serait -

```python
The original array is:
[
    [ 0 1 2 3]
    [ 4 5 6 7]
    [ 8 9 10 11]
]

Array after applying the function:
[
    [ 0 4 8]
    [ 1 5 9]
    [ 2 6 10]
    [ 3 7 11]
]
```