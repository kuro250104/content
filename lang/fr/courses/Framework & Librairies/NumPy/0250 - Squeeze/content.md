## Introduction

Cette fonction supprime une entrée unidimensionnelle de la forme du tableau donné. Deux paramètres sont nécessaires pour cette fonction.

```python
numpy.squeeze(arr, axis)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée
- **axis** - int ou tuple of int. sélectionne un sous-ensemble d'entrées unidimensionnelles dans la forme

### Exemple

```python
import numpy as np  
x = np.arange(9).reshape(1,3,3) 

print 'Array X:' 
print x 
print '\n'  
y = np.squeeze(x) 

print 'Array Y:' 
print y 
print '\n'  

print 'The shapes of X and Y array:' 
print x.shape, y.shape
```

Sa sortie est la suivante -

```python
Array X:
[
    [
        [0 1 2]
        [3 4 5]
        [6 7 8]
    ]
]

Array Y:
[
    [0 1 2]
    [3 4 5]
    [6 7 8]
]

The shapes of X and Y array:
(1, 3, 3) (3, 3)
```