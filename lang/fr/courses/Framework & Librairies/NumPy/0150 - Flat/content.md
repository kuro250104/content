## Introduction

Cette fonction renvoie un itérateur 1-D sur le tableau. Son comportement est similaire à celui de l'itérateur intégré de Python.

### Exemple

```python
import numpy as np 
a = np.arange(8).reshape(2,4) 
print 'The original array:' 
print a 
print '\n' 

print 'After applying the flat function:' 
# returns element corresponding to index in flattened array 
print a.flat[5]
```

Sa sortie est la suivante -

```python
The original array:
[
    [0 1 2 3]
    [4 5 6 7]
]

After applying the flat function:
5
```