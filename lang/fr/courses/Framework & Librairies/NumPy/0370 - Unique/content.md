## Introduction

Cette fonction retourne un tableau d'éléments uniques dans le tableau d'entrée. La fonction peut être capable de retourner un tuple de tableau de valeurs uniques et un tableau d'indices associés. La nature des indices dépend du type de paramètre de retour dans l'appel de la fonction.

```python
numpy.unique(arr, return_index, return_inverse, return_counts)
```

Où,

**Paramètre et description**

**arr** - Le tableau d'entrée. Sera aplati s'il ne s'agit pas d'un tableau 1-D
**return_index** - Si Vrai, retourne les indices des éléments dans le tableau d'entrée.
**return_inverse** - Si Vrai, retourne les indices du tableau unique, qui peuvent être utilisés pour reconstruire le tableau d'entrée.
**return_counts** - Si Vrai, retourne le nombre de fois que l'élément du tableau unique apparaît dans le tableau original.

### Exemple

```python
import numpy as np 
a = np.array([5,2,6,2,7,5,6,8,2,9]) 

print 'First array:' 
print a 
print '\n'  

print 'Unique values of first array:' 
u = np.unique(a) 
print u 
print '\n'  

print 'Unique array and Indices array:' 
u,indices = np.unique(a, return_index = True) 
print indices 
print '\n'  

print 'We can see each number corresponds to index in original array:' 
print a 
print '\n'  

print 'Indices of unique array:' 
u,indices = np.unique(a,return_inverse = True) 
print u 
print '\n' 

print 'Indices are:' 
print indices 
print '\n'  

print 'Reconstruct the original array using indices:' 
print u[indices] 
print '\n'  

print 'Return the count of repetitions of unique elements:' 
u,indices = np.unique(a,return_counts = True) 
print u 
print indices
```

Sa sortie est la suivante -

```python
First array:
[5 2 6 2 7 5 6 8 2 9]

Unique values of first array:
[2 5 6 7 8 9]

Unique array and Indices array:
[1 0 2 4 7 9]

We can see each number corresponds to index in original array:
[5 2 6 2 7 5 6 8 2 9]

Indices of unique array:
[2 5 6 7 8 9]

Indices are:
[1 0 2 0 3 1 2 4 0 5]

Reconstruct the original array using indices:
[5 2 6 2 7 5 6 8 2 9]

Return the count of repetitions of unique elements:
[2 5 6 7 8 9]
[3 2 2 1 1 1]
```