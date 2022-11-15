## Introduction

Cette fonction divise le tableau en sous-réseaux le long d'un axe spécifié. La fonction prend trois paramètres.

```python
numpy.split(ary, indices_or_sections, axis)
```

Où,

**Paramètre et description**

- **ary** - Tableau d'entrée à diviser
- **indices_or_sections** - Peut être un nombre entier, indiquant le nombre de sous-groupes de taille égale à créer à partir du tableau d'entrée. Si ce paramètre est un tableau 1-D, les entrées indiquent les points auxquels un nouveau sous-groupe doit être créé.
- **axis** - La valeur par défaut est 0

### Exemple

```python
import numpy as np 
a = np.arange(9) 

print 'First array:' 
print a 
print '\n'  

print 'Split the array in 3 equal-sized subarrays:' 
b = np.split(a,3) 
print b 
print '\n'  

print 'Split the array at positions indicated in 1-D array:' 
b = np.split(a,[4,7])
print b
```

Sa sortie est la suivante -

```python
First array:
[0 1 2 3 4 5 6 7 8]

Split the array in 3 equal-sized subarrays:
[array([0, 1, 2]), array([3, 4, 5]), array([6, 7, 8])]

Split the array at positions indicated in 1-D array:
[array([0, 1, 2, 3]), array([4, 5, 6]), array([7, 8])]
```