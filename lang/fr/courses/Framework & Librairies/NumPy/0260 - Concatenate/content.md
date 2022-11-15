## Introduction

La concaténation fait référence à la jonction. Cette fonction est utilisée pour joindre deux ou plusieurs tableaux de la même forme le long d'un axe spécifié. La fonction prend les paramètres suivants.

```python
numpy.concatenate((a1, a2, ...), axis)
```

Où,

**Paramètre et description**

- **a1,a2..** - Séquence de tableaux de même type
- **axis** - Axe le long duquel les tableaux doivent être joints. La valeur par défaut est 0

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
# both the arrays are of same dimensions 

print 'Joining the two arrays along axis 0:' 
print np.concatenate((a,b)) 
print '\n'  

print 'Joining the two arrays along axis 1:' 
print np.concatenate((a,b),axis = 1)
```

Sa sortie est la suivante -

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

Joining the two arrays along axis 0:
[
    [1 2]
    [3 4]
    [5 6]
    [7 8]
]

Joining the two arrays along axis 1:
[
    [1 2 5 6]
    [3 4 7 8]
]
```