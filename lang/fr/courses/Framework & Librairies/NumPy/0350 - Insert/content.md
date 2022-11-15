## Introduction

Cette fonction insère des valeurs dans le tableau d'entrée le long de l'axe donné et avant l'index donné. Si le type des valeurs est converti pour être inséré, il est différent du tableau d'entrée. L'insertion n'est pas faite en place et la fonction retourne un nouveau tableau. De même, si l'axe n'est pas mentionné, le tableau d'entrée est aplati.

La fonction ```insert()``` prend les paramètres suivants -

```python
numpy.insert(arr, obj, values, axis)
```

Où,

**Paramètre et description**

- **arr** - Tableau d'entrée
- **obj** - L'index avant lequel l'insertion doit être effectuée
- **values** - Le tableau des valeurs à insérer
- **axis** - L'axe le long duquel il faut insérer. S'il n'est pas donné, le tableau d'entrée est aplati.

### Exemple

```python
import numpy as np 
a = np.array([[1,2],[3,4],[5,6]]) 

print 'First array:' 
print a 
print '\n'  

print 'Axis parameter not passed. The input array is flattened before insertion.'
print np.insert(a,3,[11,12]) 
print '\n'  
print 'Axis parameter passed. The values array is broadcast to match input array.'

print 'Broadcast along axis 0:' 
print np.insert(a,1,[11],axis = 0) 
print '\n'  

print 'Broadcast along axis 1:' 
print np.insert(a,1,11,axis = 1)
```

Sa sortie serait la suivante -

```python
First array:
[
    [1 2]
    [3 4]
    [5 6]
]

Axis parameter not passed. The input array is flattened before insertion.
[ 1 2 3 11 12 4 5 6]

Axis parameter passed. The values array is broadcast to match input array.
Broadcast along axis 0:
[
    [ 1 2]
    [11 11]
    [ 3 4]
    [ 5 6]
]

Broadcast along axis 1:
[
    [ 1 11 2]
    [ 3 11 4]
    [ 5 11 6]
]
```