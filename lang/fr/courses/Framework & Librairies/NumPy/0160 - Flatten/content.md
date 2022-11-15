## Introduction

Cette fonction renvoie une copie d'un tableau réduit à une seule dimension. La fonction prend les paramètres suivants.

```python
ndarray.flatten(order)
```

Où,

**Paramètre et description**

**order** - 'C' : ordre principal de la ligne (par défaut). A' : aplatir dans l'ordre de la colonne principale, si a est contigu dans la mémoire Fortran, dans l'ordre de la ligne principale sinon 'K' : aplatir a dans l'ordre des éléments dans la mémoire.

### Exemple

```python
import numpy as np 
a = np.arange(8).reshape(2,4) 

print 'The original array is:' 
print a 
print '\n'  
# default is column-major 

print 'The flattened array is:' 
print a.flatten() 
print '\n'  

print 'The flattened array in F-style ordering:' 
print a.flatten(order = 'F')
```

La sortie du programme ci-dessus serait la suivante -

```python
The original array is:
[
    [0 1 2 3]
    [4 5 6 7]
]

The flattened array is:
[0 1 2 3 4 5 6 7]

The flattened array in F-style ordering:
[0 4 1 5 2 6 3 7]
```