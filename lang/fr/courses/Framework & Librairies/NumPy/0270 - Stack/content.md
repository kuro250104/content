## Introduction

Cette fonction joint la séquence de tableaux le long d'un nouvel axe. Cette fonction a été ajoutée depuis la version 1.10.0 de NumPy. Les paramètres suivants doivent être fournis.

__Remarque__ - Cette fonction est disponible à partir de la version 1.10.0.

```python
numpy.stack(arrays, axis)
```

Où,

**Paramètre et description**

- **arrays** - Séquence de tableaux de même forme
- **axis** - Axe du tableau résultant le long duquel les tableaux d'entrée sont empilés.

### Exemple

```python
import numpy as np 
a = np.array([[1,2],[3,4]]) 

print 'First Array:' 
print a 
print '\n'
b = np.array([[5,6],[7,8]]) 

print 'Second Array:' 
print b 
print '\n'  

print 'Stack the two arrays along axis 0:' 
print np.stack((a,b),0) 
print '\n'  

print 'Stack the two arrays along axis 1:' 
print np.stack((a,b),1)
```

Il devrait produire le résultat suivant -

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

Stack the two arrays along axis 0:
[
    [
        [1 2]
        [3 4]
    ]
    [
        [5 6]
        [7 8]
    ]
]

Stack the two arrays along axis 1:
[
    [
        [1 2]
        [5 6]
    ]
    [
        [3 4]
        [7 8]
    ]
]
```