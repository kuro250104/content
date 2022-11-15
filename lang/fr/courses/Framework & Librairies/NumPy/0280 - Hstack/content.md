## Introduction

Variantes de la fonction numpy.stack pour empiler de façon à faire un seul tableau horizontalement.

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

print 'Horizontal stacking:' 
c = np.hstack((a,b)) 
print c 
print '\n'
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

Horizontal stacking:
[
    [1 2 5 6]
    [3 4 7 8]
]
```