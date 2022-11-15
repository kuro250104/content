## Introduction

La fonction ```numpy.right_shift()``` décale les bits dans la représentation binaire d'un élément de tableau vers la droite par des positions spécifiées, et un nombre égal de 0 est ajouté à partir de la gauche.

```python
import numpy as np 

print 'Right shift 40 by two positions:' 
print np.right_shift(40,2) 
print '\n'  

print 'Binary representation of 40:' 
print np.binary_repr(40, width = 8) 
print '\n'  

print 'Binary representation of 10' 
print np.binary_repr(10, width = 8)  
# Two bits in '00001010' are shifted to right and two 0s appended from left.
```

Sa sortie serait la suivante -

```python
Right shift 40 by two positions:
10

Binary representation of 40:
00101000

Binary representation of 10
00001010
```