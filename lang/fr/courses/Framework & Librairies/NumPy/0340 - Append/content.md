## Introduction

Cette fonction ajoute des valeurs à la fin d'un tableau d'entrée. L'opération d'ajout n'est pas in situ, un nouveau tableau est alloué. De plus, les dimensions des tableaux d'entrée doivent correspondre, sinon ValueError sera généré.

La fonction prend les paramètres suivants.

```python
numpy.append(arr, values, axis)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée
- **values** - Pour être ajouté à arr. Il doit avoir la même forme que arr (à l'exception de l'axe d'ajout).
- **axis** - L'axe le long duquel l'opération d'ajout doit être effectuée. S'il n'est pas donné, les deux paramètres sont aplatis

### Exemple

```python
import numpy as np 
a = np.array([[1,2,3],[4,5,6]]) 

print 'First array:' 
print a 
print '\n'  

print 'Append elements to array:' 
print np.append(a, [7,8,9]) 
print '\n'  

print 'Append elements along axis 0:' 
print np.append(a, [[7,8,9]],axis = 0) 
print '\n'  

print 'Append elements along axis 1:' 
print np.append(a, [[5,5,5],[7,8,9]],axis = 1)
```

Sa sortie serait la suivante -

```python
First array:
[
    [1 2 3]
    [4 5 6]
]

Append elements to array:
[1 2 3 4 5 6 7 8 9]

Append elements along axis 0:
[
    [1 2 3]
    [4 5 6]
    [7 8 9]
]

Append elements along axis 1:
[
    [1 2 3 5 5 5]
    [4 5 6 7 8 9]
]
```