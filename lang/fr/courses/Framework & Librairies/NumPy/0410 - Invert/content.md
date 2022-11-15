## Introduction

Cette fonction calcule le résultat du bitwise NOT sur les entiers du tableau d'entrée. Pour les entiers signés, le complément à deux est retourné.

### Exemple

```python
import numpy as np 

print 'Invert of 13 where dtype of ndarray is uint8:' 
print np.invert(np.array([13], dtype = np.uint8)) 
print '\n'  
# Comparing binary representation of 13 and 242, we find the inversion of bits 

print 'Binary representation of 13:' 
print np.binary_repr(13, width = 8) 
print '\n'  

print 'Binary representation of 242:' 
print np.binary_repr(242, width = 8)
```

Sa sortie est la suivante -

```python
Invert of 13 where dtype of ndarray is uint8:
[242]

Binary representation of 13:
00001101

Binary representation of 242:
11110010
```

Notez que la fonction ```np.binary_repr()``` renvoie la représentation binaire du nombre décimal dans la largeur donnée.