## Introduction

Cette fonction étend le tableau en insérant un nouvel axe à la position spécifiée. Deux paramètres sont requis par cette fonction.

```python
numpy.expand_dims(arr, axis)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée
- **axis** - Position où le nouvel axe doit être inséré

### Exemple

```python
import numpy as np 
x = np.array(([1,2],[3,4])) 

print 'Array x:' 
print x 
print '\n'  
y = np.expand_dims(x, axis = 0) 

print 'Array y:' 
print y 
print '\n'

print 'The shape of X and Y array:' 
print x.shape, y.shape 
print '\n'  
# insert axis at position 1 
y = np.expand_dims(x, axis = 1) 

print 'Array Y after inserting axis at position 1:' 
print y 
print '\n'  

print 'x.ndim and y.ndim:' 
print x.ndim,y.ndim 
print '\n'  

print 'x.shape and y.shape:' 
print x.shape, y.shape
```

La sortie du programme ci-dessus serait la suivante -

```python
Array x:
[
    [1 2]
    [3 4]
]

Array y:
[
    [
        [1 2]
        [3 4]
    ]
]

The shape of X and Y array:
(2, 2) (1, 2, 2)

Array Y after inserting axis at position 1:
[
    [
        [1 2]
    ]
    [
        [3 4]
    ]
]

x.ndim and y.ndim:
2 3

x.shape and y.shape:
(2, 2) (2, 1, 2)
```