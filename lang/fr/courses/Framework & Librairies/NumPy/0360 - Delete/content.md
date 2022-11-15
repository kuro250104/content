## Introduction

Cette fonction renvoie un nouveau tableau avec le sous tableau spécifié supprimé du tableau d'entrée. Comme dans le cas de la fonction insert(), si le paramètre axis n'est pas utilisé, le tableau d'entrée est aplati. La fonction prend les paramètres suivants -

```python
Numpy.delete(arr, obj, axis)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée
- **obj** - Peut être une tranche, un entier ou un tableau d'entiers, indiquant le sous tableau à supprimer du tableau d'entrée.
- **axis** - L'axe le long duquel supprimer le sous tableau donné. S'il n'est pas donné, arr est aplati

### Exemple

```python
import numpy as np 
a = np.arange(12).reshape(3,4) 

print 'First array:' 
print a 
print '\n'  

print 'Array flattened before delete operation as axis not used:' 
print np.delete(a,5) 
print '\n'  

print 'Column 2 deleted:'  
print np.delete(a,1,axis = 1) 
print '\n'  

print 'A slice containing alternate values from array deleted:' 
a = np.array([1,2,3,4,5,6,7,8,9,10]) 
print np.delete(a, np.s_[::2])
```

Sa sortie serait la suivante -

```python
First array:
[
    [ 0 1 2 3]
    [ 4 5 6 7]
    [ 8 9 10 11]
]

Array flattened before delete operation as axis not used:
[ 0 1 2 3 4 6 7 8 9 10 11]

Column 2 deleted:
[
    [ 0 2 3]
    [ 4 6 7]
    [ 8 10 11]
]

A slice containing alternate values from array deleted:
[ 2 4 6 8 10]
```