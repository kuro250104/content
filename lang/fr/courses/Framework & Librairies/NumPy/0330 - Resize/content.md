## Introduction

Cette fonction renvoie un nouveau tableau avec la taille spécifiée. Si la nouvelle taille est supérieure à l'original, les copies répétées des entrées de l'original sont contenues. La fonction prend les paramètres suivants.

```python
numpy.resize(arr, shape)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée à redimensionner
- **shape** - Nouvelle forme du tableau résultant

### Exemple

```python
import numpy as np 
a = np.array([[1,2,3],[4,5,6]]) 

print 'First array:' 
print a 
print '\n'

print 'The shape of first array:' 
print a.shape 
print '\n'  
b = np.resize(a, (3,2)) 

print 'Second array:' 
print b 
print '\n'  

print 'The shape of second array:' 
print b.shape 
print '\n'  
# Observe that first row of a is repeated in b since size is bigger 

print 'Resize the second array:' 
b = np.resize(a,(3,3)) 
print b
```

Le programme ci-dessus produira la sortie suivante -

```python
First array:
[
    [1 2 3]
    [4 5 6]
]

The shape of first array:
(2, 3)

Second array:
[
    [1 2]
    [3 4]
    [5 6]
]

The shape of second array:
(3, 2)

Resize the second array:
[
    [1 2 3]
    [4 5 6]
    [1 2 3]
]
```