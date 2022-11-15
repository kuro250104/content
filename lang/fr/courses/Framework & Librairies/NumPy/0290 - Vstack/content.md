## Introduction

Variantes de la fonction numpy.stack pour empiler de façon à faire un seul tableau verticalement.

### Exemple

```python
import numpy as np 
a = np.array([[1,2],[3,4]]) 

print 'First array:' 
print a 
print '\n'  
b = np.array([[5,6],[7,8]]) 

print 'Second array:' 
print b 
print '\n'

print 'Vertical stacking:' 
c = np.vstack((a,b)) 
print c
```

Il produirait le résultat suivant -

```python
First array:
[
    [1 2]
    [3 4]
]

Second array:
[
    [5 6]
    [7 8]
]

Vertical stacking:
[
    [1 2]
    [3 4]
    [5 6]
    [7 8]
]
```