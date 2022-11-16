## Introduction

Nous avons vu que les données stockées dans la mémoire d'un ordinateur dépendent de l'architecture utilisée par l'unité centrale. Elles peuvent être little-endian (l'octet le moins significatif est stocké à la plus petite adresse) ou big-endian (l'octet le plus significatif est stocké à la plus petite adresse).

## numpy.ndarray.byteswap()

La fonction ```numpy.ndarray.byteswap()``` permet de basculer entre les deux représentations : bigendian et little-endian.

### Exemple

```python
import numpy as np 
a = np.array([1, 256, 8755], dtype = np.int16) 

print 'Our array is:' 
print a  

print 'Representation of data in memory in hexadecimal form:'  
print map(hex,a)  
# byteswap() function swaps in place by passing True parameter 

print 'Applying byteswap() function:' 
print a.byteswap(True) 

print 'In hexadecimal form:' 
print map(hex,a) 
# We can see the bytes being swapped
```

Il produira le résultat suivant -

```python
Our array is:
[1 256 8755]

Representation of data in memory in hexadecimal form:
['0x1', '0x100', '0x2233']

Applying byteswap() function:
[256 1 13090]

In hexadecimal form:
['0x100', '0x1', '0x3322']
```